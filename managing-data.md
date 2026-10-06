---

copyright:
  years: 2026
lastupdated: "2026-10-06"

keywords: manage paver data, paver data retention, export paver data, delete paver data, paver data residency, paver responsibilities

subcollection: paver

---

{{site.data.keyword.attribute-definition-list}}

# Managing your Paver data
{: #paver-managing-data}

Paver stores information that helps personalize your experience, maintain conversation history, and provide context-aware assistance across your {{site.data.keyword.cloud}} environment. Learn what data is stored, how it is retained, how to export or delete it, and the responsibilities of {{site.data.keyword.IBM_notm}} and customers for data management and resiliency.
{: shortdesc}

## Data storage and retention
{: #paver-data-storage-retention}

Paver stores user-specific information to support conversations, memories, and personalized interactions.

Examples of stored data include:

- Conversation history
- User memories and preferences established through interactions
- Service-generated data required to support Paver functionality [VERIFY: Customer data persisted in Postgres and COS. Should this be mentioned or clarified as to what the data is?]
- Usage and metering information for operational reporting purposes, for example token usage and model utilization. User prompts are not retained or used to train models.

Paver automatically removes inactive user data after a 90-day retention period. By default conversations and memories associated with inactive users are automatically deleted after approximately 90 days. However, users can delete their stored Paver data at any time.

## Exporting your data
{: #paver-exporting-data}

Paver provides capabilities that allow users to export their personal Paver data.

Users can export:

- Conversation history
- Stored memories

Exports are performed at the individual user level. Exporting conversations and stored memories across accounts or an enterprise is not supported.

Paver does not currently provide tools to export or migrate an entire organization's Paver environment between regions. If an organization wants to move a deployment from one region to another, users might need to re-establish context and memories in the target region.
{: note}

## Deleting your data
{: #paver-deleting-data}

Users can permanently delete their stored Paver data. Information that users can delete includes conversations history and stored memories.

In addition to user-initiated deletion of data, inactive user data is automatically removed after the 90 day retention period.

## Data residency
{: #paver-data-residency}

Paver is designed as a regional service. Customer data that is stored by Paver remains in the region associated with that Paver deployment. For example:

- Data stored in a European region remains in Europe.
- Data stored in a US region remains in the United States.

Leveraging a regional deployment helps organizations meet data residency requirements and maintain control of where Paver data is stored.

[VERIFY: whether US East inferencing dependency should be disclosed here. If yes, add: "Note: Paver relies on US East inferencing systems for some operations."]

## Availability and regional resiliency
{: #paver-availability-resiliency}

Paver is available as a regional service. If a region becomes unavailable:



- Data that exists in that region is not automatically available from another region.
- Paver does not currently provide automatic cross-region failover for customer data.
- Switching to another region might require users to begin with a new set of conversations and memories.

Organizations that require higher levels of resiliency should evaluate whether additional regional deployments are appropriate for their business requirements. [VERIFY: Can a customer actually create additional regional deployments? If so, how?]
