---

copyright:
  years: 2026
lastupdated: "2026-10-14"

keywords: paver security, paver security guide, paverguard, safety mode, safe mode, edit mode, {{site.data.keyword.at_short}}, secrets management, data retention

subcollection: paver

---

{{site.data.keyword.attribute-definition-list}}

# IBM Paver security guide for {{site.data.keyword.cloud_notm}}
{: #paver-security-guide}

IBM Paver is a cloud-hosted AI assistant service that is delivered through the IBM Cloud catalog. Because Paver is a managed service, IBM is responsible for the underlying infrastructure security, including network hardening, OS hardening, patch management, physical security, and service-level encryption. This document focuses on what customers need to know to configure and use Paver securely within their own environments.
{: shortdesc}

## Installation and secure configuration
{: #paver-security-installation-config}

Before provisioning Paver, ensure that your IBM Cloud account has the following:

- IBMid-based authentication is configured for all users who will use Paver
- IBM Cloud IAM policies reviewed and scoped to least privilege. Paver acts with the permissions of the authenticated user.
- Multifactor authentication (MFA) enforced at the IBM Cloud account level (see [Authentication and Authorization](#paver-security-auth))

### Provisioning Paver
{: #paver-security-provisioning}



Paver is not installed software. It is provisioned as a service instance through the IBM Cloud catalog, like any other IBM Cloud service. There are no server packages for customers to install or patch on the service side. The following are best practices:

- Provision Paver instances only in regions that satisfy your data residency requirements. Paver is currently available in `us-south`, `eu-de`, and `jp-tok`. All user data is stored in the region where the instance was provisioned. 
- Apply IBM Cloud IAM access controls to restrict who can provision, manage, or delete Paver service instances. 
- Use IBM Cloud resource groups and access policies to separate resources by team or environment, for example dev versus production. Because Paver operates with the permissions of the authenticated user, environment separation is achieved through standard IAM role scoping, so users who cannot perform an action directly cannot perform it through Paver either.

### Execution sandbox
{: #paver-security-execution-sandbox}

Paver runs commands and scripts in an IBM Cloud-hosted sandbox on a VM dedicated to you. Other users do not share this VM or its local sandbox storage. Within your VM, each conversation runs in a separate container with its own processes and temporary workspace.

The sandbox is temporary, but work saved for reuse is kept separately. After a period of inactivity, your VM is removed along with its containers and temporary workspaces, and a fresh one is created when you return. Files that are saved to the persistent files folder, conversation history, and memory remain available under the [data retention policy](#paver-security-data-retention).

Your persistent files are available across your own conversations. Paver checks your identity when you access them and limits each sandbox's access to your file storage. Other users cannot access these files through Paver. Saved files are [encrypted at rest in {{site.data.keyword.cos_full}}](/docs/cloud-object-storage?topic=cloud-object-storage-encryption), and file transfers are encrypted using TLS.

### CLI installation
{: #paver-security-cli-installation}

The Paver CLI (`paver`) is downloaded directly from your Paver service instance. There is no third-party package registry involved.

- Always keep the CLI up to date. The CLI will prompt you when a newer version is available. Keeping the CLI current ensures you have the latest security and feature updates.
- Download the CLI only from the URL provided by your Paver service instance.
- Verify any automated installation scripts come from a trusted internal source before running them.

## Authentication and authorization
{: #paver-security-auth}

### Identity and login
{: #paver-security-identity-login}

Login to Paver uses the same IBMid as IBM Cloud. There is no separate Paver identity or password. All IBM Cloud account policies for passwords, session duration, and MFA apply automatically to Paver.

- MFA is governed by your IBM Cloud account policy. Enforce MFA at the IBM Cloud account level to require it for Paver access.
- Session expiry follows your IBM Cloud IAM session policy.

### Paver runs as the user
{: #paver-security-runs-as-user}

Paver acts on behalf of the authenticated user using their credentials. It does not use a shared service account. Actions taken by Paver against IBM Cloud resources are logged as that user's actions in IBM Cloud {{site.data.keyword.at_short}}, which is the same as if the user had performed those actions directly by using the CLI or console. This means:

- Paver can't exceed the permissions of the authenticated user.
- Revoking a user's IBM Cloud IAM access immediately prevents Paver from acting on their behalf.
- The principle of least privilege applies. Users should be granted only the IBM Cloud IAM roles they need, and Paver will be bounded by those roles.

### User management
{: #paver-security-user-management}

User access to Paver is managed entirely through IBM Cloud IAM. There are no Paver-specific user accounts or role assignments to maintain separately.

IBM operators can access Paver service data only under controlled operator access.

## Secure deployment
{: #paver-security-deployment}

### Encryption
{: #paver-security-encryption}

All Paver service data (conversations, memories, files) is stored in IBM-managed {{site.data.keyword.postgresql}} and {{site.data.keyword.cos_short}}, using IBM-managed encryption at rest compliant with IBM Cloud security standards. Sandbox execution environments use local block storage on the hosting VM, also managed by IBM.

All data in transit between the Paver client (CLI or web UI) and between all Paver components is encrypted using TLS.

### Secrets management
{: #paver-security-secrets-management}

Paver stores user-supplied credentials, such as bearer tokens, API keys, and SSH keys, in an encrypted keyring scoped to the authenticated user. Secrets stored in the keyring are used by Paver to authenticate to target systems on the user's behalf and are not shared across users.

For IBM Cloud, the only credential stored in the keyring by default is the user's bearer token, which is managed automatically by Paver and does not need to be rotated manually. Additional secrets (such as API keys for other services) can be added to the keyring as needed by specific workflows.

Consider the following best practices:

- Store only the minimum set of credentials required for your workflows.
- Use IBM Cloud API keys with the minimum IAM permissions required.
- Rotate credentials stored in the Paver keyring on the same schedule as your other credentials.
- Remove credentials from the keyring when they are no longer needed (`paver keyring remove`).

## Safe use and risk controls
{: #paver-security-safe-use-risk-controls}

### Paver Guard — Risk Assessment
{: #paver-security-paverguard}

Every action Paver proposes to take against a resource on behalf of the user is evaluated by Paver Guard, a secondary AI agent that classifies the risk of the action as low, medium, or high before execution.

Risk is assessed based on both the nature of the operation and the context of the conversation:

| Risk level | Typical operations |
|---|---|
| **Low** | Read operations — listing, describing, or querying resources |
| **Medium** | Modifications — creating, updating, or reconfiguring resources |
| **High** | Operations that may cause data loss or service interruption — deleting resources, stopping services, changing access policies |
{: caption="Paver Guard risk level classifications" caption-side="bottom"}

Context matters significantly. Paver Guard considers the full conversation context when assigning risk — for example, deleting a blank test VM that was just created in the same conversation may be rated medium risk, while deleting a production VM that hosts live applications would be rated high risk.

Users can configure a risk threshold policy:
- **Prompt on medium or high risk** (default): Paver pauses and asks for explicit confirmation before proceeding with any medium- or high-risk action.
- **Auto-deny high risk**: Paver Guard automatically denies Paver's first attempt at a high-risk action and instructs Paver to find another way to complete the task. If Paver can't find a lower-risk approach after several attempts, it returns to the user and asks for permission to run the high-risk action.
- **Auto-deny medium or above**: Same behavior as described for auto-deny high risk, applied to both medium- and high-risk actions.

Auto-deny policies are not an absolute block. They steer Paver toward lower-risk approaches, but Paver can still ask for your permission to run a denied action if no alternative exists. To completely block Paver from modifying your resources, use Safe mode instead.

### Safety mode
{: #paver-security-safe-edit-mode}

Safety mode controls whether Paver can modify your cloud resources. You switch between two modes: **Safe mode** and **Edit mode**.

Paver operates in **Safe mode** by default. In Safe mode, Paver does not execute any action that modifies a resource. It can read, query, analyze, and report on your cloud account, but it cannot create, update, or delete resources. Paver can still read and write files in its sandbox, so you can explore your account safely and plan changes, including creating scripts or Terraform to implement those plans. However, Paver cannot run those scripts or apply those plans in Safe mode. Safe mode is the appropriate control when you want a hard guarantee that no resources will be modified.

To allow Paver to modify resources, the user must explicitly switch to **Edit mode** (`paver mode edit`). Edit mode remains active for the session and all actions in Edit mode are still subject to PaverGuard risk assessment.

A recommended practice for shared or sensitive environments is to keep Paver in Safe mode as the default and require users to consciously switch to Edit mode when changes are intended.
{: tip}

### Administrative best practices
{: #paver-security-admin-best-practices}

Review the following administrative best practices for Paver:

- Train users on how to use safety mode, including the difference between Safe mode and Edit mode and when each is appropriate.
- Use IBM Cloud IAM deny policies to hard-limit what Paver can do for users who should not be making infrastructure changes.
- Review conversation history periodically to audit what actions Paver has taken on behalf of your users. For more information, see [Logging and Conversation History](#paver-security-logging-history).

## Logging and conversation history
{: #paver-security-logging-history}

Paver integrates with {{site.data.keyword.cloudaccesstraillong}} and maintains per-user conversation history, giving you a complete audit trail of every action taken on your behalf.

### {{site.data.keyword.at_full_notm}}
{: #paver-security-activity-tracker}

Because Paver acts on behalf of the authenticated user using their own credentials, all actions are recorded in {{site.data.keyword.at_short}} as events performed by that user and not by Paver. There is no distinction in {{site.data.keyword.at_short}} between an action that the user took directly and an action Paver took on their behalf. This means existing {{site.data.keyword.at_short}} queries, alerts, and compliance tools work without any modification.

To determine exactly what a user asked Paver to do, what Paver did in response, and what occurred in IBM Cloud as a result, the {{site.data.keyword.at_short}} record can be correlated with the user's Paver conversation history. For more information, see [Correlating Conversation History with {{site.data.keyword.at_short}}](#paver-security-correlating-history-activity-tracker).

As a best practice, provision an IBM Cloud {{site.data.keyword.at_short}} instance to ensure these events are captured and retained. Without an {{site.data.keyword.at_short}} instance, events are not stored.

For event field definitions, retention, and export capabilities, refer to the [IBM Cloud {{site.data.keyword.at_short}} documentation](/docs/activity-tracker).

### Security monitoring
{: #paver-security-monitoring}

Monitor for security-relevant events using IBM Cloud {{site.data.keyword.at_short}}. Key events to watch for include:

- Actions taken outside expected hours or from unexpected locations (by IBMid)
- High volumes of resource modification events from a single user
- Failed authentication attempts

Because Paver attributes all actions to the authenticated user, existing IBM Cloud security monitoring practices and tooling apply without modification.

### Conversation history
{: #paver-security-conversation-history}

Paver maintains a complete history of every conversation, including:
- All messages the user sent
- All actions Paver proposed and took (including the exact commands or API calls issued)
- All responses Paver returned
- Outcomes and errors

Conversation history is stored per user, scoped to the region of their Paver instance, and is accessible only to that user. It serves as a detailed audit record of Paver's activity that complements IBM Cloud {{site.data.keyword.at_short}}.

To retrieve history, run the following commands:

```sh
paver conversation list          # list all conversations
paver conversation show <id>       # view a specific conversation
```
{: pre}

To export history for audit, compliance, or offload, run the following command:

```sh
paver conversation export <id>   # export a single conversation as JSON
```
{: pre}

Conversation history in JSON format includes full action detail and can be retained in external systems as an audit record.

To delete history, run the following command:

```sh
paver conversation delete <id>   # delete a specific conversation
```
{: pre}

Users own and control their own conversation data. They can delete individual conversations at any time. There are no administrator-level controls over another user's conversation history. This is by design so a single user can work across multiple IBM Cloud accounts and administration domains within a single conversation.

Organizations with compliance requirements for conversation retention should instruct users to export conversations before deletion and store them in an external record-keeping system.

### Logging limitations
{: #paver-security-logging-limitations}

Paver does not currently produce its own structured audit log stream. There is no Paver-specific log of internal service events, such as when a conversation was created, when a sandbox was provisioned, or when Paver Guard evaluated an action, available for export or integration into a SIEM.

For audit purposes, the two available sources are:
- IBM Cloud {{site.data.keyword.at_short}} that records all IBM Cloud API actions performed under the user's identity
- Paver conversation history, which records everything the user asked, every action Paver took, and all outcomes

Together these provide a complete picture of what a user did through Paver and what happened in IBM Cloud as a result.

### Correlating conversation history with {{site.data.keyword.at_short}}
{: #paver-security-correlating-history-activity-tracker}

Conversation history and {{site.data.keyword.at_short}} events can be correlated by IBMid (user) and timestamp. The conversation record also captures the exact action taken. For example, the IBM Cloud CLI command with full parameters, which provides additional precision when tracing a specific {{site.data.keyword.at_short}} event back to the user's conversation context.

### Data retention
{: #paver-security-data-retention}

Paver retains user data (conversations, memories, files) for 90 days from the date of last access. Data that has not been accessed within 90 days is automatically deleted. A user who has not used Paver for 90 days will have all their stored data deleted.

| Data type | Retention |
|---|---|
| Conversations | 90 days from last access |
| Memories | 90 days from last access |
| Files | 90 days from last access |
{: caption="Data retention periods" caption-side="bottom"}

For compliance use cases requiring longer retention, export conversations using the CLI and store them in your own record-keeping system before the 90-day window elapses.
{: tip}

## Web UI
{: #paver-security-web-ui}

The Paver web UI is delivered as a cloud-hosted application and is updated automatically by IBM. There is nothing for customers to install or maintain. Browser access follows the same IBMid authentication as the CLI.
