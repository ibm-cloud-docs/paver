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

The data that Paver stores for each user includes:

- Conversation history
- Memories
- Skills
- Files

All stored data (conversations, memories, and files) is subject to a 90-day retention period from the date of last access. Data that has not been accessed within 90 days is automatically deleted. Users can delete their stored Paver data at any time.



## Exporting your data
{: #paver-exporting-data}

Paver provides capabilities that allow users to export their personal Paver data.

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

To delete your data, you can use the following commands:

Delete all files in the sandbox workspace:

```sh
paver files removeall
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

Alternatively, you can delete individual conversations by ID by using `paver conversation delete <id>`.


## Data residency
{: #paver-data-residency}

Paver is designed as a regional service. A user's conversation history, memories, skills, and files are stored in the {{site.data.keyword.cloud_notm}} region in which Paver is hosted for that user. If a region becomes unavailable, data stored in that region is not accessible from another region.

AI inferencing is performed in the {{site.data.keyword.cloud_notm}} `us-east` region in the United States, regardless of the region in which Paver is hosted. To generate a response, Paver sends prompts and related content to an IBM AI model inferencing service in the `us-east` region. The inferencing service does not retain prompts or responses.
