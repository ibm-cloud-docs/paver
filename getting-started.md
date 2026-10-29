---

copyright:
  years: 2026
lastupdated: "2026-10-29"

keywords: paver getting started, paver console, chat with paver

subcollection: paver

content-type: tutorial
completion-time: 10m

---

{{site.data.keyword.attribute-definition-list}}

# Getting started with {{site.data.keyword.paver_full_notm}} in {{site.data.keyword.cloud_notm}}
{: #getting-started}
{: toc-content-type="tutorial"}
{: toc-completion-time="10m"}

Learn how to get started with {{site.data.keyword.paver_full}} in the {{site.data.keyword.cloud}}. {{site.data.keyword.paver}} is available in the {{site.data.keyword.cloud_notm}} console, where you can quickly start a chat with {{site.data.keyword.paver}} to manage your cloud operations, account resources, and infrastructure.
{: shortdesc}

To interact with {{site.data.keyword.paver}} from your terminal instead, see [Installing {{site.data.keyword.paver}} CLI](/docs/paver?topic=paver-paver-cli-install).

## Access {{site.data.keyword.paver}} in the console
{: #paver-console}
{: step}

{{site.data.keyword.paver}} is built into the {{site.data.keyword.cloud_notm}} console, so you can access it from anywhere in your account without leaving the page you're on.

1. Log in to your {{site.data.keyword.cloud_notm}} account.
1. From the {{site.data.keyword.cloud_notm}} console menu bar, click the **Help** icon ![Help icon](../icons/help.svg "Help") > **{{site.data.keyword.paver}} AI assistant**.

Note the mode switcher where you can change between **Safe** and **Edit** mode. Since you're just getting started, stay in safe mode for now, which keeps {{site.data.keyword.paver}} from modifying your resources until you're ready. You can still ask {{site.data.keyword.paver}} to explore your account and plan changes.
{: tip}

## Take the getting started tour
{: #tour}
{: step}

To help you get familiar with {{site.data.keyword.paver}} in the console, you can take a quick tour.

1. From {{site.data.keyword.paver}} in the console, click the **Help** icon ![Help icon](../icons/help.svg "Help") > **Getting started tour**.
1. Select **Let's get started**.
1. Follow the prompts to tell {{site.data.keyword.paver}} a little bit about yourself and try out a prompt for the first time.


## Start a new conversation
{: #paver-interactive}
{: step}

Pick a starter prompt or write your own to send a first message to {{site.data.keyword.paver}}.

1. Select **New task** to start a new conversation.
1. Choose a starter prompt from the Getting started, Create, or Investigate categories, or type your own question. Use natural language to describe what you want to do or what you want to know.
1. Click **Send message** to start the conversation.

You can ask {{site.data.keyword.paver}} to tell you about its capabilities and features to learn more about how {{site.data.keyword.paver}} can assist. It knows your account and resources, so it can help you troubleshoot, gain insight, make a plan, or accomplish a task.
{: tip}

## Tell {{site.data.keyword.paver}} about how you work
{: #personalize-workflow}
{: step}

{{site.data.keyword.paver}} remembers things about you across conversations such as your preferred regions, how you like to work, the projects you're running, and other context that makes future interactions faster and more relevant. This is called memory in Paver. You can explicitly teach Paver about your preferences by telling Paver directly in a chat, or you can try out the personalization workflow to have {{site.data.keyword.paver}} ask you a series of questions about your working style and preferences:

1. In the chat, enter the `/personalize` slash command and send it as a message. This starts an interactive interview to help {{site.data.keyword.paver}} learn more about your preferences.
1. Respond to {{site.data.keyword.paver}} as it asks you questions to build new memories.

You can view and change these memories later from the **Memories** settings page, or you can tell {{site.data.keyword.paver}} to delete or update a memory directly in an interactive chat.


## Explore the settings
{: #paver-settings}
{: step}

Set your theme, language preference, or Paver Guard approval policies that put guardrails in place and control how often you're asked to approve specific actions.

1. Click the **Settings** icon ![Settings](../icons/settings.svg "Settings icon").
1. Set your theme to match how you like to work.
1. Set your preferred language.
1. Review the auto-approve and auto-deny options. For more information about setting guard policies, see [Managing safeguards and controls](https://paver.ibm.com/docs/core-concepts/managing-risk-and-control).
1. Select **All settings** to explore more options for managing memories, storing secrets in the keyring, switching your plan, or updating the region where your data is stored.

## Next steps
{: #next-steps}
{: step}

Now that you know how to find {{site.data.keyword.paver}} and start a chat, you can explore all of the possibilities by chatting directly with {{site.data.keyword.paver}}. {{site.data.keyword.paver}} is your best guide to understanding all of its capabilities and making a plan to streamline your infrastructure operations.

You can also use the following resources to learn more about Paver:
* For more information about {{site.data.keyword.paver}} and its core concepts and tasks, see [IBM {{site.data.keyword.paver}}](https://paver.ibm.com/docs/welcome){: external}.
* Explore [common use cases](https://paver.ibm.com/docs/use-cases){: external} and [best practices](https://paver.ibm.com/docs/best-practices){: external} to learn more about what {{site.data.keyword.paver}} can do.
* Decide which [plan](/docs/paver?topic=paver-paver-plans) works best for you.
* [Install the {{site.data.keyword.paver}} CLI](/docs/paver?topic=paver-paver-cli-install) to work with {{site.data.keyword.paver}} in your terminal.
