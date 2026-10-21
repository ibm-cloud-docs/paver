---

copyright:
  years: 2026
lastupdated: "2026-10-21"

keywords: paver 403 error, context-based restrictions API failure, IBM_CLOUD_REQ_CTX, IBM-Cloud-Req-Ctx, curl 403 forbidden paver

subcollection: paver

content-type: troubleshoot

---

{{site.data.keyword.attribute-definition-list}}

# Why do my direct API calls return a 403 error in the Paver sandbox?
{: #troubleshoot-cbr-403}
{: troubleshoot}
{: support}

A `curl` command or custom script that calls an {{site.data.keyword.cloud_notm}} API from inside the Paver sandbox returns a `403 Forbidden` error, even though your IAM permissions are correct.
{: shortdesc}

You observe one or both of the following symptoms:

- A `curl` command to an {{site.data.keyword.cloud_notm}} API returns `403 Forbidden`.
- A custom script that calls {{site.data.keyword.cloud_notm}} APIs fails with an access-denied error.
{: tsSymptoms}

Your {{site.data.keyword.cloud_notm}} account uses context-based restrictions. {{site.data.keyword.paver}} creates a context token that captures your client IP address and injects it into the sandbox as the `IBM_CLOUD_REQ_CTX` environment variable. The {{site.data.keyword.paver}} CLI and built-in scripts automatically include this token when calling {{site.data.keyword.cloud_notm}} APIs. However, when you write a prompt that asks {{site.data.keyword.paver}} to call an {{site.data.keyword.cloud_notm}} API directly with `curl` or a custom script, {{site.data.keyword.paver}} might not include the context token in those requests. Without the token, context-based restrictions rules can't verify your client context, and the API call fails.
{: tsCauses}

When you write a prompt that involves direct API calls, instruct {{site.data.keyword.paver}} to set the `IBM-Cloud-Req-Ctx` request header to the value of the `IBM_CLOUD_REQ_CTX` environment variable. For example:

```sh
curl -X GET "https://resource-controller.cloud.ibm.com/v2/resource_instances" \
  -H "Authorization: Bearer $IAM_TOKEN" \
  -H "IBM-Cloud-Req-Ctx: $IBM_CLOUD_REQ_CTX"
```
{: pre}
{: tsResolve}

For more information about context-based restrictions, see [What are context-based restrictions?](/docs/iam?topic=iam-context-restrictions-whatis){: external}.
