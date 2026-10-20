---

copyright:
  years: 2026
lastupdated: "2026-10-20"

keywords: paver activity tracking, paver activity tracker events, paver audit events, paver at events

subcollection: paver

---

{{site.data.keyword.attribute-definition-list}}

# Activity tracking events for {{site.data.keyword.paver_full_notm}}
{: #at_events}

{{site.data.keyword.cloud_notm}} services, such as {{site.data.keyword.paver_full}}, generate activity tracking events.
{: shortdesc}

Activity tracking events report on activities that change the state of a service in {{site.data.keyword.cloud_notm}}. You can use the events to investigate abnormal activity and critical actions and to comply with regulatory audit requirements.

You can use {{site.data.keyword.atracker_full_notm}}, a platform service, to route auditing events in your account to destinations of your choice by configuring targets and routes that define where activity tracking events are sent. For more information, see [About {{site.data.keyword.atracker_full_notm}}](/docs/atracker?topic=atracker-about).

You can use {{site.data.keyword.logs_full_notm}} to visualize and alert on events that are generated in your account and routed by {{site.data.keyword.atracker_full_notm}} to an {{site.data.keyword.logs_full_notm}} instance.

## Locations where activity tracking events are generated
{: #at-locations}

{{site.data.keyword.paver}} sends activity tracking events by {{site.data.keyword.atracker_full_notm}} in the regions that are indicated in the following tables.

| Dallas (`us-south`) | Washington (`us-east`) | Toronto (`ca-tor`) | Montreal (`ca-mon`) | Sao Paulo (`br-sao`) |
|---------------------|------------------------|--------------------|---------------------|----------------------|
| NO | No | No | No | No |
{: caption="Regions where activity tracking events are sent in Americas locations" caption-side="top"}
{: #atracker-table-1}
{: tab-title="Americas"}
{: tab-group="atracker"}
{: class="simple-tab-table"}

| Tokyo (`jp-tok`) | Sydney (`au-syd`) | Osaka (`jp-osa`) | Chennai (`in-che`) |
|------------------|-------------------|------------------|--------------------|
| No | No | No | No |
{: caption="Regions where activity tracking events are sent in Asia Pacific locations" caption-side="top"}
{: #atracker-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="atracker"}
{: class="simple-tab-table"}

| Frankfurt (`eu-de`) | London (`eu-gb`) | Madrid (`eu-es`) |
|---------------------|------------------|------------------|
| Yes | No | No |
{: caption="Regions where activity tracking events are sent in Europe locations" caption-side="top"}
{: #atracker-table-3}
{: tab-title="Europe"}
{: tab-group="atracker"}
{: class="simple-tab-table"}

## How events reach your account
{: #at-event-delivery}

[VERIFY: Describe how {{site.data.keyword.paver}} events reach the customer's account, and whether the customer must configure anything for events to be generated. Confirm each delivery level in the following list.]

Instance level
:   [VERIFY: Describe how events are delivered to an {{site.data.keyword.atracker_short}} instance, and under what conditions.]

Enterprise instance level
:   [VERIFY: Describe how events are delivered to an enterprise instance, and under what conditions.]

Account level
:   [VERIFY: Describe how events are delivered at the account level, and under what conditions.]

## Viewing activity tracking events for {{site.data.keyword.paver}}
{: #at-viewing}

You can use {{site.data.keyword.logs_full_notm}} to visualize and alert on events that are generated in your account and routed by {{site.data.keyword.atracker_full_notm}} to an {{site.data.keyword.logs_full_notm}} instance.

### Launching {{site.data.keyword.logs_full_notm}} from the Observability page
{: #log-launch-standalone}

For information about launching the {{site.data.keyword.logs_full_notm}} UI, see [Launching the UI](/docs/cloud-logs?topic=cloud-logs-instance-launch) in the {{site.data.keyword.logs_full_notm}} documentation.

## List of management events
{: #at_actions}

The following table lists the actions that {{site.data.keyword.paver}} sends to {{site.data.keyword.atracker_short}} and that generate management events.

| Action | Description |
|--------|-------------|
| `[VERIFY: action name]` | [VERIFY: An event is generated when ...] |
{: caption="Actions that generate management events" caption-side="bottom"}

## Actions that don't generate events
{: #at-no-events}

[VERIFY: List the actions that deliberately generate no activity tracking events, and explain why. Replace the placeholder row.]

| Action | Reason that no event is generated |
|--------|-----------------------------------|
| [VERIFY: action] | [VERIFY: reason] |
{: caption="Actions that don't generate events" caption-side="bottom"}

Because {{site.data.keyword.paver}} acts with the credentials of the authenticated user, actions that {{site.data.keyword.paver}} takes against other {{site.data.keyword.cloud_notm}} services are recorded by those services as actions of that user. For more information, see [Logging and conversation history](/docs/paver?topic=paver-paver-security-guide#paver-security-logging-history).

## Analyzing {{site.data.keyword.paver}} activity tracking events
{: #at_events_analyze}

For information about the fields that are common to all activity tracking events, see [Event fields](/docs/atracker?topic=atracker-event).

### Request data
{: #at-request-data}

[VERIFY: Describe the information that {{site.data.keyword.paver}} events add to the `requestData` field, and list the fields and their meanings. Replace the placeholder row.]

| Field | Description |
|-------|-------------|
| `[VERIFY: field]` | [VERIFY: description] |
{: caption="Request data fields in Paver events" caption-side="bottom"}

### Severity
{: #at-severity}

[VERIFY: Describe the rules that determine the severity of each {{site.data.keyword.paver}} event, such as normal, warning, or critical. Replace the placeholder row.]

| Severity | When it is assigned |
|----------|---------------------|
| `[VERIFY: severity]` | [VERIFY: rule] |
{: caption="Severity rules for Paver events" caption-side="bottom"}
