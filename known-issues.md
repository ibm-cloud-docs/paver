---

copyright:
  years: 2026
lastupdated: "2026-10-08"

keywords: paver known issues, paver limitations, context-based restrictions, IBM Cloud API 403, IBM_CLOUD_REQ_CTX, context token

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

Paver handles context-based restrictions by creating a context token that captures your client IP address and injecting it into the sandbox as the `IBM_CLOUD_REQ_CTX` environment variable. The Paver CLI and built-in scripts automatically include this token when calling {{site.data.keyword.cloud_notm}} APIs, so those calls pass context-based restrictions checks.

However, if you write a prompt that asks Paver to call an {{site.data.keyword.cloud_notm}} API directly with `curl` or a custom script, Paver might not include the context token in those requests. Without the token, context-based restrictions rules can't verify your client context, and the API call fails.

You might observe either of the following:

- A `curl` command to a {{site.data.keyword.cloud_notm}} API returns `403 Forbidden`, even though your IAM permissions are correct.
- A custom script that calls {{site.data.keyword.cloud_notm}} APIs fails with an access-denied error.

To address this, when you write a prompt that involves direct API calls, instruct Paver to set the `IBM-Cloud-Req-Ctx` request header to the value of the `IBM_CLOUD_REQ_CTX` environment variable. For example:

```sh
curl -X GET "https://resource-controller.cloud.ibm.com/v2/resource_instances" \
  -H "Authorization: Bearer $IAM_TOKEN" \
  -H "IBM-Cloud-Req-Ctx: $IBM_CLOUD_REQ_CTX"
```
{: pre}

For more information about context-based restrictions, see [What are context-based restrictions](/docs/account?topic=account-context-restrictions-whatis){: external}.
