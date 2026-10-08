---

copyright:
  years: 2026
lastupdated: "2026-10-08"

keywords: paver help, paver support, paver feedback, troubleshoot paver

subcollection: paver

---

{{site.data.keyword.attribute-definition-list}}

# Getting help and support with Paver
{: #help-and-support}

If you experience an issue or have questions, you can ask Paver directly, open a support case, or submit feedback to help improve the product.
{: shortdesc}

## Ask Paver for help
{: #paver-chat}

The fastest way to get help is to ask Paver directly. Paver can help you understand its capabilities, available commands and their usage, and how to troubleshoot issues that arise. If you get to a point where you need additional support, just ask Paver. Based on your [support plan](/docs/support?topic=support-support-plans), you can work with Paver to open a support case or connect with a live support engineer.

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
