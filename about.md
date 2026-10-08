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

Learn about IBM Paver, {{site.data.keyword.IBM}}'s embedded agentic AI operator for {{site.data.keyword.IBM_notm}} infrastructure operations, its capabilities, and how it works with your account. Paver is available within supported {{site.data.keyword.IBM_notm}} offerings, which includes {{site.data.keyword.cloud}}. For more information, see [IBM Paver](https://paver.ibm.com/){: external}.
{: shortdesc}

In {{site.data.keyword.cloud_notm}}, Paver is a built-in agentic AI operator that helps you deploy, operate, and troubleshoot your cloud resources through natural language. It is available directly in the {{site.data.keyword.cloud_notm}} console and through the Paver CLI, so you can work with your accounts, services, and infrastructure without switching between tools.

Rather than generating code for you to run elsewhere, Paver acts on your behalf within {{site.data.keyword.cloud_notm}}. It runs commands and scripts in a secure sandbox, reads your account context, reasons about what needs to happen, explains its plan, and executes approved changes against your live environment.

Paver is built for environments where reliability, governance, and accountability matter. Every action is recorded through a complete audit trail. Paver operates within your existing permissions and security policies and can't exceed your authorized access.

Your prompts, context, and operational data are never used to train foundation models.
{: note}

## How Paver works with your account
{: #paver-how-it-works}

When you work with Paver, several capabilities work together to make it effective across sessions, tasks, and your team's way of working.

### Your account context, always ready
{: #paver-memory}

When you work across multiple {{site.data.keyword.cloud_notm}} accounts, regions, and resource groups, repeating that context in every session adds friction. Paver builds a persistent picture of how you work, such as your preferred regions, the projects you return to, and the resources you manage most, and carries that context forward automatically. If your setup changes or Paver has something wrong, correct it by telling Paver in chat and it updates immediately. For more information about Paver's memory, see [Building persistent context](https://paver.ibm.com/docs/core-concepts/memory){: external}.

### Bring your configs and artifacts into the conversation
{: #paver-files}

Managing cloud infrastructure means working with a lot of files, whether it's Terraform plans, Kubernetes manifests, deployment configs, or logs. Paver has a persistent file workspace so that you can upload the files that matter to a task, ask Paver to review or act on them, and download anything Paver generates. Your workspace persists across sessions, so files are there when you return. For more information, see [Sharing files with Paver](https://paver.ibm.com/docs/core-concepts/files){: external}.

### Keep your credentials out of the chat
{: #paver-keyring}

Connecting Paver to your {{site.data.keyword.cloud_notm}} services often means working with API keys and service credentials. The keyring lets you store those secrets once, and then Paver injects them as environment variables at the start of each session so they're available when needed, without you ever pasting them into the chat. Secret values are never displayed after storage and are automatically redacted from Paver's output. Entries expire on a schedule you control, so credentials don't persist beyond their useful life. For more information, see [Storing your secrets](https://paver.ibm.com/docs/core-concepts/files){: external}.

### Run {{site.data.keyword.cloud_notm}} commands in the same environment Paver uses
{: #paver-shell}

When you need to go beyond chat to run a quick `ibmcloud` command, inspect a Kubernetes cluster, or verify a Terraform plan before applying it, Paver's shell puts you directly inside the environment Paver uses it to act on your behalf. It comes preloaded with the {{site.data.keyword.cloud_notm}} CLI, `kubectl`, `helm`, `terraform`, and standard scripting tools, all connected to your account. Open it with `paver shell` from your terminal or `/shell` from a chat session without losing your conversation context. For more information, see [Using the interactive shell](https://paver.ibm.com/docs/core-concepts/shell){: external}.

### Skills that know your services
{: #paver-skills}

IBM maintains a set of built-in skills for {{site.data.keyword.cloud_notm}} services, which works as domain-specific knowledge that Paver loads automatically based on what you ask, covering the right commands, correct sequences, and service-specific considerations for the task at hand. These are called system skills. You can also upload your own user skills to encode team-specific workflows, naming conventions, or runbooks. For more information, see [Extending Paver with skills](https://paver.ibm.com/docs/core-concepts/skills){: external}.

### Operating with safeguards
{: #paver-safety}

When you're managing enterprise workloads on {{site.data.keyword.cloud_notm}}, staying in control of what Paver does and when is essential. By default, Paver operates in Safe mode where it can read your resources, diagnose problems, and explain what it would do, but it won't make changes. When you're ready to take action, switching to Edit mode means Paver asks for your explicit approval before each operation runs, and you can modify the exact command before it executes. Paver Guard adds a risk policy on top of this so you can set thresholds that auto-approve routine operations while holding higher-risk changes for your review, giving you fine-grained control that scales with how comfortable you are with the task at hand. For more information, see [Managing safeguards and controls](https://paver.ibm.com/docs/core-concepts/managing-risk-and-control){: external}.

## What you can do with Paver
{: #paver-capabilities}

Paver can help you accomplish the following operational goals in your {{site.data.keyword.cloud_notm}} account:

- Deploy applications across {{site.data.keyword.cloud_notm}} infrastructure
- Resolve incidents by correlating logs, metrics, and recent changes
- Optimize infrastructure utilization and reduce operational overhead
- Identify security exposures, policy gaps, and compliance risks
- Surface cost optimization opportunities and unused resources
- Understand infrastructure resources, configurations, and dependencies

These are just a few example use cases where Paver can help. Try chatting with Paver about your goals or pain points to identify additional use cases that are relevant to your environment and workflow.

## Paver plans
{: #paver-plan-details}

Paver has a Free and Professional plan. Each plan includes a monthly credit allocation for running Paver operations. Credits are consumed as you use Paver, and when credits are exhausted, the behavior depends on your plan. Credits reset on the first of every month. For full details on cost and included features per plan, go to [TBD](TBD). 

Free
:   The Free plan is designed for individual exploration and learning. You receive 1,000 credits per month at no cost. When credits are exhausted, Paver enters read-only mode, meaning it can continue to provide information and guidance but can't' take actions on your behalf until credits renew. Supported features may vary.

Professional
:   The Professional plan is designed for individual practitioners and teams who run regular operations. When credits are exhausted, additional usage is billed on a pay-as-you-go basis per credit.

You can upgrade from the Free plan to the Professional plan at any time. If you are reaching your limit on the Free plan, you are prompted in the console with alerts that you're reaching your limit and you can choose to upgrade at that time too.

1. Go to ![Help icon](../icons/help.svg "Help") **Help** menu and select **Ask Paver**.
1. **TBD on whether they can go through catalog**

## Next steps
{: #paver-plans-next-steps}

You can get started with Paver for free today. Check out the following resources:

- [Getting started with Paver](/docs/paver?topic=paver-getting-started)
- [Learn more about Paver](/docs/paver?topic=paver-paver-about)
