---

copyright:
  years: 2026
lastupdated: "2026-10-10"

keywords: paver known issues, paver limitations, context-based restrictions, IBM Cloud API 403, IBM_CLOUD_REQ_CTX, context token, trusted profiles, human oversight, AI operations, paver guard

subcollection: paver

---

{{site.data.keyword.attribute-definition-list}}

# Known issues and limitations
{: #paver-known-issues}

Review known issues and limitations for IBM Paver in {{site.data.keyword.cloud}} that might affect your workflows.
{: shortdesc}

## Direct API calls can fail when context-based restrictions are enabled
{: #known-issue-cbr}

If your {{site.data.keyword.cloud_notm}} account uses context-based restrictions, direct API calls that you make inside the Paver sandbox might return a `403` error.

Paver handles context-based restrictions by creating a context token that captures your client IP address and injecting it into the sandbox as the `IBM_CLOUD_REQ_CTX` environment variable. The Paver CLI and built-in scripts automatically include this token when calling {{site.data.keyword.cloud_notm}} APIs. However, this token is not automatically included when you write a prompt that asks Paver to call an {{site.data.keyword.cloud_notm}} API directly with `curl` or a custom script. Without the token, context-based restrictions rules can't verify your client context, and the API call fails with a `403 Forbidden` error.

For steps to resolve this issue, see [Why do my direct API calls return a 403 error in the Paver sandbox?](/docs/paver?topic=paver-troubleshoot-cbr-403).

## Trusted profiles are not supported for Paver sessions
{: #known-issue-trusted-profiles}

Paver does not support IBM Cloud Identity and Access Management (IAM) trusted profiles as the active identity for a session. If you are logged in to the {{site.data.keyword.cloud_notm}} console with a trusted profile selected as your active account identity, Paver cannot use that trusted profile to authenticate its actions.

To use Paver, log in to the console with your standard user identity rather than a trusted profile. Trusted profile support is planned for a future release.

## Human oversight is required for AI-driven operations
{: #known-issue-human-oversight}

Paver, like all AI agents, can make mistakes when reasoning about your environment or executing tasks. It attempts to detect and correct its own errors automatically, but it can get stuck and be unable to proceed on its own. If Paver gets stuck, describe a different approach in the chat. For example, suggest an alternative command, a different order of operations, or a simpler way to achieve the same goal. Paver incorporates your suggestion and continues from there.

Give extra attention to operations that Paver Guard flags as high risk. High-risk operations have a greater potential impact on your environment, and a careful review before you approve those steps reduces the chance of a hard-to-reverse error. For more information, see [Managing safeguards and controls](https://paver.ibm.com/docs/core-concepts/managing-risk-and-control){: external}.
