---

copyright:
  years: 2026
lastupdated: "2026-10-19"

keywords: using paver, paver cli, paver chat, paver ask, update paver cli

subcollection: paver

---

{{site.data.keyword.attribute-definition-list}}

# Starting an interactive chat with IBM Paver in {{site.data.keyword.cloud_notm}}
{: #paver-using}

Learn how to work with Paver by starting an interactive chat session in the console and CLI. From discovering what Paver can do to working in the CLI, Paver is the best guide to help you be successful.
{: shortdesc}

Ask Paver directly
:   Run `paver ask "what can you help me with?"` or inside a chat session ask questions like `can you help me identify resources that are rarely used` to explore what Paver can do for your task.

Ask before you act
:   You can ask Paver to explain a service, a resource, or a proposed change before letting it make one. In Safe mode, Paver can't modify your resources, but it can still read your resources and write files in its sandbox, such as plans, scripts, or Terraform. This makes exploring low-stakes.


## Starting a chat in the CLI
{: #paver-chat-session-cli}
{: cli}

In the CLI, start an interactive chat session:

```sh
paver chat
```
{: pre}

Or send a single question and get an answer:

```sh
paver ask "what can you help me with?"
```
{: pre}

Don't enter personal information, API keys, or other secrets in your prompts to Paver.
{: note}


## Starting a chat in the console
{: #paver-chat-session}
{: ui}

Starting a chat session with Paver in the console is simple. It's deciding

1. From the {{site.data.keyword.cloud_notm}} console menu bar, click ![Help icon](../icons/help.svg "Help") > **Chat with Paver**.
1. Choose a starter prompt from the Getting started, Create, or Investigate categories, or type your own question. Use natural language to describe what you want to do or what you want to know.
1. Click **Send message** to start your chat.
