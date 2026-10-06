---

copyright:
  years: 2026
lastupdated: "2026-10-06"

keywords: paver responsibilities, IBM responsibilities, customer responsibilities, shared responsibilities, paver data management

subcollection: paver

---

{{site.data.keyword.attribute-definition-list}}

# Understanding your responsibilities when using Paver
{: #paver-responsibilities}

Learn about the management responsibilities and terms and conditions that you have when you use Paver. For a high-level view of the service types in {{site.data.keyword.cloud}} and the breakdown of responsibilities between the customer and {{site.data.keyword.IBM_notm}} for each type, see [Shared responsibilities for {{site.data.keyword.cloud_notm}} offerings](/docs/overview?topic=overview-shared-responsibilities).
{: shortdesc}

Review the following sections for the specific responsibilities for you and for {{site.data.keyword.IBM_notm}} when you use Paver. For the overall terms of use, see [{{site.data.keyword.cloud}} Terms and Notices](/docs/overview?topic=overview-terms).

## Incident and operations management
{: #paver-incident-and-ops}

Incident and operations management includes tasks such as monitoring, event management, high availability, problem determination, recovery, and full state backup and recovery.

|  | {{site.data.keyword.IBM_notm}} responsibilities | Your responsibilities |
|--|--|--|
| Service operations | Operate and maintain the Paver service. | No action required. |
| Infrastructure security | Secure the service infrastructure. | No action required. |
| Service monitoring | Manage service monitoring and operational response processes. | No action required. |
{: row-headers}
{: caption="Responsibilities for incident and operations management" caption-side="bottom"}
{: summary="The rows are read from left to right. The first column describes the task. The second column describes {{site.data.keyword.IBM_notm}} responsibilities for that task. The third column describes your responsibilities as the customer for that task."}

## Change management
{: #paver-change-management}

Change management includes tasks such as deployment, configuration, upgrades, patching, configuration changes, and deletion.

|  | {{site.data.keyword.IBM_notm}} responsibilities | Your responsibilities |
|--|--|--|
| Data retention lifecycle | Maintain the retention lifecycle for Paver-managed data. Inactive user data is automatically deleted after approximately 90 days. | Export any data you want to preserve outside of Paver before the retention period expires. |
{: row-headers}
{: caption="Responsibilities for change management" caption-side="bottom"}
{: summary="The rows are read from left to right. The first column describes the task. The second column describes {{site.data.keyword.IBM_notm}} responsibilities for that task. The third column describes your responsibilities as the customer for that task."}

## Security and regulation compliance
{: #paver-security-compliance}

Security and regulation compliance includes tasks such as security controls implementation and compliance certification.

|  | {{site.data.keyword.IBM_notm}} responsibilities | Your responsibilities |
|--|--|--|
| Data export and deletion | Provide capabilities to export and delete user data. | Export or delete your stored Paver data as needed to meet your compliance requirements. |
{: row-headers}
{: caption="Responsibilities for security and regulation compliance" caption-side="bottom"}
{: summary="The rows are read from left to right. The first column describes the task. The second column describes {{site.data.keyword.IBM_notm}} responsibilities for that task. The third column describes your responsibilities as the customer for that task."}

## Disaster recovery
{: #paver-disaster-recovery}

Disaster recovery includes tasks such as providing dependencies on disaster recovery sites, provision disaster recovery environments, data and configuration backup, replicating data and configuration to the disaster recovery environment, and failover on disaster events.

|  | {{site.data.keyword.IBM_notm}} responsibilities | Your responsibilities |
|--|--|--|
| Regional deployments | Provide Paver as a regional service. | [VERIFY: Whether customer responsibility for multi-region resiliency should be stated explicitly here. If confirmed, use:] Determine regional deployment requirements and evaluate whether multiple regional deployments are needed to meet resiliency objectives. Manage any business continuity or disaster recovery requirements that extend beyond a single-region deployment. |
{: row-headers}
{: caption="Responsibilities for disaster recovery" caption-side="bottom"}
{: summary="The rows are read from left to right. The first column describes the task. The second column describes {{site.data.keyword.IBM_notm}} responsibilities for that task. The third column describes your responsibilities as the customer for that task."}
