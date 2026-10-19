---

copyright:
  years: 2026, 2026
lastupdated: "2026-10-19"

keywords: paver help, paver support, paver feedback, troubleshoot paver, paver issue

subcollection: paver

---

{{site.data.keyword.attribute-definition-list}}

# Getting help and support with Paver in {{site.data.keyword.cloud_notm}}
{: #help-and-support}

If you experience an issue or have questions when using Paver, start by asking Paver directly in a chat session. Paver can help diagnose and resolve many common issues.
{: shortdesc}

If you still can't resolve the problem, you can request help without ever leaving the conversation. Depending on your support plan, Paver can open a support case on your behalf or hand you off to a live support engineer with your full conversation history included so you don't have to start over. You can also submit feedback directly from a chat session to help improve the Paver experience.

## Ask Paver for help
{: #paver-chat}

The fastest way to get help is to ask Paver directly. Paver can help you understand its capabilities, available commands, their usage, and how to troubleshoot issues. If you reach a point where you need additional support, ask Paver without leaving the conversation.

Based on your [support plan](/docs/support?topic=support-support-plans), Paver can do the following:

- **Open a support case** on your behalf. Paver pre-populates the case with relevant details from your conversation, so you don't need to re-describe the issue.
- **Connect you with a live support engineer** through live chat. If your support plan includes live chat, Paver hands off the conversation to a support engineer, including the full history of your chat session.

- In an interactive chat with Paver in the console, explain what issue you're having and work with Paver to resolve it.
- If you're using the CLI, start a chat or use the help commands:

   Start an interactive session in the CLI by running the following command:

   ```sh
   paver chat
   ```
   {: pre}

   From the `paver chat` session, you can ask Paver about anything, from CLI help and command syntax to understanding how specific features work. For a full list of available commands, use the built-in help:

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

If you can't resolve an issue by asking Paver or reviewing the documentation, ask Paver to open a support case. Paver pre-populates the case with context from your conversation, including relevant session details, so you don't need to describe the issue from scratch.

Before you open a case, check the following:

- Check the status of {{site.data.keyword.cloud_notm}} platform and resources on the [Status page](https://cloud.ibm.com/status){: external} to rule out a platform-level incident.
- Review [Stack Overflow](https://stackoverflow.com/questions/tagged/ibm-cloud){: external} to see whether other users encountered the same problem. When you post a question, tag it with `ibm-cloud` and `paver` so that it's visible to the {{site.data.keyword.cloud_notm}} development teams.

To open a case from the conversation, ask Paver: *"Open a support case"* or *"I need to submit a support ticket."* Paver guides you through the required details and submits the case. To open a case manually, see [Creating support cases](/docs/support?topic=support-open-case).

Based on your [support plan](/docs/support?topic=support-support-plans), you might have access to additional support options, including priority handling and direct access to a support engineer through live chat.

### Providing support case details
{: #paver-support-case-details}

To help the support team investigate your issue quickly, include the following information in your support case:

1. Describe the issue and include the exact steps to reproduce it, if applicable.
2. Include the Paver session ID. From a chat session, run the following command to retrieve it:

   ```sh
   /info
   ```
   {: pre}

3. Include the relevant output from the Paver session, such as error messages, unexpected responses, or command output.
4. If the issue involves the Paver CLI, include the CLI version by running the following command:

   ```sh
   paver --version
   ```
   {: pre}

5. If the issue involves a specific {{site.data.keyword.cloud_notm}} resource, include the resource ID and region.

## Submitting feedback in Paver
{: #paver-feedback}

Your feedback is valuable in helping improve the Paver experience. Submit feedback directly from an interactive chat session:

```sh
/feedback "Your feedback message here"
```
{: pre}

The following examples show helpful feedback messages:

```sh
/feedback "This was great! I successfully automated a complex deployment workflow"
```
{: pre}

```sh
/feedback "Encountered difficulty with resource provisioning commands"
```
{: pre}

When you submit feedback, relevant logs and diagnostic data are automatically sent for analysis.
{: note}
