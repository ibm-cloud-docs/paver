---

copyright:
  years: 2026
lastupdated: "2026-10-25"

keywords: paver known issues, paver limitations, IBM Cloud API 403, IBM_CLOUD_REQ_CTX, context token
subcollection: paver

---

{{site.data.keyword.attribute-definition-list}}

# Known issues and limitations for {{site.data.keyword.paver_full_notm}} in {{site.data.keyword.cloud_notm}}
{: #paver-known-issues}

Review known issues and limitations about using {{site.data.keyword.paver_full}} for {{site.data.keyword.cloud}} that can affect your workflows.
{: shortdesc}

## Direct API calls can fail when context-based restrictions are enabled
{: #known-issue-cbr}

If your {{site.data.keyword.cloud_notm}} account uses context-based restrictions, direct API calls that you make inside the {{site.data.keyword.paver}} sandbox might return a `403` error.

{{site.data.keyword.paver}} handles context-based restrictions by creating a context token that captures your client IP address and injecting it into the sandbox as the `IBM_CLOUD_REQ_CTX` environment variable. The {{site.data.keyword.paver}} CLI and built-in scripts automatically include this token when calling {{site.data.keyword.cloud_notm}} APIs. However, this token is not automatically included when you write a prompt that asks {{site.data.keyword.paver}} to call an {{site.data.keyword.cloud_notm}} API directly with `curl` or a custom script. Without the token, context-based restrictions rules can't verify your client context, and the API call fails with a `403 Forbidden` error.

For steps to resolve this issue, see [Why do my direct API calls return a 403 error in the {{site.data.keyword.paver}} sandbox?](/docs/paver?topic=paver-troubleshoot-cbr-403)

## Trusted profiles are not supported for {{site.data.keyword.paver}} sessions
{: #known-issue-trusted-profiles}

{{site.data.keyword.paver}} does not support {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) trusted profiles as the active identity for a session. If you are logged in to the {{site.data.keyword.cloud_notm}} console with a trusted profile selected as your active account identity, {{site.data.keyword.paver}} can't use that trusted profile to authenticate its actions.

To use {{site.data.keyword.paver}}, log in to the console with your standard user identity rather than a trusted profile. Trusted profile support is planned for a future release.

## Human oversight is required for AI-driven operations
{: #known-issue-human-oversight}

Paver, like all AI agents, can make mistakes when reasoning about your environment or executing tasks. It attempts to detect and correct its own errors automatically, but it can get stuck and be unable to proceed on its own. If {{site.data.keyword.paver}} gets stuck, describe a different approach in the chat. For example, suggest an alternative command, a different order of operations, or a simpler way to achieve the same goal. {{site.data.keyword.paver}} incorporates your suggestion and continues from there.

Give additional attention to operations that {{site.data.keyword.paver}} Guard flags as high risk. High-risk operations have a greater potential impact on your environment, and a careful review before you approve those steps reduces the chance of a hard-to-reverse error. For more information, see [Managing safeguards and controls](https://paver.ibm.com/docs/core-concepts/managing-risk-and-control){: external}.
