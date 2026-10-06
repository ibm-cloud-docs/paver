---

copyright:
  years: 2026
lastupdated: "2026-10-06"

keywords: using paver, paver cli, paver chat, paver ask, update paver cli

subcollection: paver

---

{{site.data.keyword.attribute-definition-list}}

# Working with IBM Paver
{: #paver-using}

Learn how to work with Paver, start chat sessions in the CLI, ask questions, and keep your CLI updated.
{: shortdesc}

From discovering what Paver can do to working in the CLI, Paver is the best guide to help you be successful.

- **Ask Paver directly**: Run `paver ask "what can you help me with?"` or, inside a chat session, ask questions like "can you help me troubleshoot a Kubernetes cluster" to explore what Paver can do for your task.
- **Ask before you act**: You can ask Paver to explain a service, a resource, or a proposed change before letting it make one. In safe mode (the default), high-risk write operations are blocked, so exploring is low-stakes.


## Starting a chat session in the CLI
{: #paver-chat-session}

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

## Updating the Paver CLI
{: #paver-update-cli}

The Paver CLI automatically checks for updates on a schedule. To update immediately to the latest version, run the following command:

```sh
paver update
```
{: pre}

Keep your CLI updated to ensure compatibility with the server.
{: important}
