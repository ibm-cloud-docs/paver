---

copyright:
  years: 2026
lastupdated: "2026-10-20"

keywords: paver overview, what is paver, agentic ai, infrastructure operations, paver capabilities

subcollection: paver

---

{{site.data.keyword.attribute-definition-list}}

# About {{site.data.keyword.paver_full_notm}} for {{site.data.keyword.cloud_notm}}
{: #paver-about}

Learn about {{site.data.keyword.paver_full}}, its capabilities, and how it works with your account. {{site.data.keyword.paver}} is a built-in agentic AI operator that helps you deploy, operate, and troubleshoot your cloud account and resources through natural language.
{: shortdesc}

{{site.data.keyword.paver}} is available directly in the {{site.data.keyword.cloud_notm}} console and through the {{site.data.keyword.paver_full_notm}} CLI, so you can work with your accounts, services, and infrastructure without switching between tools. Rather than generating code for you to run elsewhere, {{site.data.keyword.paver}} acts on your behalf within {{site.data.keyword.cloud_notm}}. It runs commands and scripts in a secure sandbox, reads your account context, reasons about what needs to happen, explains its plan, and actions approved changes against your live environment.

{{site.data.keyword.paver}} is built for environments where reliability, governance, and accountability matter. It operates within your existing permissions and security policies and can't exceed your authorized access.

Your prompts, context, and operational data are never used to train foundation models.
{: note}

## What you can do with {{site.data.keyword.paver}} in {{site.data.keyword.cloud_notm}}
{: #paver-capabilities}

{{site.data.keyword.paver}} can help you accomplish the following operational goals in your {{site.data.keyword.cloud_notm}} account:

- Deploy applications across {{site.data.keyword.cloud_notm}} infrastructure
- Resolve incidents by correlating logs, metrics, and recent changes
- Optimize infrastructure utilization and reduce operational overhead
- Identify security exposures, policy gaps, and compliance risks
- Surface cost optimization opportunities and unused resources
- Understand infrastructure resources, configurations, and dependencies

These are just a few example use cases where {{site.data.keyword.paver}} can help. Try chatting with {{site.data.keyword.paver}} about your goals or challenges to identify more use cases that are relevant to your environment and workflow, and review additional [common use cases](https://paver.ibm.com/docs/use-cases){: external}.

## How {{site.data.keyword.paver}} works with your {{site.data.keyword.cloud_notm}} account
{: #paver-how-it-works}

When you work with {{site.data.keyword.paver}}, several features and capabilities work together to make it effective across sessions, tasks, and your team's way of working.

### Your account context, always ready
{: #paver-memory}

When you work across multiple {{site.data.keyword.cloud_notm}} accounts, regions, and resource groups, repeating that context in every session adds friction. {{site.data.keyword.paver}} builds a persistent picture of how you work, such as your preferred regions, the projects you return to, and the resources you manage most, and carries that context forward automatically. If your setup changes or {{site.data.keyword.paver}} has something wrong, correct it by telling {{site.data.keyword.paver}} in chat and it updates immediately. For more information about {{site.data.keyword.paver}}'s memory, see [Building persistent context](https://paver.ibm.com/docs/core-concepts/memory){: external}.

### Operating with safeguards
{: #paver-safety}

When you're managing enterprise workloads in {{site.data.keyword.cloud_notm}}, staying in control of what {{site.data.keyword.paver}} does and when is essential. You can set {{site.data.keyword.paver}}'s safety mode to Safe mode, where {{site.data.keyword.paver}} can't modify your resources. In Safe mode, {{site.data.keyword.paver}} can still read your resources, diagnose problems, and read and write files in its sandbox, so you can safely explore your account and plan changes, such as creating scripts or Terraform to implement them. {{site.data.keyword.paver}} can't run those scripts or apply those plans until you switch to Edit mode. When you're ready to act, switching to Edit mode means that {{site.data.keyword.paver}} asks for your explicit approval before each operation runs, and you can modify the exact command before it executes. 

{{site.data.keyword.paver}} Guard adds a risk policy on top of this so you can set thresholds that auto-approve routine operations while holding higher-risk changes for your review, giving you fine-grained control that scales with how comfortable you are with the task at hand. For more information, see [Managing safeguards and controls](https://paver.ibm.com/docs/core-concepts/managing-risk-and-control){: external}.

### Bring your configs and artifacts into the conversation
{: #paver-files}

Managing cloud infrastructure means working with many files, whether it's Terraform plans, Kubernetes manifests, deployment configs, or logs. {{site.data.keyword.paver}} has a persistent file workspace so that you can upload the files that matter to a task, ask {{site.data.keyword.paver}} to review or act on them, and download anything {{site.data.keyword.paver}} generates. Your workspace persists across sessions so the files are there when you return. For more information, see [Sharing files with {{site.data.keyword.paver}}](https://paver.ibm.com/docs/core-concepts/files){: external}.

### Keep your credentials out of the chat
{: #paver-keyring}

Connecting {{site.data.keyword.paver}} to your {{site.data.keyword.cloud_notm}} services often requires working with API keys and service credentials. With the keyring, you can store those secrets once, export them, and then {{site.data.keyword.paver}} injects them as environment variables at the start of each session so they're available when needed, without you ever pasting them into the chat. {{site.data.keyword.paver}} encrypts stored values and doesn't display them after storage. When exported, any command in the conversation can read the value, so export only what you need. Entries expire on a schedule that you control, so credentials don't persist beyond their useful life. For more information, see [Storing your secrets](https://paver.ibm.com/docs/core-concepts/files){: external}.

### Run {{site.data.keyword.cloud_notm}} commands in the same environment {{site.data.keyword.paver}} uses
{: #paver-shell}

When you need to go beyond chat to run a quick `ibmcloud` command, inspect a Kubernetes cluster, or verify a Terraform plan before applying it, {{site.data.keyword.paver}}'s shell puts you directly inside the environment {{site.data.keyword.paver}} uses it to act on your behalf. It comes preinstalled with the {{site.data.keyword.cloud_notm}} CLI, `kubectl`, `helm`, `terraform`, and standard scripting tools, all connected to your account. Open it with `paver shell` from your terminal or `/shell` from a chat session without losing your conversation context. For more information, see [Using the interactive shell](https://paver.ibm.com/docs/core-concepts/shell){: external}.

### Skills that know your services
{: #paver-skills}

{{site.data.keyword.IBM}} maintains a set of built-in skills for working in {{site.data.keyword.cloud_notm}}, which works as domain-specific knowledge that {{site.data.keyword.paver}} loads automatically based on what you ask, covering the right commands, correct sequences, and service-specific considerations for the task at hand. These are called system skills. You can also upload your own user skills to encode team-specific workflows, naming conventions, or organizational expertise. For more information, see [Extending Paver with skills](https://paver.ibm.com/docs/core-concepts/skills){: external}.
