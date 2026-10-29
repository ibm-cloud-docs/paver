---

copyright:
  years: 2026
lastupdated: "2026-10-27"

keywords: paver responsibilities, customer responsibilities with paver

subcollection: paver

---

{{site.data.keyword.attribute-definition-list}}

# Understanding your responsibilities when using {{site.data.keyword.paver_full_notm}} in {{site.data.keyword.cloud_notm}}
{: #paver-responsibilities}

Learn about the management responsibilities and terms and conditions that you have when you use {{site.data.keyword.paver_full}}. For a high-level view of the service types in {{site.data.keyword.cloud}} and the breakdown of responsibilities between the customer and {{site.data.keyword.IBM_notm}} for each type, see [Shared responsibilities for {{site.data.keyword.cloud_notm}} offerings](/docs/overview?topic=overview-shared-responsibilities).
{: shortdesc}

Review the following sections for the specific responsibilities for you and for {{site.data.keyword.IBM_notm}} when you use {{site.data.keyword.paver}}. For the overall terms of use, see [{{site.data.keyword.cloud}} Terms and Notices](/docs/overview?topic=overview-terms).

## Incident and operations management
{: #paver-incident-and-ops}

Incident and operations management includes tasks such as monitoring, event management, high availability, problem determination, recovery, and full state backup and recovery.

|  | {{site.data.keyword.IBM_notm}} responsibilities | Your responsibilities |
|--|--|--|
| Service operations | Operate and maintain the {{site.data.keyword.paver}} service. | No action required. |
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
| Instance provisioning and data residency | Make {{site.data.keyword.paver}} available in supported {{site.data.keyword.cloud_notm}} regions and store user data in the region where the instance is created. | Provision {{site.data.keyword.paver}} instances in the region where you require data to be stored to meet your [data residency](/docs/paver?topic=paver-paver-managing-data#paver-data-residency) requirements. |
| Data retention lifecycle | Maintain the retention lifecycle for {{site.data.keyword.paver}}-managed data. Inactive user data is automatically deleted after approximately 90 days according to the {{site.data.keyword.paver}} for {{site.data.keyword.cloud_notm}} [data retention policy](/docs/paver?topic=paver-paver-security-guide#paver-security-data-retention). | Export any data that you want to preserve outside of {{site.data.keyword.paver}} before the retention period expires. |
{: row-headers}
{: caption="Responsibilities for change management" caption-side="bottom"}
{: summary="The rows are read from left to right. The first column describes the task. The second column describes {{site.data.keyword.IBM_notm}} responsibilities for that task. The third column describes your responsibilities as the customer for that task."}

## Identity and access management
{: #paver-iam-responsibilities}

Identity and access management includes tasks such as authentication, authorization, access control policies, and approving, granting, and revoking access.

|  | {{site.data.keyword.IBM_notm}} responsibilities | Your responsibilities |
|--|--|--|
| Access policies and permissions | Enforce {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) policies. Ensure that {{site.data.keyword.paver}} operates only with the permissions of the authenticated user. | Follow IAM least privilege principles when assigning access policies. Ensure that users have only the permissions that are required for their tasks. |
| User actions and data access | Restrict operations to the permissions of the authenticated user. | Take responsibility for all actions taken, data that is accessed, and changes made through {{site.data.keyword.paver}} under your credentials. |
| Risk evaluation and safeguards | Provide risk warnings for proposed actions and provide safety mode, where Safe mode prevents {{site.data.keyword.paver}} from modifying resources. | Review {{site.data.keyword.paver}}'s warnings about risky actions, make appropriate judgments before approving changes, and use Safe mode in [Safety mode](/docs/paver?topic=paver-paver-security-guide#paver-security-safe-edit-mode) when working with sensitive resources or accounts. |
{: row-headers}
{: caption="Responsibilities for identity and access management" caption-side="bottom"}
{: summary="The rows are read from left to right. The first column describes the task. The second column describes {{site.data.keyword.IBM_notm}} responsibilities for that task. The third column describes your responsibilities as the customer for that task."}

## Security and regulation compliance
{: #paver-security-compliance}

Security and regulation compliance includes tasks such as security controls implementation and compliance certification.

|  | {{site.data.keyword.IBM_notm}} responsibilities | Your responsibilities |
|--|--|--|
| Sensitive data handling | Encrypt stored data at rest and in transit. {{site.data.keyword.paver}} does not request personally identifiable information (PII) or sensitive personal information (SPI). | Take responsibility for any PII or SPI that you submit through {{site.data.keyword.paver}}. Understand that any sensitive data that you provide or use {{site.data.keyword.paver}} to handle is stored in conversation history and files, and you must manage or [delete your data](/docs/paver?topic=paver-paver-managing-data#paver-deleting-data) to comply with your organization's regulatory standards. |
| Data export and deletion | Provide capabilities to export and delete user data. | Export or delete your stored {{site.data.keyword.paver}} data as needed to meet your compliance requirements. |
{: row-headers}
{: caption="Responsibilities for security and regulation compliance" caption-side="bottom"}
{: summary="The rows are read from left to right. The first column describes the task. The second column describes {{site.data.keyword.IBM_notm}} responsibilities for that task. The third column describes your responsibilities as the customer for that task."}

## Disaster recovery
{: #paver-disaster-recovery}

Disaster recovery includes tasks such as providing dependencies on disaster recovery sites, provisioning disaster recovery environments, data and configuration backup, replicating data and configuration to the disaster recovery environment, and fail over on disaster events.

|  | {{site.data.keyword.IBM_notm}} responsibilities | Your responsibilities |
|--|--|--|
| Regional deployments | Provide {{site.data.keyword.paver}} as a regional service. | No action required. |
{: row-headers}
{: caption="Responsibilities for disaster recovery" caption-side="bottom"}
{: summary="The rows are read from left to right. The first column describes the task. The second column describes {{site.data.keyword.IBM_notm}} responsibilities for that task. The third column describes your responsibilities as the customer for that task."}
