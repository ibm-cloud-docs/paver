---

copyright:
  years: 2026
lastupdated: "2026-10-12"

keywords: paver responsibilities, customer responsibilities with paver

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
| Instance provisioning and data residency | Make Paver available in supported {{site.data.keyword.cloud_notm}} regions and store user data in the region where the instance is created. | Provision Paver instances in the region where you require data to be stored to meet your [data residency](/docs/paver?topic=paver-paver-managing-data#paver-data-residency) requirements. |
| Data retention lifecycle | Maintain the retention lifecycle for Paver-managed data. Inactive user data is automatically deleted after approximately 90 days. | Export any data that you want to preserve outside of Paver before the retention period expires. |
{: row-headers}
{: caption="Responsibilities for change management" caption-side="bottom"}
{: summary="The rows are read from left to right. The first column describes the task. The second column describes {{site.data.keyword.IBM_notm}} responsibilities for that task. The third column describes your responsibilities as the customer for that task."}

## Identity and access management
{: #paver-iam-responsibilities}

Identity and access management includes tasks such as authentication, authorization, access control policies, and approving, granting, and revoking access.

|  | {{site.data.keyword.IBM_notm}} responsibilities | Your responsibilities |
|--|--|--|
| Access policies and permissions | Enforce {{site.data.keyword.cloud_notm}} IAM policies. Ensure that Paver operates only with the permissions of the authenticated user. | Follow IAM least privilege principles when assigning access policies. Ensure that users have only the permissions required for their tasks. |
| User actions and data access | Restrict operations to the permissions of the authenticated user. | Take responsibility for all actions taken, data that is accessed, and changes made through Paver under your credentials. |
| Risk evaluation and safeguards | Provide risk warnings for proposed actions and provide safety mode, where Safe mode prevents Paver from modifying resources. | Review Paver's warnings about risky actions, make appropriate judgments before approving changes, and use Safe mode in [Safety mode](/docs/paver?topic=paver-paver-security-guide#paver-security-safe-edit-mode) when working with sensitive resources or accounts. |
{: row-headers}
{: caption="Responsibilities for identity and access management" caption-side="bottom"}
{: summary="The rows are read from left to right. The first column describes the task. The second column describes {{site.data.keyword.IBM_notm}} responsibilities for that task. The third column describes your responsibilities as the customer for that task."}

## Security and regulation compliance
{: #paver-security-compliance}

Security and regulation compliance includes tasks such as security controls implementation and compliance certification.

|  | {{site.data.keyword.IBM_notm}} responsibilities | Your responsibilities |
|--|--|--|
| Sensitive data handling | Encrypt stored data at rest and in transit. Paver does not request personally identifiable information (PII) or sensitive personal information (SPI). | Take responsibility for any PII or SPI that you submit through Paver. Understand that any sensitive data that you provide or use Paver to handle is stored in conversation history and files, and you must manage or [delete your data](/docs/paver?topic=paver-paver-managing-data#paver-deleting-data) to comply with your organization's regulatory standards. |
| Data export and deletion | Provide capabilities to export and delete user data. | Export or delete your stored Paver data as needed to meet your compliance requirements. |
{: row-headers}
{: caption="Responsibilities for security and regulation compliance" caption-side="bottom"}
{: summary="The rows are read from left to right. The first column describes the task. The second column describes {{site.data.keyword.IBM_notm}} responsibilities for that task. The third column describes your responsibilities as the customer for that task."}

## Disaster recovery
{: #paver-disaster-recovery}

Disaster recovery includes tasks such as providing dependencies on disaster recovery sites, provision disaster recovery environments, data and configuration backup, replicating data and configuration to the disaster recovery environment, and fail over on disaster events.

|  | {{site.data.keyword.IBM_notm}} responsibilities | Your responsibilities |
|--|--|--|
| Regional deployments | Provide Paver as a regional service. | No action required. |
{: row-headers}
{: caption="Responsibilities for disaster recovery" caption-side="bottom"}
{: summary="The rows are read from left to right. The first column describes the task. The second column describes {{site.data.keyword.IBM_notm}} responsibilities for that task. The third column describes your responsibilities as the customer for that task."}
