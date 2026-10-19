---

copyright:
  years: 2026
lastupdated: "2026-10-19"

keywords: manage paver data, paver data retention, export paver data, delete paver data, paver data residency, paver responsibilities

subcollection: paver

---

{{site.data.keyword.attribute-definition-list}}

# Managing your {{site.data.keyword.paver}} data in {{site.data.keyword.cloud_notm}}
{: #paver-managing-data}

Learn how to manage your {{site.data.keyword.paver_full}} data in {{site.data.keyword.cloud}}, including data retention, export, and deletion processes.
{: shortdesc}

{{site.data.keyword.paver}} stores information that helps personalize your experience, maintain conversation history, and provide context-aware assistance across your {{site.data.keyword.cloud}} environment. Learn what data is stored, how it is retained, how to export or delete it, and the responsibilities of {{site.data.keyword.IBM_notm}} and customers for data management and resiliency.

## Data storage and retention
{: #paver-data-storage-retention}

{{site.data.keyword.paver}} stores user-specific information to support conversations, memories, and personalized interactions.

The data that {{site.data.keyword.paver}} stores for each user includes:

- Conversation history
- Memories
- Skills
- Files

All stored data (conversations, memories, skills, and files) is subject to a 90-day retention period from the date of last access. Data that has not been accessed within 90 days is automatically deleted. Users can delete their stored {{site.data.keyword.paver}} data at any time.

## Exporting your data
{: #paver-exporting-data}

{{site.data.keyword.paver}} provides capabilities that allow users to export their personal {{site.data.keyword.paver}} data.

Users can export their conversation history and memories, and download their files. Exports and downloads are performed at the individual user level. A full export of all content across an account is not supported.

If you have compliance requirements that mandate retaining data beyond the 90-day retention period, export your conversations and store them in your own external record-keeping system before the 90-day window elapses.

To export your data, you can use the following commands:

```sh
paver files download <name> [local-path]
```
{: codeblock}

```sh
paver memory export
```
{: codeblock}

```sh
paver conversation export <id>
```
{: codeblock}


## Deleting your data
{: #paver-deleting-data}

Users can permanently delete their conversation history, memories, skills, and files.

To delete your all of your data, you can use the `paver user delete-data` command. Alternatively, you can individually delete different types of data by using the following commands:

Delete all files in the sandbox workspace:

```sh
paver files clear
```
{: codeblock}


Delete all memories:

```sh
paver memory clear
```
{: codeblock}

Remove a user skill:

```sh
paver skills remove <skill-name>
```
{: codeblock}

Delete all conversations:

```sh
paver conversation clear
```
{: codeblock}

Alternatively, you can delete individual conversations by ID by using `paver conversation remove <id>`.


## Data residency
{: #paver-data-residency}

All {{site.data.keyword.paver}} data, including conversation history, memories, skills, and files, is stored and processed exclusively in the {{site.data.keyword.cloud_notm}} region in which {{site.data.keyword.paver}} is hosted for your account. If a region becomes unavailable, data stored in that region is not accessible from another region.

The only exception is AI inferencing, which is currently performed in the `us-east`, regardless of the region where {{site.data.keyword.paver}} is hosted. To generate a response, {{site.data.keyword.paver}} sends prompts and related content to an IBM AI model inferencing service in the `us-east` region. The inferencing service does not retain prompts or responses. Support for AI inferencing in additional {{site.data.keyword.cloud_notm}} regions is planned, so that inferencing can co-reside with the region in which your data is stored.
