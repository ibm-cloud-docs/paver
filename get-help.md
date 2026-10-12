---

copyright:
  years: 2026
lastupdated: "2026-10-12"

keywords: paver help, paver support, paver feedback, troubleshoot paver

subcollection: paver

---

{{site.data.keyword.attribute-definition-list}}

# Getting help and support with Paver
{: #help-and-support}

If you experience an issue or have questions when using Paver, start by asking Paver directly in a chat session. Paver can help diagnose and resolve many common issues. If you still can't resolve the problem, you can open a support case with IBM Cloud Support. You can also submit feedback directly from a chat session to help improve the Paver experience.
{: shortdesc}

## Ask Paver for help
{: #paver-chat}

The fastest way to get help is to ask Paver directly. Paver can help you understand its capabilities, available commands, and their usage, and how to troubleshoot issues that arise. If you get to a point where you need extra support, ask Paver. Based on your [support plan](/docs/support?topic=support-support-plans), you can work with Paver to open a support case or connect with a live support engineer.

* In an interactive chat with Paver in the console, explain what issue you're having and work with Paver to resolve it.
* If you're using the CLI, start a chat or use the help commands:

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

If you can't resolve an issue by asking Paver or reviewing the documentation, you can open a support case with IBM Cloud Support.

Before you open a case, try the following:

* Check the status of {{site.data.keyword.cloud_notm}} platform and resources on the [Status page](https://cloud.ibm.com/status){: external} to rule out a platform-level incident.
* Review [Stack Overflow](https://stackoverflow.com/questions/tagged/ibm-cloud){: external} to see whether other users ran into the same problem. When you post a question, tag it with `ibm-cloud` and `paver` so that it's visible to the {{site.data.keyword.cloud_notm}} development teams.

When you're ready to open a case, go to [Creating support cases](/docs/get-support?topic=get-support-open-case) for instructions. Based on your [support plan](/docs/get-support?topic=get-support-support-plans), you might have access to more support options including priority handling and direct access to a support engineer.

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
