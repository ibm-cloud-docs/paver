---

copyright:
  years: 2026
lastupdated: "2026-10-08"

keywords: paver known issues, paver limitations, context-based restrictions, CBR, IBM Cloud API blocked

subcollection: paver

---

{{site.data.keyword.attribute-definition-list}}

# Known issues and limitations
{: #paver-known-issues}

Review known issues and limitations for IBM Paver in {{site.data.keyword.cloud}} that might affect your workflows.
{: shortdesc}

## Context-based restrictions can block Paver API calls
{: #known-issue-cbr}

If your {{site.data.keyword.cloud_notm}} account has context-based restrictions enabled, Paver's direct calls to {{site.data.keyword.cloud_notm}} APIs might be blocked.

Paver acts on your behalf by making API calls to {{site.data.keyword.cloud_notm}} services from IBM-managed infrastructure. When context-based restrictions rules are in place on your account or on specific services, those rules evaluate the network context of every incoming API request. Because Paver's requests originate from IBM-managed infrastructure rather than your local network, VPC, or other allowed network zones that your rules recognize, those requests may be denied even though Paver is operating with your valid credentials and IAM permissions.

This issue affects any {{site.data.keyword.cloud_notm}} service or resource that is protected by a context-based restrictions rule.
{: note}

You might observe any of the following:

- Paver reports that an API call failed with a `403 Forbidden` or access-denied error, even though the authenticated user has the correct IAM permissions for the requested action.
- Paver is unable to list, read, or modify resources in your account despite your IAM roles appearing correct.
- Actions that work in the {{site.data.keyword.cloud_notm}} console or from your local machine fail when Paver attempts the same operation.

To address this limitation, you might need to adjust context-based restrictions in the account. For more information about managing network zones and service references, see [What are context-based restrictions](/docs/account?topic=account-context-restrictions-whatis) and [Managing context-based restrictions](/docs/iam?topic=iam-context-restrictions-update).
