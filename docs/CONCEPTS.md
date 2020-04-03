# API Concepts


## Abilities
"Abilities" describes your account's capabilities by feature name. For example `"teams"`.


An ability may be available to your account based on things like your pricing plan or account state.

## Add-ons

Developers can write their own functionality to insert into PagerDuty's UI.

## Business Services

Business Services model capabilities that span multiple technical Services and that may be owned by several different teams.


Mapping technical Services to business Services gives responders context on an Incident’s impact to the business. 


[*Read more about business Services in the PagerDuty Knowledge Base*](https://support.pagerduty.com/docs/business-Services).

## Escalation Policies

An Escalation Policy determines what [User](#Users) or [Schedule](#Schedules) will be [Notified](#Notifications) and in what order. This will happen when an [Incident](#Incidents) is triggered.


Escalation policies can be used by one or more [Services](#Services).


#### Escalation Rules

An Escalation Policy is made up of multiple Escalation Rules. Each Escalation Rule represents a level of [On-Call](#On-Calls) duty.


It specifies one or more [Users](#Users) or [Schedules](#Schedules) to be notified when an unacknowledged [Incident](#Incidents) reaches that Escalation Rule.


The first Escalation Rule in the Escalation Policy is the [User](#Users) that will be [notified](#Notifications) about the triggered [Incident](#Incidents).


If all [On-Call](#On-Calls) [User](#Users) for a given Escalation Rule have been acknowledged of an [Incident](#Incidents) and the Escalation Rule's escalation delay has elapsed, the [Incident](#Incidents) escalates to the next Escalation Rule.


[*Read more about Escalation Policies in the PagerDuty Knowledge Base*](https://support.pagerduty.com/hc/en-us/articles/202828950-What-is-an-Escalation-Policy-).


## Extensions
A PagerDuty Extension represents an instance of an [Extension Schema](#Extension-Schema) on a object that an Extension can be attached to, such as a Service.


An example of an Extension would be a Generic Webhook endpoint, or the Slack Extension.

## Extension Schema
An Extension Schema represents a specific type of outbound extension such as Generic Webhook, Slack, ServiceNow.


Extension Schemas will contain template configuration information that is required to instantiate an instance of the Extension Schema as an Extension.


If an Extension Schema already has a preconfigured url, the Extension will not have to configure one.


In addition, if the Extension Schema has a config object, the Extension will need to provide config values based on what the Extension Schema indicates are required for the config.


Some Extension Schemas that require OAuth Authorization to be setup, such as the Slack Extension, cannot be configured through the API.

## Incidents
An Incident represents a problem or an issue that needs to be addressed and resolved.


Incidents can be thought of as a problem or an issue within your [Service](#Services) that needs to be addressed and resolved, they are normalized and de-duplicated.


Incidents can be `triggered`, `acknowledged`, or `resolved`, and are assigned to a [User](#User) based on the [Service](#Services)'s [Escalation Policy](#Escalation-Policies).


A triggered Incident prompts a [Notification](#Notifications) to be sent to the current [On-Call](#On-Calls) [User(s)](#Users) as defined in the [Escalation Poicy](#Escalation-Policy) used by the [Service](#Services).


Incidents are triggered through the [Events API](https://v2.developer.pagerduty.com/docs/events-api) or are created by Integrations.


[*Read more about Incidents in the PagerDuty Knowledge Base*](https://support.pagerduty.com/hc/en-us/articles/202829250-What-Is-an-Incident-).

### Responder Requests
Responder Requests are a request for a specific [User](#User) to respond to the Incident.

### Notes
Notes are appended to Incidents to add context for responders.

### Status Updates
Status Updates are a updates for stakeholders who are not responding to incidents.

### Snooze
Snoozing an Incident will re-trigger it after a specified amount of time.


### Alerts
An Alert is sent to a [User](#User) to have them respond to an Incident. Alerts will follow a User's notification policies.

## Log Entries
Updates to an Incident generate [Log Entries](#Log_Entries) that capture the changes to an Incident over time, whether these changes were prompted by a [User](#Users), an [Integration](#Integrations), or were performed automatically.


Log entries give you more insight into how your [team](#Teams) or organization is handling your [Incidents](#Incidents).


Log entry data includes details about the event(s) that affected the [Incident](#Incidents) throughout its lifecycle, such as:

- The data contained in events sent by the [Integration.](#Integrations)
- Which [Users](#Users) were [notified](#Notifications) and at what time.
- How a User was [notified](#Notifications)
- What [User(s)](#Users) acknowledged or resolved the [Incident](#Incidents)
- Any automatic actions that occurred to the [Incident](#Incidents)
- Any other manual [User](#Users) actions, such as a reassignment or a note


Log entries cannot be created directly through the API; they are a result of other actions. The API provides read-only access to the Log Entries generated by PagerDuty.


## Maintenance Windows
A Maintenance Window is used to temporarily disable one or more [Services](#Services) for a set period of time.


No [Incidents](#Incidents) will be triggered and no [Notifications](#Notifications) will be received while a [Service](#Services) is disabled by a Maintenance Window.


Maintenance windows are specified to start at a certain time and end after they have begun. Once started, a Maintenance Window cannot be deleted; it can only be ended immediately to re-enable the [Service](#Services).


[*Read more about Maintenance Windows in the PagerDuty Knowledge Base*](https://support.pagerduty.com/hc/en-us/articles/202830350-Putting-a-Service-in-maintenance-mode).

## Notifications
A Notification is created when an [Incident](#Incident) is triggered or escalated and an [Alert](#Alert) is sent to a [User.](#User)


Notifications are messages containing the details of the [Incident](#Incidents), and can be through SMS, email, phone calls, and push notifications.


Notifications cannot be created directly through the API; they are a result of other actions. The API provides read-only access to the Notifications generated by PagerDuty.


[*Read more about Notifications in the PagerDuty Knowledge Base*](https://support.pagerduty.com/hc/en-us/articles/202828840-What-is-an-Alert-Notification-).

## On-Calls
An On-Call represents a contiguous unit of time for which a [User](#Users) will be On-Call for a given [Escalation Policy](#Escalation-Policies) and [Escalation Rule](#Escalation-Rules).


This may be the result of that [User](#Users) always being On-Call for the [Escalation Rule](#Escalation-Policies), or a block of time during which the computed result of a [Schedule](#Schedules) on that [Escalation Rule](#Escalation-Policies) puts the User On-Call.


During an On-Call, the [User](#Users) is expected to bear responsibility for responding to any [Notifications](#Notifications) they receives and working to resolve the associated [Incident(s)](#Incidents).


On-Calls cannot be created directly through the API; they are the computed result of how [Escalation Policies](#Escalation-Policies) and [Schedules](#Schedules) are configured. The API provides read-only access to the On-Calls generated by PagerDuty.

## Priorities
A Priority is a label representing the importance and impact of an incident. This feature is only available on Standard and Enterprise plans.


## Response Plays
Response Plays let you create packages of Incident Actions that can be applied to an [Incident.](#Incident)


This enables you to take a complex activity, like assembling a response team of multiple On-Calls and an Incident commander, and make it available to anyone that needs to use it.

## Schedules
A Schedule determines the time periods that [Users](#Users) are [On-Call.](#On-Calls)

Only [On-Call](#On-Calls) [Users](#Users) are eligible to receive [Notifications](#Notifications) from [Incidents](#Incidents).


The details of the On-Call Schedule specify which single [User](#Users) is [On-Call](#On-Calls) for that Schedule at any given point in time.


An On-Call Schedule consists of one or more [Schedule Layers](https://support.pagerduty.com/hc/en-us/articles/202830250-Scheduling-Layers) that rotate a group of [Users](#Users) through the same shift at a set interval.


Schedules are used by [Escalation Policies](#Escalation-Policies) as an escalation target for a given [Escalation Rule](#Escalation-Rules).


[*Read more about On-Call Schedules in the PagerDuty Knowledge Base*](https://support.pagerduty.com/hc/en-us/sections/200550790-On-Call-Schedules).

## Services
A Service represents an entity you monitor (such as a web Service, email Service, or database Service.)


It is a container for related [Incidents](#Incidents) that associates them with [Escalation Policies](#Escalation-Policies).


A Service is the focal point for [Incident](#Incidents) management; Services specify the configuration for the behavior of [Incidents](#Incidents) triggered on them.


This behavior includes specifying urgency and performing automated actions based on time of day, [Incident](#Incidents) duration, and other factors.

[*Read more about Services in the PagerDuty Knowledge Base*](https://support.pagerduty.com/hc/en-us/sections/200550800-Services).

#### Integrations
An Integration is an endpoint (like Nagios, email, or an API call) that generates events, which are normalized and de-duplicated by PagerDuty to create [Incidents](#Incidents).


Integrations feed events into Services and provide event management functionality such as filtering and de-duplication.

## Tags
A Tag can be assigned to Escalation Policy, Team or User, and searches for those objects can be filtered to retrieve those with specific tags.

## Teams
A Team is a collection of [Users](#Users) and [Escalation Policies](#Escalation-Policies) that represent a group of people
within an organization.


Teams can be used throughout the API and PagerDuty applications to filter information to only what is relevant for one or more teams.


The account must have the Teams ability to use the following endpoints.


[*Read more about Teams in the PagerDuty Knowledge Base*](https://support.pagerduty.com/hc/en-us/articles/204072090-How-to-Create-Teams-in-PagerDuty-).

## Users
Users are members of an Account that have the ability to interact with [Incidents](#Incidents) and other data on the account.


Users are fundamental agents of different types of actions in PagerDuty. A User can, among other things:

- Acknowlege, reassign, snooze, escalate, and resolve [Incidents.](#Incidents)
- Configure [Services](#Services), [Escalation Policies](#Escalation-Policies), [Integrations](#Integrations), [On-Call Schedules](#Schedules), [Teams](#Teams), and more.
- Go [On-Call](#On-Calls) for one or more [Schedules](#Schedules) or [Escalation Policies.](#Escalation-Policies)
- Get [Alerted](#Alerts) and receive [Notifications.](#Notifications)


Depending on a User's role, they may have access to different parts of the account's data.


[*Read more about Users in the PagerDuty Knowledge Base*](https://support.pagerduty.com/hc/en-us/sections/200550780-Users).

## Vendors
A Vendor represents a specific type of [Integration](#Integration). AWS Cloudwatch, Skacj, Datadog, are all examples of Vendors that can be integrated into PagerDuty by making an [Integration](#!/Services/get_Services_id_Integrations_Integration_id).


Vendor Integrations (when compared to generic email and API Integrations) are automatically configured with the right API or email filtering settings for inbound events from that Vendor. Some Vendors also have associated [Integration Guides](https://support.pagerduty.com/docs/aws-cloudwatch-integration-guide) on the PagerDuty support site.
