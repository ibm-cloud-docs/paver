---

copyright:
  years: 2026, 2026
lastupdated: "2026-10-25"

keywords: paver help, paver support, paver feedback, troubleshoot paver, paver issue

subcollection: paver

---

{{site.data.keyword.attribute-definition-list}}

# Getting help and support with {{site.data.keyword.paver_full_notm}} for {{site.data.keyword.cloud_notm}}
{: #help-and-support}

If you experience an issue or have questions when using {{site.data.keyword.paver_full}}, start by asking {{site.data.keyword.paver}} directly in a chat session. {{site.data.keyword.paver}} can help diagnose and resolve many common issues.
{: shortdesc}

If you still can't resolve the problem, you can request help without ever leaving the conversation. You can ask {{site.data.keyword.paver}} to open a support case for you, with details from your conversation already included. You can also submit feedback directly from a chat session to help improve the Paver experience.

## Ask {{site.data.keyword.paver}} for help
{: #paver-chat}

The fastest way to get help is to ask {{site.data.keyword.paver}} directly. {{site.data.keyword.paver}} can help you understand its capabilities, available commands, their usage, and how to troubleshoot issues.

- In an interactive chat with {{site.data.keyword.paver}} in the console, explain what issue you're having and work with {{site.data.keyword.paver}} to resolve it.
- If you're using the CLI, start a chat or use the help commands:

   Start an interactive session in the CLI by running the following command:

   ```sh
   paver chat
   ```
   {: pre}

   From the interactive chat session, you can ask {{site.data.keyword.paver}} about anything, from CLI help and command syntax to understanding how specific features work. For a full list of available commands, use the built-in help:

   ```sh
   paver help
   ```
   {: pre}

   For detailed information about a specific command, run:

   ```sh
   paver help [command]
   ```
   {: pre}


## Opening a support case
{: #paver-support-case}

Before you open a case, check the following:

- Review the documentation for the specific services or resources that you're working with, if it is not an issue specific to {{site.data.keyword.paver}} itself.
- Check the status of {{site.data.keyword.cloud_notm}} platform and resources on the [Status page](https://cloud.ibm.com/status){: external} to rule out a platform-level incident.
- Review [Stack Overflow](https://stackoverflow.com/questions/tagged/ibm-cloud){: external} to see whether other users encountered the same problem. When you post a question, tag it with `ibm-cloud` and `paver` so that it's visible to the {{site.data.keyword.cloud_notm}} development teams.

If you can't resolve an issue by troubleshooting with {{site.data.keyword.paver}}, ask {{site.data.keyword.paver}} to open a support case. You can do this in an interactive chat in the CLI or in the console.

To open a case from the conversation, tell {{site.data.keyword.paver}} in natural language that you need to open a support case about a specific issue. For example, you can say `Open a support case about my failed deployment` or `I need to submit a support case for a provisioning error.` {{site.data.keyword.paver}} might ask you additional questions to clarify the issue you're experiencing, then it opens the case for you and populates the case subject, description, and other details based on your conversation about the issue, so you don't need to describe the issue from scratch.

The type of case that you can open depends on your [support plan](/docs/support?topic=support-support-plans). For example, if you have a Basic support plan, you can't open technical cases. To open a case manually, see [Creating support cases](/docs/support?topic=support-open-case).

## Submitting feedback in {{site.data.keyword.paver}}
{: #paver-feedback}

Your feedback is valuable in helping improve the {{site.data.keyword.paver}} experience. Submit feedback directly from an interactive chat session in the console:

```sh
/feedback create "Your feedback message here"
```
{: pre}

The following examples show feedback submissions:

```sh
/feedback create "This was great! I successfully automated a complex deployment workflow"
```
{: pre}

```sh
/feedback create "Encountered difficulty with resource provisioning commands"
```
{: pre}

You can also use the `paver feedback create <your-feedback>` command in the CLI or `/feedback <your-feedback>` in an interactive chat in your terminal.

When you submit feedback, relevant logs and diagnostic data are automatically sent for analysis.
{: note}
