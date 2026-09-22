---

copyright:
  years:  2021, 2026
lastupdated: "2026-09-22"

keywords:

subcollection: atracker

---

{{site.data.keyword.attribute-definition-list}}



# Auditing events for {{site.data.keyword.dashdblong_notm}}
{: #at_events_dashdb}

{{site.data.keyword.cloud}} services, such as {{site.data.keyword.dashdblong}}, generate activity tracking events.
{: shortdesc}

Activity tracking events report on activities that change the state of a service in {{site.data.keyword.cloud_notm}}. You can use the events to investigate abnormal activity and critical actions and to comply with regulatory audit requirements.

You can use {{site.data.keyword.atracker_full_notm}}, a platform service, to route auditing events in your account to destinations of your choice by configuring targets and routes that define where activity tracking events are sent. For more information, see [About {{site.data.keyword.atracker_full_notm}}](/docs/atracker?topic=atracker-about).

You can use {{site.data.keyword.logs_full_notm}} to visualize and alert on events that are generated in your account and routed by {{site.data.keyword.atracker_full_notm}} to an {{site.data.keyword.logs_full_notm}} instance.

<mezmo>

As a security officer, auditor, or manager, you can use the {{site.data.keyword.at_full_notm}} service to track how users and applications interact with the {{site.data.keyword.dashdblong}} service in {{site.data.keyword.cloud_notm}}.
{: shortdesc}

You can provision an instance of {{site.data.keyword.dashdblong}} through the [{{site.data.keyword.cloud_notm}} catalog](https://cloud.ibm.com/db2-wh){: external}. [Learn more](/docs/account?topic=account-iamoverview).


The {{site.data.keyword.at_full_notm}} service records user-initiated activities that change the state of a service in {{site.data.keyword.cloud_notm}}. To get started monitoring your user's actions, see [{{site.data.keyword.at_full_notm}}](/docs/activity-tracker?topic=activity-tracker-getting-started). An initiator can be a user, a service, or an application.

</mezmo>

## Viewing activity tracking events for {{site.data.keyword.dashdblong_notm}}
{: #at-viewing-dashdb}

You can use {{site.data.keyword.logs_full_notm}} to visualize and alert on events that are generated in your account and routed by {{site.data.keyword.atracker_full_notm}} to an {{site.data.keyword.logs_full_notm}} instance.

### Launching {{site.data.keyword.logs_full_notm}} from the Observability page
{: #log-launch-standalone-dashdb}

For information on launching the {{site.data.keyword.logs_full_notm}} UI, see [Launching the UI in the {{site.data.keyword.logs_full_notm}} documentation.](/docs/cloud-logs?topic=cloud-logs-instance-launch)

## Platform events
{: #at_events_dashdb_platform}

The following table lists the actions that generate an event:

| Action                                   | Description |
|------------------------------------------|---------|
| `dashdb.instance.create`           | An event is generated when you provision a service instance. |
| `dashdb.instance.update`           | An event is generated when you rename a service instance or when you change the service plan. |
| `dashdb.instance.delete`           | An event is generated when a service instance is deleted. |
| `dashdb.instance.schedule_reclaim` | An event is generated when a service instance is pending_reclamation. |
| `dashdb.instance.restore`          | An event is generated when a service instance is restored. |
{: caption="Actions that generate platform events" caption-side="top"}

The following table lists the actions that generate an event for managing service credentials that are associated to a service instance:

| Action                         | Description |
|--------------------------------|---------|
| `service_name.key.create` | An event is generated when an API key is created for a service instance through the *Service credentials* section of the service instance UI. |
| `service_name.key.delete` | An event is generated when an API key that is associated with a service instance is deleted from the *Service credentials* section of the service instance UI. |
{: caption="Actions that generate service credentials events" caption-side="top"}

<mezmo>

## Viewing events
{: #at_events_dashdb_ui}

Events are available in the **Frankfurt (eu-de)** region.

To view these events, you must [provision an instance](/docs/activity-tracker?topic=activity-tracker-provision#provision) of the {{site.data.keyword.at_full_notm}} service in the **Frankfurt (eu-de)** region. Then, you must [open the {{site.data.keyword.at_full_notm}} UI](/docs/activity-tracker?topic=activity-tracker-launch).
