---

copyright:
  years: 2026
lastupdated: "2026-10-26"

keywords: using paver, paver cli, paver chat, paver ask

subcollection: paver

---

{{site.data.keyword.attribute-definition-list}}

# Starting an interactive chat with {{site.data.keyword.paver_full_notm}} in {{site.data.keyword.cloud_notm}}
{: #paver-using}

Learn how to work with {{site.data.keyword.paver_full_notm}} by starting an interactive chat session in the {{site.data.keyword.cloud_notm}} console or CLI.
{: shortdesc}


## Starting a chat in {{site.data.keyword.paver}} CLI
{: #paver-chat-session-cli}
{: cli}

In the {{site.data.keyword.paver}} CLI, start an interactive chat session:

```sh
paver chat
```
{: pre}

Or send a single question and get an answer. `paver ask` is useful for AI automation and scripts because you can send a single message, stream the response, and exit.

```sh
paver ask "what can you help me with?"
```
{: pre}

Don't enter personal information, API keys, or other secrets in your prompts to {{site.data.keyword.paver}}.
{: note}


## Starting a chat in the console
{: #paver-chat-session}
{: ui}

You can quickly start a chat session with {{site.data.keyword.paver}} in the console.

1. From the {{site.data.keyword.cloud_notm}} console menu bar, click the **Help** icon ![Help icon](../icons/help.svg "Help") > **Paver AI assistant**.
1. Choose a starter prompt from the Getting started, Create, or Investigate categories, or enter your own question. Use natural language to describe what you want to do or what you want to know.

   Don't enter personal information, API keys, or other secrets in your prompts to Paver.
   {: note}

1. Click **Send message** to start your chat.


## Tips for chatting with {{site.data.keyword.paver}}
{: #chat-tips}

Using an interactive chat session to understand more about {{site.data.keyword.paver}}, your account, and resources is as easy as asking a question like you would to a team member. Use natural language to describe a challenge you're facing, a plan you want to make, a goal you want to accomplish, or a task that you want it to act on for you. Here are some tips for chatting with {{site.data.keyword.paver}}:

Before you start a task, check whether {{site.data.keyword.paver}} is in Safe mode or Edit mode. The starting mode is set automatically based on your account name: accounts with `prod` or `production` in the name start in Safe mode, and accounts with `dev`, `test`, or `stage` start in Edit mode. If you're exploring or getting started, verify that you're in Safe mode before you proceed.
{: important}

Ask {{site.data.keyword.paver}} what you want to know directly
:   Run `paver ask "what can you help me with?"` or inside a chat session ask questions like `Can you help me identify resources that are rarely used` to explore what {{site.data.keyword.paver}} can do for your task.

Work together to make a plan before you act
:   You can ask {{site.data.keyword.paver}} to explain a service, a resource, or a proposed change before letting it make one. In Safe mode, {{site.data.keyword.paver}} can't modify your resources, but it can still read your resources and write files in its sandbox, such as plans, scripts, or Terraform. This makes exploring low-stakes.

Be goal-oriented
:   Instead of asking `How do I check my cluster status?`, tell {{site.data.keyword.paver}} your goal, for example `Check if my Kubernetes cluster iks-useast-ha-cluster is healthy and let me know if any pods are crashing`.

Use contextual references
:   {{site.data.keyword.paver}} has access to a persistent file system and memory. If you have a configuration file or a log, upload it and use an `@` reference to the file in your chat message. Similarly, you can quickly tell {{site.data.keyword.paver}} to inspect or work with specific resources with `@` references.

Iterate and refine
:   If the first response isn't exactly what you need, guide {{site.data.keyword.paver}} by telling it to focus on something specific, for example provide a full CLI example and explain each option, or guide it to use a specific tool if necessary.

Don't forget to use slash commands
:   In an interactive chat, you can use the slash [chat commands](https://paver.ibm.com/docs/tui-reference){: external} as your built-in shortcuts. For example, `/files` is used to manage your files in the persistent file system and `/memory` can help you view and manage what {{site.data.keyword.paver}} remembers about your account and preferences.
