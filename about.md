---

copyright:
  years: 2026
lastupdated: "2026-10-08"

keywords: paver overview, what is paver, agentic ai, infrastructure operations, paver capabilities, paver security

subcollection: paver

---

{{site.data.keyword.attribute-definition-list}}

# About IBM Paver
{: #paver-about}

Learn about Paver, {{site.data.keyword.IBM_notm}}'s embedded agentic AI operator for {{site.data.keyword.cloud_notm}} infrastructure operations, its capabilities, and how it works with your account.
{: shortdesc}

Paver is an agentic AI built into {{site.data.keyword.cloud_notm}} that helps you deploy, operate, and troubleshoot your cloud resources through natural language. It is available directly in the {{site.data.keyword.cloud_notm}} console and through the Paver CLI, so you can work with your accounts, services, and infrastructure without switching between tools.

Rather than generating code for you to run elsewhere, Paver acts on your behalf within {{site.data.keyword.cloud_notm}}. It runs commands and scripts in a secure sandbox, reads your account context, reasons about what needs to happen, explains its plan, and executes approved changes against your live environment.

Paver is built for environments where reliability, governance, and accountability matter. Every action is recorded through a complete audit trail. Paver operates within your existing permissions and security policies and can't exceed your authorized access. Your prompts, context, and operational data are never used to train foundation models.

## What you can do with Paver
{: #paver-capabilities}

Paver can help you accomplish the following operational goals in your {{site.data.keyword.cloud_notm}} account:

- Deploy applications across {{site.data.keyword.cloud_notm}} infrastructure
- Resolve incidents by correlating logs, metrics, and recent changes
- Optimize infrastructure utilization and reduce operational overhead
- Identify security exposures, policy gaps, and compliance risks
- Surface cost optimization opportunities and unused resources
- Understand infrastructure resources, configurations, and dependencies

## How Paver works with your account
{: #paver-how-it-works}

When you work with IBM Paver, several capabilities work together to make it effective across sessions, tasks, and your team's way of working.

### Your account context, always ready
{: #paver-memory}

When you work across multiple {{site.data.keyword.cloud_notm}} accounts, regions, and resource groups, repeating that context in every session adds friction. Paver builds a persistent picture of how you work, such as your preferred regions, the projects you return to, and the resources you manage most, and carries that context forward automatically. If your setup changes or Paver has something wrong, correct it by telling Paver in chat and it updates immediately.

### Bring your configs and artifacts into the conversation
{: #paver-files}

Managing cloud infrastructure means working with a lot of files, whether it's Terraform plans, Kubernetes manifests, deployment configs, or logs. Paver has a persistent file workspace so you can upload the files that matter to a task, ask Paver to review or act on them, and download anything Paver generates. Your workspace persists across sessions, so files are there when you return.

### Keep your credentials out of the chat
{: #paver-keyring}

Connecting Paver to your {{site.data.keyword.cloud_notm}} services often means working with API keys and service credentials. The keyring lets you store those secrets once, and then Paver injects them as environment variables at the start of each session so they're available when needed, without you ever pasting them into the chat. Secret values are never displayed after storage and are automatically redacted from Paver's output. Entries expire on a schedule you control, so credentials don't persist beyond their useful life.

### Run {{site.data.keyword.cloud_notm}} commands in the same environment Paver uses
{: #paver-shell}

When you need to go beyond chat to run a quick `ibmcloud` command, inspect a Kubernetes cluster, or verify a Terraform plan before applying it, Paver's shell puts you directly inside the environment Paver uses to act on your behalf. It comes preloaded with the {{site.data.keyword.cloud_notm}} CLI, `kubectl`, `helm`, `terraform`, and standard scripting tools, all connected to your account. Open it with `paver shell` from your terminal or `/shell` from a chat session without losing your conversation context.

### Skills that know your services
{: #paver-skills}

IBM maintains a set of built-in skills for {{site.data.keyword.cloud_notm}} services, which works as domain-specific knowledge that Paver loads automatically based on what you ask, covering the right commands, correct sequences, and service-specific considerations for the task at hand. You can also upload your own user skills to encode team-specific workflows, naming conventions, or runbooks.

### Operating with safeguards
{: #paver-safety}

When you're managing enterprise workloads on {{site.data.keyword.cloud_notm}}, staying in control of what Paver does and when is essential. By default, Paver operates in Safe mode where it can read your resources, diagnose problems, and explain what it would do, but it won't make changes. When you're ready to take action, switching to Edit mode means Paver asks for your explicit approval before each operation runs, and you can modify the exact command before it executes. Paver Guard adds a risk policy on top of this so you can set thresholds that auto-approve routine operations while holding higher-risk changes for your review, giving you fine-grained control that scales with how comfortable you are with the task at hand.
