# API Concepts


## Abilities
"Abilities" describes your account's capabilities by feature name. For example `"teams"`.


An ability may be available to your account based on things like your pricing plan or account state.

## Add-ons

Developers can write their own functionality to insert into PagerDuty's UI.

## Business Services

Business Services model capabilities that span multiple technical Services and that may be owned by several different teams.


Mapping technical Services to business Services gives responders context on an Incident’s impact to the business. 


[*Read more about business Services in the PagerDuty Knowledge Base*](https://support.pagerduty.com/docs/business-services).

## Escalation Policies

An Escalation Policy determines what [User](#users) or [Schedule](#schedules) will be [Notified](#notifications) and in what order. This will happen when an [Incident](#incidents) is triggered.


Escalation Policies can be used by one or more [Services](#services).


#### Escalation Rules

An Escalation Policy is made up of multiple Escalation Rules. Each Escalation Rule represents a level of [On-Call](#on-calls) duty.


It specifies one or more [Users](#users) or [Schedules](#schedules) to be notified when an unacknowledged [Incident](#incidents) reaches that Escalation Rule.


The first Escalation Rule in the Escalation Policy is the [User](#users) that will be [notified](#notifications) about the triggered [Incident](#incidents).


If all [On-Call](#on-calls) [User](#users) for a given Escalation Rule have been acknowledged of an [Incident](#incidents) and the Escalation Rule's escalation delay has elapsed, the [Incident](#incidents) escalates to the next Escalation Rule.


[*Read more about Escalation Policies in the PagerDuty Knowledge Base*](https://support.pagerduty.com/hc/en-us/articles/202828950-What-is-an-escalation-policy-).


## Extensions
A PagerDuty Extension represents an instance of an [Extension Schema](#extension-schema) on a object that an Extension can be attached to, such as a Service.


An example of an Extension would be a Generic Webhook endpoint, or the Slack Extension.

## Extension Schema
An Extension Schema represents a specific type of outbound extension such as Generic Webhook, Slack, ServiceNow.


Extension Schemas will contain template configuration information that is required to instantiate an instance of the Extension Schema as an Extension.


If an Extension Schema already has a preconfigured url, the Extension will not have to configure one.


In addition, if the Extension Schema has a config object, the Extension will need to provide config values based on what the Extension Schema indicates are required for the config.


Some Extension Schemas that require OAuth Authorization to be setup, such as the Slack Extension, cannot be configured through the API.

## Incidents
An Incident represents a problem or an issue that needs to be addressed and resolved.


Incidents can be thought of as a problem or an issue within your [Service](#services) that needs to be addressed and resolved, they are normalized and de-duplicated.


Incidents can be `triggered`, `acknowledged`, or `resolved`, and are assigned to a [User](#user) based on the [Service](#services)'s [Escalation Policy](#escalation-policies).


A triggered Incident prompts a [Notification](#notifications) to be sent to the current [On-Call](#on-calls) [User(s)](#users) as defined in the [Escalation Poicy](#escalation-policy) used by the [Service](#services).


Incidents are triggered through the [Events API](https://developer.pagerduty.com/docs/events-api) or are created by Integrations.


[*Read more about Incidents in the PagerDuty Knowledge Base*](https://support.pagerduty.com/hc/en-us/articles/202829250-What-Is-an-Incident-).

### Responder Requests
Responder Requests are a request for a specific [User](#user) to respond to the Incident.

### Notes
Notes are appended to Incidents to add context for responders.

### Status Updates
Status Updates are a updates for stakeholders who are not responding to incidents.

### Snooze
Snoozing an Incident will re-trigger it after a specified amount of time.


### Alerts
An Alert is sent to a [User](#user) to have them respond to an Incident. Alerts will follow a User's notification policies.

## Log Entries
Updates to an Incident generate [Log Entries](#log_Entries) that capture the changes to an Incident over time, whether these changes were prompted by a [User](#users), an [Integration](#integrations), or were performed automatically.


Log entries give you more insight into how your [team](#teams) or organization is handling your [Incidents](#incidents).


Log entry data includes details about the event(s) that affected the [Incident](#incidents) throughout its lifecycle, such as:

- The data contained in events sent by the [Integration.](#integrations)
- Which [Users](#users) were [notified](#notifications) and at what time.
- How a User was [notified](#notifications)
- What [User(s)](#users) acknowledged or resolved the [Incident](#incidents)
- Any automatic actions that occurred to the [Incident](#incidents)
- Any other manual [User](#users) actions, such as a reassignment or a note


Log entries cannot be created directly through the API; they are a result of other actions. The API provides read-only access to the Log Entries generated by PagerDuty.


## Maintenance Windows
A Maintenance Window is used to temporarily disable one or more [Services](#services) for a set period of time.


No [Incidents](#incidents) will be triggered and no [Notifications](#notifications) will be received while a [Service](#services) is disabled by a Maintenance Window.


Maintenance windows are specified to start at a certain time and end after they have begun. Once started, a Maintenance Window cannot be deleted; it can only be ended immediately to re-enable the [Service](#services).


[*Read more about Maintenance Windows in the PagerDuty Knowledge Base*](https://support.pagerduty.com/hc/en-us/articles/202830350-Putting-a-service-in-maintenance-mode).

## Notifications
A Notification is created when an [Incident](#incident) is triggered or escalated and an [Alert](#alert) is sent to a [User.](#user)


Notifications are messages containing the details of the [Incident](#incidents), and can be through SMS, email, phone calls, and push notifications.


Notifications cannot be created directly through the API; they are a result of other actions. The API provides read-only access to the Notifications generated by PagerDuty.


[*Read more about Notifications in the PagerDuty Knowledge Base*](https://support.pagerduty.com/hc/en-us/articles/202828840-What-is-an-alert-notification-).

## On-Calls
An On-Call represents a contiguous unit of time for which a [User](#users) will be On-Call for a given [Escalation Policy](#escalation-policies) and [Escalation Rule](#escalation-rules).


This may be the result of that [User](#users) always being On-Call for the [Escalation Rule](#escalation-policies), or a block of time during which the computed result of a [Schedule](#schedules) on that [Escalation Rule](#escalation-policies) puts the User On-Call.


During an On-Call, the [User](#users) is expected to bear responsibility for responding to any [Notifications](#notifications) they receives and working to resolve the associated [Incident(s)](#incidents).


On-Calls cannot be created directly through the API; they are the computed result of how [Escalation Policies](#escalation-policies) and [Schedules](#schedules) are configured. The API provides read-only access to the On-Calls generated by PagerDuty.

## Priorities
A Priority is a label representing the importance and impact of an incident. This feature is only available on Standard and Enterprise plans.


## Response Plays
Response Plays let you create packages of Incident Actions that can be applied to an [Incident.](#incident)


This enables you to take a complex activity, like assembling a response team of multiple On-Calls and an Incident commander, and make it available to anyone that needs to use it.

## Rulesets
Rulesets allow you to route events to an endpoint and create collections of event rules, which define sets of actions to take based on event content.

[*Read more about rulesets in the PagerDuty Knowledge Base*](https://support.pagerduty.com/docs/rulesets).

## Schedules
A Schedule determines the time periods that [Users](#users) are [On-Call.](#on-calls)

Only [On-Call](#on-calls) [Users](#users) are eligible to receive [Notifications](#notifications) from [Incidents](#incidents).


The details of the On-Call Schedule specify which single [User](#users) is [On-Call](#on-calls) for that Schedule at any given point in time.


An On-Call Schedule consists of one or more [Schedule Layers](https://support.pagerduty.com/hc/en-us/articles/202830250-Scheduling-Layers) that rotate a group of [Users](#users) through the same shift at a set interval.


Schedules are used by [Escalation Policies](#escalation-policies) as an escalation target for a given [Escalation Rule](#escalation-rules).


[*Read more about On-Call Schedules in the PagerDuty Knowledge Base*](https://support.pagerduty.com/hc/en-us/sections/200550790-On-Call-Schedules).

## Services
A Service represents an entity you monitor (such as a web Service, email Service, or database Service.)


It is a container for related [Incidents](#incidents) that associates them with [Escalation Policies](#escalation-policies).


A Service is the focal point for [Incident](#incidents) management; Services specify the configuration for the behavior of [Incidents](#incidents) triggered on them.


This behavior includes specifying urgency and performing automated actions based on time of day, [Incident](#incidents) duration, and other factors.

[*Read more about Services in the PagerDuty Knowledge Base*](https://support.pagerduty.com/hc/en-us/sections/200550800-Services).

#### Integrations
An Integration is an endpoint (like Nagios, email, or an API call) that generates events, which are normalized and de-duplicated by PagerDuty to create [Incidents](#incidents).


Integrations feed events into Services and provide event management functionality such as filtering and de-duplication.

## Tags
A Tag can be assigned to Escalation Policy, Team or User, and searches for those objects can be filtered to retrieve those with specific tags.

## Teams
A Team is a collection of [Users](#users) and [Escalation Policies](#escalation-policies) that represent a group of people
within an organization.


Teams can be used throughout the API and PagerDuty applications to filter information to only what is relevant for one or more teams.


The account must have the Teams ability to use the following endpoints.


[*Read more about Teams in the PagerDuty Knowledge Base*](https://support.pagerduty.com/hc/en-us/articles/204072090-How-to-Create-Teams-in-PagerDuty-).

## Users
Users are members of an Account that have the ability to interact with [Incidents](#incidents) and other data on the account.


Users are fundamental agents of different types of actions in PagerDuty. A User can, among other things:

- Acknowlege, reassign, snooze, escalate, and resolve [Incidents.](#incidents)
- Configure [Services](#services), [Escalation Policies](#escalation-policies), [Integrations](#integrations), [On-Call Schedules](#schedules), [Teams](#teams), and more.
- Go [On-Call](#on-calls) for one or more [Schedules](#schedules) or [Escalation Policies.](#escalation-policies)
- Get [Alerted](#alerts) and receive [Notifications.](#notifications)


Depending on a User's role, they may have access to different parts of the account's data.


[*Read more about Users in the PagerDuty Knowledge Base*](https://support.pagerduty.com/hc/en-us/sections/200550780-Users).

## Vendors
A Vendor represents a specific type of [Integration](#integration). AWS Cloudwatch, Skacj, Datadog, are all examples of Vendors that can be integrated into PagerDuty by making an [Integration](#!/Services/get_Services_id_Integrations_Integration_id).


Vendor Integrations (when compared to generic email and API Integrations) are automatically configured with the right API or email filtering settings for inbound events from that Vendor. Some Vendors also have associated [Integration Guides](https://support.pagerduty.com/docs/aws-cloudwatch-integration-guide) on the PagerDuty support site.
