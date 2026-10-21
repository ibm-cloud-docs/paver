---

copyright:
  years: 2026
lastupdated: "2026-10-21"

keywords: paver security, paver security guide, paverguard, safety mode, safe mode, edit mode, {{site.data.keyword.at_short}}, secrets management, data retention

subcollection: paver

---

{{site.data.keyword.attribute-definition-list}}

# {{site.data.keyword.paver_full_notm}} security guide for {{site.data.keyword.cloud_notm}}
{: #paver-security-guide}

{{site.data.keyword.paver_full}} is a cloud-hosted AI assistant service that is delivered through the {{site.data.keyword.cloud}} catalog. Because {{site.data.keyword.paver}} is a managed service, {{site.data.keyword.IBM}} is responsible for the underlying infrastructure security, including network hardening, OS hardening, patch management, physical security, and service-level encryption.
{: shortdesc}

This document focuses on what customers need to know to configure and use {{site.data.keyword.paver}} securely within their own environments.

## Installation and secure configuration
{: #paver-security-installation-config}

Before provisioning {{site.data.keyword.paver}}, ensure that your {{site.data.keyword.cloud_notm}} account has the following:

- IBMid-based authentication is configured for all users who will use {{site.data.keyword.paver}}
- {{site.data.keyword.cloud_notm}} IAM policies reviewed and scoped to least privilege. {{site.data.keyword.paver}} acts with the permissions of the authenticated user.
- Multifactor authentication (MFA) is enforced at the {{site.data.keyword.cloud_notm}} account level. For more information, see [Authentication and Authorization](#paver-security-auth).

### Provisioning {{site.data.keyword.paver}}
{: #paver-security-provisioning}

{{site.data.keyword.paver}} is not installed software. It is provisioned as a service instance through the {{site.data.keyword.cloud_notm}} catalog, like any other {{site.data.keyword.cloud_notm}} service. There are no server packages for customers to install or patch on the service side. The following are best practices:

- Provision {{site.data.keyword.paver}} instances only in regions that satisfy your data residency requirements. {{site.data.keyword.paver}} is currently available in `us-south`, `eu-de`, and `jp-tok`. All user data is stored in the region where the instance was provisioned. 
- Apply {{site.data.keyword.cloud_notm}} IAM access controls to restrict who can provision, manage, or delete {{site.data.keyword.paver}} service instances.
- Use {{site.data.keyword.cloud_notm}} resource groups and access policies to separate resources by team or environment, for example dev versus production. Because {{site.data.keyword.paver}} operates with the permissions of the authenticated user, environment separation is achieved through standard IAM role scoping, so users who can't perform an action directly can't perform it through {{site.data.keyword.paver}} either.

### Execution sandbox
{: #paver-security-execution-sandbox}

{{site.data.keyword.paver}} runs commands and scripts in an {{site.data.keyword.cloud_notm}}-hosted sandbox on a virtual machine (VM) dedicated to you. Other users do not share this VM or its local sandbox storage. Within your VM, each conversation runs in a separate container with its own processes and temporary workspace.

The sandbox is temporary, but work saved for reuse is kept separately. After a period of inactivity, your VM is removed along with its containers and temporary workspaces, and a fresh one is created when you return. Files that are saved to the persistent files folder, conversation history, and memory remain available under the [data retention policy](#paver-security-data-retention).

Your persistent files are available across your own conversations. {{site.data.keyword.paver}} checks your identity when you access them and limits each sandbox's access to your file storage. Other users can't access these files through {{site.data.keyword.paver}}. Saved files are [encrypted at rest in {{site.data.keyword.cos_full}}](/docs/cloud-object-storage?topic=cloud-object-storage-encryption), and file transfers are encrypted using TLS.

### CLI installation
{: #paver-security-cli-installation}

The {{site.data.keyword.paver}} CLI (`paver`) is downloaded directly from your {{site.data.keyword.paver}} service instance. There is no third-party package registry involved.

- Always keep the CLI up to date. The CLI prompts you when a newer version is available. Keeping the CLI current ensures you have the latest security and feature updates.
- Download the CLI only from the URL provided by your {{site.data.keyword.paver}} service instance.
- Verify any automated installation scripts come from a trusted internal source before running them.

## Authentication and authorization
{: #paver-security-auth}

### Identity and login
{: #paver-security-identity-login}

Login to {{site.data.keyword.paver}} uses the same IBMid as {{site.data.keyword.cloud_notm}}. There is no separate {{site.data.keyword.paver}} identity or password. All {{site.data.keyword.cloud_notm}} account policies for passwords, session duration, and MFA apply automatically to {{site.data.keyword.paver}}.

- MFA is governed by your {{site.data.keyword.cloud_notm}} account policy. Enforce MFA at the {{site.data.keyword.cloud_notm}} account level to require it for {{site.data.keyword.paver}} access.
- Session expiry follows your {{site.data.keyword.cloud_notm}} IAM session policy.

### {{site.data.keyword.paver}} runs as the user
{: #paver-security-runs-as-user}

{{site.data.keyword.paver}} acts on behalf of the authenticated user using their credentials. It does not use a shared service account. Actions that are taken by {{site.data.keyword.paver}} against {{site.data.keyword.cloud_notm}} resources are logged as that user's actions in {{site.data.keyword.cloud_notm}} {{site.data.keyword.at_short}}, which is the same as if the user had performed those actions directly by using the CLI or console. This means:

- {{site.data.keyword.paver}} can't exceed the permissions of the authenticated user.
- Revoking a user's {{site.data.keyword.cloud_notm}} IAM access immediately prevents {{site.data.keyword.paver}} from acting on their behalf.
- The principle of least privilege applies. Users should be granted only the {{site.data.keyword.cloud_notm}} IAM roles they need, and {{site.data.keyword.paver}} will be bounded by those roles.

### User management
{: #paver-security-user-management}

User access to {{site.data.keyword.paver}} is managed entirely through {{site.data.keyword.cloud_notm}} IAM. There are no {{site.data.keyword.paver}}-specific user accounts or role assignments to maintain separately.

{{site.data.keyword.IBM_notm}} operators can access {{site.data.keyword.paver}} service data only under controlled operator access.

## Secure deployment
{: #paver-security-deployment}

### Encryption
{: #paver-security-encryption}

All {{site.data.keyword.paver}} service data (conversations, memories, files) is stored in {{site.data.keyword.IBM_notm}}-managed {{site.data.keyword.postgresql}} and {{site.data.keyword.cos_short}}, using {{site.data.keyword.IBM_notm}}-managed encryption at rest compliant with {{site.data.keyword.cloud_notm}} security standards. Sandbox execution environments use local block storage on the hosting VM, also managed by {{site.data.keyword.IBM_notm}}.

All data in transit between the {{site.data.keyword.paver}} client (CLI or web UI) and between all {{site.data.keyword.paver}} components is encrypted using TLS.

### Secrets management
{: #paver-security-secrets-management}

{{site.data.keyword.paver}} stores user-supplied credentials, such as bearer tokens, API keys, and SSH keys, in an encrypted keyring scoped to the authenticated user. Secrets stored in the keyring are used by {{site.data.keyword.paver}} to authenticate to target systems on the user's behalf and are not shared across users.

For {{site.data.keyword.cloud_notm}}, the only credential stored in the keyring by default is the user's bearer token, which is managed automatically by {{site.data.keyword.paver}} and does not need to be rotated manually. Additional secrets, such as API keys for other services, can be added to the keyring as needed by specific workflows.

Consider the following best practices:

- Store only the minimum set of credentials required for your workflows.
- Use {{site.data.keyword.cloud_notm}} API keys with the minimum IAM permissions required.
- Rotate credentials stored in the {{site.data.keyword.paver}} keyring on the same schedule as your other credentials.
- Remove credentials from the keyring when they are no longer needed (`paver keyring remove`).

## Safe use and risk controls
{: #paver-security-safe-use-risk-controls}

### Paver Guard — Risk Assessment
{: #paver-security-paverguard}

Every action {{site.data.keyword.paver}} proposes to take against a resource on behalf of the user is evaluated by {{site.data.keyword.paver}} Guard, a secondary AI agent that classifies the risk of the action as low, medium, or high before execution.

Risk is assessed based on both the nature of the operation and the context of the conversation:

| Risk level | Typical operations |
|---|---|
| **Low** | Read operations — listing, describing, or querying resources |
| **Medium** | Modifications — creating, updating, or reconfiguring resources |
| **High** | Operations that might cause data loss or service interruption — deleting resources, stopping services, changing access policies |
{: caption="Paver Guard risk level classifications" caption-side="bottom"}

Context matters significantly. {{site.data.keyword.paver}} Guard considers the full conversation context when assigning risk — for example, deleting a blank test VM that was just created in the same conversation might be rated medium risk, while deleting a production VM that hosts live applications would be rated high risk.

Users can configure a risk threshold policy:

Prompt on medium or high risk (default)
:   {{site.data.keyword.paver}} pauses and asks for explicit confirmation before proceeding with any medium- or high-risk action.

Auto-deny high risk
:   {{site.data.keyword.paver}} Guard automatically denies {{site.data.keyword.paver}}'s first attempt at a high-risk action and instructs {{site.data.keyword.paver}} to find another way to complete the task. If {{site.data.keyword.paver}} can't find a lower-risk approach after several attempts, it returns to the user and asks for permission to run the high-risk action.

Auto-deny medium or above
:   The same behavior as described for auto-deny high risk, applied to both medium- and high-risk actions.

Auto-deny policies are not an absolute block. They steer {{site.data.keyword.paver}} toward lower-risk approaches, but {{site.data.keyword.paver}} can still ask for your permission to run a denied action if no alternative exists. To completely block {{site.data.keyword.paver}} from modifying your resources, use Safe mode instead.

### Safety mode
{: #paver-security-safe-edit-mode}

The safety mode controls whether {{site.data.keyword.paver}} can modify your cloud resources. You switch between two modes: **Safe** and **Edit** mode.

In Safe mode, {{site.data.keyword.paver}} does not execute any action that modifies a resource. It can read, query, analyze, and report on your cloud account, but it can't create, update, or delete resources. {{site.data.keyword.paver}} can still read and write files in its sandbox, so you can explore your account safely and plan changes, including creating scripts or Terraform to implement those plans. However, {{site.data.keyword.paver}} can't run those scripts or apply those plans in Safe mode. Safe mode is the appropriate control when you want a hard guarantee that no resources will be modified.

To allow {{site.data.keyword.paver}} to modify resources, switch to **Edit mode** (`/edit`). All actions in Edit mode are still subject to {{site.data.keyword.paver}} Guard risk assessment.

#### Starting mode in {{site.data.keyword.cloud_notm}}
{: #paver-security-starting-mode}

{{site.data.keyword.paver}} does not start in Safe mode by default. In {{site.data.keyword.cloud_notm}}, {{site.data.keyword.paver}} can automatically switch between Safe mode and Edit mode based on the name of your account.

- If the account name suggests a production environment, {{site.data.keyword.paver}} starts in Safe mode.
- If the account name suggests a development or test environment, {{site.data.keyword.paver}} starts in Edit mode.
- If the account name doesn't suggest either type of environment, {{site.data.keyword.paver}} doesn't change the mode.

Because the starting mode depends on the account name, always check the current mode before you start a task, and switch modes if needed. Don't rely on automatic mode selection to protect your resources.
{: important}

For shared or sensitive environments, a recommended practice is to confirm that {{site.data.keyword.paver}} is in Safe mode and to switch to Edit mode only when changes are intended.
{: tip}

### Administrative best practices
{: #paver-security-admin-best-practices}

Review the following administrative best practices for {{site.data.keyword.paver}}:

- Train users on how to use safety mode, including the difference between Safe mode and Edit mode, when each is appropriate, and the need to check the current mode because {{site.data.keyword.paver}} can start in either mode depending on the account name.
- Use {{site.data.keyword.cloud_notm}} IAM deny policies to hard-limit what {{site.data.keyword.paver}} can do for users who should not be making infrastructure changes.
- Review conversation history periodically to audit what actions {{site.data.keyword.paver}} has taken on behalf of your users. For more information, see [Logging and Conversation History](#paver-security-logging-history).

## Logging and conversation history
{: #paver-security-logging-history}

{{site.data.keyword.paver}} integrates with {{site.data.keyword.cloudaccesstraillong}} and maintains per-user conversation history, giving you a complete audit trail of every action taken on your behalf.

### {{site.data.keyword.at_full_notm}}
{: #paver-security-activity-tracker}

Because {{site.data.keyword.paver}} acts on behalf of the authenticated user using their own credentials, all actions are recorded in {{site.data.keyword.at_short}} as events performed by that user and not by {{site.data.keyword.paver}}. There is no distinction in {{site.data.keyword.at_short}} between an action that the user took directly and an action {{site.data.keyword.paver}} took on their behalf. This means existing {{site.data.keyword.at_short}} queries, alerts, and compliance tools work without any modification.

To determine exactly what a user asked {{site.data.keyword.paver}} to do, what {{site.data.keyword.paver}} did in response, and what occurred in {{site.data.keyword.cloud_notm}} as a result, the {{site.data.keyword.at_short}} record can be correlated with the user's {{site.data.keyword.paver}} conversation history. For more information, see [Correlating Conversation History with {{site.data.keyword.at_short}}](#paver-security-correlating-history-activity-tracker).

As a best practice, provision an {{site.data.keyword.cloud_notm}} {{site.data.keyword.at_short}} instance to ensure these events are captured and retained. Without an {{site.data.keyword.at_short}} instance, events are not stored.

For event field definitions, retention, and export capabilities, refer to the [{{site.data.keyword.cloud_notm}} {{site.data.keyword.at_short}} documentation](/docs/activity-tracker).

### Security monitoring
{: #paver-security-monitoring}

Monitor for security-relevant events using {{site.data.keyword.cloud_notm}} {{site.data.keyword.at_short}}. Key events to watch for include:

- Actions that are taken outside expected hours or from unexpected locations (by IBMid)
- High volumes of resource modification events from a single user
- Failed authentication attempts

Because {{site.data.keyword.paver}} attributes all actions to the authenticated user, existing {{site.data.keyword.cloud_notm}} security monitoring practices and tooling apply without modification.

### Conversation history
{: #paver-security-conversation-history}

{{site.data.keyword.paver}} maintains a complete history of every conversation, including:
- All messages the user sent
- All actions {{site.data.keyword.paver}} proposed and took (including the exact commands or API calls issued)
- All responses {{site.data.keyword.paver}} returned
- Outcomes and errors

Conversation history is stored per user, scoped to the region of their {{site.data.keyword.paver}} instance, and is accessible only to that user. It serves as a detailed audit record of {{site.data.keyword.paver}}'s activity that complements {{site.data.keyword.cloud_notm}} {{site.data.keyword.at_short}}.

To retrieve history, run the following commands:

```sh
paver conversation list          # list all conversations
paver conversation show ID       # view a specific conversation
```
{: pre}

To export history for audit, compliance, or offload, run the following command:

```sh
paver conversation export ID   # export a single conversation as JSON
```
{: pre}

Conversation history in JSON format includes full action detail and can be retained in external systems as an audit record.

To delete history, run the following command:

```sh
paver conversation delete ID   # delete a specific conversation
```
{: pre}

Users own and control their own conversation data. They can delete individual conversations at any time. There are no administrator-level controls over another user's conversation history. This is by design so a single user can work across multiple {{site.data.keyword.cloud_notm}} accounts and administration domains within a single conversation.

Organizations with compliance requirements for conversation retention should instruct users to export conversations before deletion and store them in an external record-keeping system.

### Logging limitations
{: #paver-security-logging-limitations}

{{site.data.keyword.paver}} doesn't currently produce its own structured audit log stream. There is no {{site.data.keyword.paver}}-specific log of internal service events, such as when a conversation was created, when a sandbox was provisioned, or when {{site.data.keyword.paver}} Guard evaluated an action, available for export or integration into a SIEM.

For audit purposes, the two available sources are:
- {{site.data.keyword.cloud_notm}} {{site.data.keyword.at_short}} that records all {{site.data.keyword.cloud_notm}} API actions performed under the user's identity
- {{site.data.keyword.paver}} conversation history, which records everything the user asked, every action {{site.data.keyword.paver}} took, and all outcomes

Together these provide a complete picture of what a user did through {{site.data.keyword.paver}} and what happened in {{site.data.keyword.cloud_notm}} as a result.

### Correlating conversation history with {{site.data.keyword.at_short}}
{: #paver-security-correlating-history-activity-tracker}

Conversation history and {{site.data.keyword.at_short}} events can be correlated by IBMid (user) and timestamp. The conversation record also captures the exact action taken. For example, the {{site.data.keyword.cloud_notm}} CLI command with full parameters, which provides additional precision when tracing a specific {{site.data.keyword.at_short}} event back to the user's conversation context.

### Data retention
{: #paver-security-data-retention}

{{site.data.keyword.paver}} retains user data (conversations, memories, skills, files) for 90 days from the date of last access. Data that has not been accessed within 90 days is automatically deleted. A user who has not used {{site.data.keyword.paver}} for 90 days will have all their stored data deleted.

For compliance use cases requiring longer retention, export conversations using the CLI and store them in your own record-keeping system before the 90-day window elapses.
{: tip}

## Web UI
{: #paver-security-web-ui}

The {{site.data.keyword.paver}} web UI is delivered as a cloud-hosted application and is updated automatically by {{site.data.keyword.IBM_notm}}. There is nothing for customers to install or maintain. Browser access follows the same IBMid authentication as the CLI.
