# Changelog

PagerDuty aims to have no breaking changes to our API, we do fix bugs and add new functionality continously. This document serves as a reference for any bug fixes or additions to our API.

Currently we rarely deprecate, and do not remove any API functionality.

## 2023-03-02
- Update description of `IncidentWorkflowTrigger.condition` to more clearly describe the impact around triggers starting either when an incident is created, or when conditions are met

## 2023-03-01
- Fix example for `POST /customfields/fields/{id}/field_options` endpoint

## 2023-02-22
- Adding deprecation notice to Response Plays. Because Incident Workflows are a more robust and powerful version of Response Plays, we will be working to upgrade accounts from Response Plays to Incident Workflows, ultimately culminating in a Response Plays end-of-life in late 2023. This affects the following endpoints:
   - `GET /response_plays`
   - `POST /response_plays`
   - `GET /response_plays/{id}`
   - `PUT /response_plays/{id}`
   - `DELETE /response_plays/{id}`
   - `POST /response_plays/{id}/run`

## 2023-02-14
- Allow `default_value` when `required` is false for the following endpoints
   - `POST /customfields/schemas`
   - `PUT /customfields/schemas/{id}`
   - `POST /customfields/schemas/{id}/field_configurations`
   - `PUT /customfields/schemas/{id}/field_configurations/{configuration_id}`

## 2023-02-13
- Remove `X-EARLY-ACCESS` header warning from `/incident_workflows` endpoints

## 2023-02-10
- Removed `name` from `PUT /customfields/fields/{id}` request body.

## 2023-02-09
- Update `IncidentWorkflowTrigger.permissions.team_ids` (string[]) => `IncidentWorkflowTrigger.permissions.team_id` (string)

## 2023-02-08
- Specify valid `type` property values on `IncidentWorkflow`, `IncidentWorkflowAction`, `IncidentWorkflowInstance`, `IncidentWorkflowStep` and `IncidentWorkflowTrigger`
- Add description to `steps` proprerty on `IncidentWorkflow`
- Specify `incident_workflow_instance.incident.id` is a required in `POST /incident_workflows/{id}/instances` request body
- Update `domain_name` and `name` property descriptions on `IncidentWorkflowAction`
- Remove currently unused `integration` as allowed enum value on `action_type` property on `IncidentWorkflowAction`

## 2023-02-03
- Fix type of `next_cursor` property on List Triggers and List Actions response bodies

### 2023-02-02
- Wording changes and typo correction for MS Teams Integration documentation
- Cleaned up the list of schemas in MS Teams Integration section

## 2023-02-02
- Added Early-Access endpoints for Custom Fields
   - `GET /customfields/fields`
   - `POST /customfields/fields`
   - `GET /customfields/fields/{id}`
   - `PUT /customfields/fields/{id}`
   - `DELETE /customfields/fields/{id}`

   - `GET /customfields/fields/{id}/schemas`

   - `GET /customfields/fields/{id}/field_options`
   - `POST /customfields/fields/{id}/field_options`
   - `GET /customfields/fields/{id}/field_options/{option_id}`
   - `PUT /customfields/fields/{id}/field_options/{option_id}`
   - `DELETE /customfields/fields/{id}/field_options/{option_id}`

   - `GET /customfields/schemas`
   - `POST /customfields/schemas`
   - `GET /customfields/schemas/{id}`
   - `PUT /customfields/schemas/{id}`
   - `DELETE /customfields/schemas/{id}`

   - `GET /customfields/schemas/{id}/field_configurations`
   - `POST /customfields/schemas/{id}/field_configurations`
   - `GET /customfields/schemas/{id}/field_configurations/{configuration_id}`
   - `PUT /customfields/schemas/{id}/field_configurations/{configuration_id}`
   - `DELETE /customfields/schemas/{id}/field_configurations/{configuration_id}`

   - `POST /customfields/schema_assignments`
   - `GET /customfields/schema_assignments`
   - `DELETE /customfields/schema_assignments/:id`

   - `PUT /incidents/:id/field_values`
   - `GET /incidents/:id/field_values`
   - `GET /incidents/:id/field_values/schema`
   - `GET /incidents/:id/?include[]=field_values`

## 2023-01-30
- Add `permissions` property to `IncidentWorkflowsTrigger` entity schema

## 2023-01-27
- Update Template API Documentation
  - Change render path to  /template/{id}/render, add `external` to request body and make `status_update.message` optional.
  - Add `template_type` filter to LIST endpoint
  - Remove Early Access flags

## 2023-01-26
- Update `GET /incident_workflows/triggers` endpoint to use cursor pagination
- Update `GET /incident_workflows/triggers` endpoint to include sort_by query parameter
- Update `GET /incident_workflows/actions` endpoint to use cursor pagination
- Remove `IncidentWorkflowAction.invoke_url` property
- Rename `IncidentWorkflowActionInput.default_value_serialized` property to `default_value`
- Rename `ActionInvocation.Inputs[].serialized_value` property to `value`
- Remove `IncidentWorkflowTrigger.workflow_id` and `IncidentWorkflowTrigger.workflow_name` properties
- Update `IncidentWorkflowTrigger.workflow` property to be a proper ResourceReference

## 2023-01-23
- Added `POST /incident_workflows/{id}/instances` endpoint

## 2023-01-16
- Added `POST /integration-ms-teams/incidents/{incident_id}/meeting` endpoint

## 2023-01-12
- Added optional `query` querystring parameter to `GET /incident_workflows`
- Added `DELETE /incident_workflows/{id}` endpoint

## 2023-01-09
- Added `GET /analytics/raw/incidents/{id}/responses` to the Analytics API

## 2022-12-22
- Added Early Access Incident Workflows endpoints including Triggers and Actions
- `GET /incident_workflows`
- `POST /incident_workflows`
- `GET /incident_workflows/{id}`
- `PUT /incident_workflows/{id}`
- `GET /incident_workflows/actions`
- `GET /incident_workflows/actions/{id}`
- `GET /incident_workflows/triggers`
- `POST /incident_workflows/triggers`
- `GET /incident_workflows/triggers/{id}`
- `PUT /incident_workflows/triggers/{id}`
- `POST /incident_workflows/triggers/{id}/services`
- `DELETE /incident_workflows/triggers/{trigger_id}/services/{service_id}`

## 2022-12-20
- Removed `integrations` key from the example response and response schema of `GET /event_orchestrations/`
- Replaced `integration` key with `integrations` in the example response of `GET /event_orchestrations/{id}`

## 2022-12-16
- Removed early access parameters from all automation_access endpoints; they are
  now in GA

## 2022-12-08
Clarified for service post/put the null option for alert_grouping_parameters.type will shut grouping off

## 2022-11-18
 - Added Automation Action Team Management endpoints.
 - `GET /automation_actions/action/{id}/teams`
 - `GET /automation_actions/action/{id}/teams/{team_id}`

## 2022-11-17
- Added Automation Action Management endpoints.
- `GET /automation_actions/actions/{id}/services`
- `GET /automation_actions/actions/{id}/services/{service_id}`

## 2022-11-14
- Added Automation Action Runner Management endpoints.
- `GET /automation_actions/runners/{id}/teams`
- `GET /automation_actions/runners/{id}/teams/{team_id}`

### 2022-11-09
- Updated specs of Automation Action Runner Management endpoints.
- `GET /automation_actions/runners`
- `POST /automation_actions/runners`
- `GET /automation_actions/runners/{id}`
- `PUT /automation_actions/runners/{id}`

### 2022-11-10
- Added Automation Action Invocation endpoints.
- `GET /automation_actions/invocations`
- `GET /automation_actions/invocations/{id}`
- `POST /automation_actions/actions/{id}/invocations`

---
### 2022-11-07
- Added Automation Action Management endpoints.
- `GET /automation_actions/actions`
- `POST /automation_actions/actions`
- `GET /automation_actions/actions/{id}`
- `DELETE /automation_actions/actions/{id}`
- `PUT /automation_actions/actions/{id}`
- `POST /automation_actions/actions/{id}/services`
- `DELETE /automation_actions/actions/{id}/services/{service_id}`
- `POST /automation_actions/actions/{id}/teams`
- `DELETE /automation_actions/actions/{id}/teams/{team_id}`

Added new fields within `alert_grouping_settings` for configuring Intelligent Alert Grouping with a flexible time window.
  - `POST /services`
  - `PUT /services/{id}`
  - `GET /services`
  - `GET /services/{id}`

### 2022-11-03
- Added Automation Action Runner Management endpoints.
- `GET /automation_actions/runners`
- `POST /automation_actions/runners`
- `GET /automation_actions/runners/{id}`
- `PUT /automation_actions/runners/{id}`
- `DELETE /automation_actions/runners/{id}`
- `POST /automation_actions/runners/{id}/teams`
- `DELETE /automation_actions/runners/{id}/teams/{team_id}`

### 2022-10-27
- Fixed the wording of the `query` query parameter. Previously it said it filtered over tags when it was actually filtering over an object's name field.
- `GET /schedules`
- `GET /escalation_policies`
- `GET /extensions`
- `GET /users`
- `GET /teams`
- `GET /tags`
- `GET /services`
- `GET /response_plays`
- `GET /maintenance_windows`

### 2022-10-24

Added documentation of Flexible Licensing within the API to support querying for License and License allocation information along with creating and updating Users with specified Licenses.

This introduces three new API endpoints:

- `GET /licenses` for retrieving the list of Licenses an Account has purchased along with usage and availability counts
- `GET /license_allocations` for retrieving what Licenses are allocated to what Users
- `GET /users/:id/license` for retrieiving the License assigned to an individual User

Additionally, two endpoints have been updated to support Licensing behavior:

- `POST /users` for assigning a License to a User when it is first created
- `PUT /users/:id` for assigning a new License to an existing User

### 2022-10-20
Added information on upcoming changes to [OAuth token expiries](https://developer.pagerduty.com/docs/f14c5f7a16fd5-o-auth-2-0-authorization-code-grant-flow#token-expiries)

All OAuth clients registered prior to October 30th 2022 will have the following settings:

 - access token expiry of one year
 - refresh token expiry of one year

After October 30th 2022, all newly registered OAuth clients will have the following settings:

 - access token expiry of 30 days
 - refresh token expiry of 210 days
 - rolling refresh window of 3 years

After April 30th 2023, we will apply the new expiry settings to all OAuth clients.
### 2022-10-05
- Added Templates API documentation
### 2022-09-13
- Updated Alerts definition in API Concepts
### 2022-09-13
- Updated Create Orchestration API to reference the correct endpoint and remove `id` as a required param
### 2022-09-02
- Updated Flex Service API to reflect new changes to allow bulk changes in Fields and Field Schemas
### 2022-08-18
- Updated Audit Trails params description with the new restriction of a max duration of 31 days.

### 2022-06-06
- Updated 'outlier_incident' documentation link to point to new 'Outlier Incident' documentation
  - `GET /incidents/{id}/outlier_incident`

### 2022-06-01
- Added `integrations` as option for `include[]` query parameter to the Get a Service endpoint.
  - `GET /services/{id}?include[]=integrations`

### 2022-05-27
- Provide example for how to query multiple incident statues.

### 2022-05-20
- Added custom html email documentation for Status Updates.

### 2022-05-12
- Added product limit documentation for Incident Notes.

### 2022-05-10
- Removed ended layer in schedule create example to guide users away from creating schedules with layers that are no longer in effect.
  - `POST /schedules`

### 2022-05-10
- Added rate limiting details for the "Manage incidents" endpoint. Only 500 requests per minute are allowed.

### 2022-05-10
- Fixed capitalization in the following routes
  - `POST /{entity_type}/{id}/change_tags`
  - `GET /{entity_type}/{id}/tags`
  - `GET /tags`
  - `POST /tags`
  - `GET /tags/{id}`
  - `DELETE /tags/{id}`

### 2022-05-09
- Expanded the description for `alerts.body.details` to indicate that this data can also be formatted as a string (not just as a JSON object)
  - `GET /incidents/{id}/alerts`

### 2022-05-05
- Changed description for "Manage incidents" to reflect the lower maximum of changed incidents. Only 250 incidents may be updated at a time.
  - `PUT /incidents/`

### 2022-04-29
- Updated definitions for Event Orchestration endpoints to include Automation Actions:
  - `GET /event_orchestrations/services/{id}`
  - `PUT /event_orchestrations/services/{id}`
- Added open Incidents limit description to documentation for service creation and update
  - `POST /services`
  - `PUT /services/{id}`

### 2022-04-18
- Updated definitions for Analytics endpoints.

### 2022-03-21
- Added product limit documentation for Services, Business Services, and Service Dependencies.

### 2022-03-17
- Removed reference to an incorrect statement in the documentation indicating a `password` property is accepted when updating a user.
  - `PUT /users/{id}`

### 2022-02-23
- Added new fields for configuring Auto-Pause Notifications to Services endpoints
  - `POST /services`
  - `PUT /services/{id}`
  - `GET /services`
  - `GET /services/{id}`

### 2022-02-23
- Updated documentation for JIRA Integration Rules API to indicate the maximum number of rules.

### 2022-02-17
- Added new endpoints for reporting counts on Incident Pause usage for a given reporting period for the requesting account or scoped to a service within the account. Can scope paused incidents on `rules` and `auto_pause`
  - `GET /paused_incident_reports/counts`
- Added new endpoints gettting the 5 most recent alerts that were triggered after being paused and the 5 most recent alerts that were resolved after being paused for a given reporting period for the requesting account or scoped to a service within the account. Can scope paused incidents on `rules` and `auto_pause`
  - `GET /paused_incident_reports/alerts`

### 2022-02-11
- Added documentation for Event Orchestration
  - `GET /event_orchestrations/services/{service_id}/active`
  - `PUT /event_orchestrations/services/{service_id}/active`


### 2022-02-09
- Updated link to the `API Concepts` page across all API Documentation (164 occurances) to point to the correct page, this link has been broken since the migration to the new API Documentation platform.


### 2022-01-31
- Removed reference to an incorrect statement in the documentation indicating a `password` property is required for user creation.
  - `POST /users`


### 2022-01-26
- Added missing documentation for the `Images` field
  - `POST /change/enqueue`

### 2022-01-24
- Fix missing `From` header requirement on response play endpoints.
  - `POST /response_plays`
  - `PUT /response_plays/{response_play_id}`
  - `DELETE /response_play/{response_play_id}`

### 2022-01-22
- Added documentation for `urgency` query parameter for `GET /users/{user_id}/notification_rules` endpoint.

### 2022-01-14
- *BREAKING* Beginning November 2021, newly issued oauth tokens are no longer included in the `users/{id}/sessions` endpoints

### 2022-01-13
- Added documentation for Event Orchestration
  - `GET /event_orchestrations`
  - `POST /event_orchestrations`
  - `GET /event_orchestrations/{orchestration_id}`
  - `PUT /event_orchestrations/{orchestration_id}`
  - `DELETE /event_orchestrations/{orchestration_id}`
  - `GET /event_orchestrations/{orchestration_id}/router`
  - `PUT /event_orchestrations/{orchestration_id}/router`
  - `GET /event_orchestrations/{orchestration_id}/unrouted`
  - `PUT /event_orchestrations/{orchestration_id}/unrouted`
  - `GET /event_orchestrations/services/{service_id}`
  - `PUT /event_orchestrations/services/{service_id}`

### 202l-01-06
- Updated how since and until parameters work for schedules GET API

### 2021-12-1
- Added documentation for `custom_headers` as part of the `delivery_method` on a `subscription_webhook`

### 2021-11-30
- Added documentation for `incidents_responders` and `responder_requests` as part of Incident responses

### 2021-11-03
- Added `user` to Log Entry
- Added `notification` to Channel
- Added `conferenceAddress` to Notification

### 2021-09-06
- Added the authorization section for Slack Connections
- Added `notification_type` to `SlackConnection` model.
   - The field allows users to set which format of slack card they would like to receive.
   - The field has been added to all `/workspaces/{slack_team_id}/connections` endpoints' request and response schema.
   - The field has two options `responder` and `stakeholder`, and defaults to `responder` on `PUT` and `POST`

### 2021-07-26
- Added documentation for HandoffNotificationRules
  - `GET /users/{user_id}/oncall_handoff_notification_rules/`
  - `POST /users/{user_id}/oncall_handoff_notification_rules/`
  - `DELETE /users/{user_id}/oncall_handoff_notification_rules/`
  - `GET /users/{user_id}/oncall_handoff_notification_rules/{oncall_handoff_notification_rule_id}`
  - `PUT /users/{user_id}/oncall_handoff_notification_rules/{oncall_handoff_notification_rule_id}`

### 2021-07-26
- Removed requirement for teams ability to use `team_ids` filter
  - `POST /analytics/raw/incidents`
  - `POST /analytics/metrics/incidents/all`
  - `POST /analytics/metrics/incidents/services`
  - `POST /analytics/metrics/incidents/teams`

### 2021-06-29
- Updated documentation for Incident Notes now that the API can differentiate between User-created Notes and system-created Notes.
  - `GET /incidents/{id}/notes`

### 2021-06-28
- Removed limits for `team_ids` and `service_ids` filters
  - `POST /analytics/raw/incidents`

### 2021-06-14
- Removed Early-Access for Related Change Events endpoint
  - `GET /incidents/{id}/related_change_events`

### 2021-06-09
- Added new API endpoint that returns Outlier Incident information for a given incident on its Service.
  - `GET /incidents/{incident_id}/outlier_incident`

### 2021-05-18
- Fixed typos in Slack Integration API documentation
- Added `incident.status_update_published` event to Slack Connection

### 2021-05-10
- Wording changes for past incidents documentation

### 2021-05-06
- Added new API endpoints that provide the ability to create Slack specific Webhook Subscriptions (Slack Connections). These endpoints are used to manage mappings between Slack channels and PagerDuty Services and Teams.
  - `GET /workspaces/{slack_team_id}/connections`
  - `POST /workspaces/{slack_team_id}/connections`
  - `GET /workspaces/{slack_team_id}/connections/{connection_id}`
  - `PUT /workspaces/{slack_team_id}/connections/{connection_id}`
  - `DELETE /workspaces/{slack_team_id}/connections/{connection_id}`

### 2021-04-28
- Fix missing From header requirement on response play endpoints.
  - `GET /response_plays`
  - `GET /response_plays/{id}`

### 2021-04-23
- Removed Early Access for webhook-v3. `webhooks_early-access`

### 2021-04-22
- Added documentation on the new acive field for webhook_subscriptions.

### 2021-04-20
- Added includes to list schedules endpoint with an example
  - `GET /schedules`

### 2021-04-12
- Added subdomain as part of includes
  - `GET /users/me`

### 2021-04-12
- Added Early-Access endpoint for Related Change Events
  - `GET /incidents/{id}/related_change_events`

### 2021-04-01
- Added bulk overrides functionality to `PUT /schedules/{id}/overrides`. This deprecates the original single-override request/response schema and semantics. We will continue to support unmanaged clients using the deprecated schema and semantics.

### 2021-03-30
- Fix assignee response format for AssignLogEntry and EscalateLogEntry

### 2021-03-24
- Added documentation on setting filters and parsers for generic email inbound integrations


### 2021-02-24
- Removed Early Access for User Subscription endpoints. `usms-early-access`

### 2021-02-05
- Added one new Early-Access endpoint for enabling a webhook subscription
  - `POST /webhook_subscriptions/{id}/enable`

### 2021-02-03
- Added nine new Early-Access endpoints for business impact monitoring and management.
  - `GET /business_services/impactors`
  - `GET /business_services/{id}/impactors`
  - `GET /business_services/impacts`
  - `GET /business_services/{id}/supporting_services/impacts`
  - `GET /incidents/{id}/business_services/impacts`
  - `PUT /incidents/{id}/business_services/{business_service_id}/impacts`
  - `GET /business_services/priority_thresholds`
  - `PUT /business_services/priority_thresholds`
  - `DELETE /business_services/priority_thresholds`

- Added five new Early-Access endpoints for Status Dashboards
  - `GET /status_dashboards`
  - `GET /status_dashboards/{id}`
  - `GET /status_dashboards/url_slugs/{url_slug}`
  - `GET /status_dashboards/{id}/service_impacts`
  - `GET /status_dashboards/url_slugs/{url_slug}/service_impacts`

### 2021-01-19
- Added a new public endpoint for the Related Incidents.
  - `GET /incidents/{id}/related_incidents`

### 2021-01-18
- Documented Offset Pagination more clearly.

### 2021-01-08
- Added a new public endpoint for Past Incidents.
  - `GET /incidents/{id}/past_incidents`

### 2021-01-05
- Added response examples for audit records endpoints
  - `GET /users/{id}/audit/records`
  - `GET /teams/{id}/audit/records`
  - `GET /services/{id}/audit/records`
  - `GET /schedules/{id}/audit/records`
  - `GET /escalation_policies/{id}/audit/records`

### 2020-12-23
- Added 14 new Early-Access endpoints for Status Update subscription management.
  - `GET /business_services/{id}/account_subscription`
  - `DELETE /business_services/{id}/account_subscription`
  - `GET /business_services/{id}/subscribers`
  - `POST /business_services/{id}/subscribers`
  - `POST /business_services/{id}/unsubscribe`
  - `GET /incidents/{id}/status_updates/subscribers`
  - `POST /incidents/{id}/status_updates/subscribers`
  - `POST /incidents/{id}/status_updates/unsubscribe`
  - `GET /teams/{id}/notification_subscriptions`
  - `POST /teams/{id}/notification_subscriptions`
  - `POST /teams/{id}/notification_subscriptions/unsubscribe`
  - `GET /users/{id}/notification_subscriptions`
  - `POST /users/{id}/notification_subscriptions`
  - `POST /users/{id}/notification_subscriptions/unsubscribe`

### 2020-12-16
- Updated Cursor for the Analytics Raw Incidents endpoint to be an opaque/encoded string instead of an id.
- Added ability to order by seconds_to_resolve in the Analytics Raw Incidents endpoint.
- Added ability to specify the sort order (asc/desc) in the Analytics Raw Incidents endpoint.

### 2020-12-14
- Updated how Alert Grouping can be configured for Services using Services API. New field are backwards compatible.

### 2020-12-01
- Updated record-level audit trail record listing endpoints to indicate that a 402 Payment Required response can be returned for unentitled accounts. This now matches the account-level audit trail record listing endpoint's behavior.

### 2020-12-01
- Changed timestamp field from required to optional for Event V2 `/change/enqueue` endpoint.

### 2020-11-25
- Removed Early-Access Header for all Change Events endpoints.
- Removed Early-access requirements for all audit records APIs.

### 2020-11-17
- Updated date_range documentation to reflect the maximum (6 month) and default (1 month) durations we enforce.

### 2020-11-05
- *BREAKING* The Subscriptions API used to manage V3 webhooks is now the Webhook Subscriptions API. You can find the details in their new home under the "Webhooks" tag.
  - `GET /webhook_subscriptions`
  - `POST /webhook_subscriptions`
  - `GET /webhook_subscriptions/{id}`
  - `PUT /webhook_subscriptions/{id}`
  - `DELETE /webhook_subscriptions/{id}`
  - `POST /webhook_subscriptions/{id}/ping`

### 2020-11-03
- *BREAKING* Restricted the set of valid actions in the Audit records query

### 2020-10-28
- *BREAKING* Changed audit record params for `resource_types` to `root_resource_types`.

### 2020-10-27
- Added Early-Access endpoints for Change Events
  - `GET /change_events`
  - `GET /change_events/{id}`
  - `GET /services/{id}/change_events`
  - `PUT /change_events/{id}`

### 2020-10-22
- *BREAKING* Changed top level attribute for `resource` to `root_resource` in audit record schema.

### 2020-10-20
- Removed the Early-Access headers from all the Service-level Event Rules endpoints.

### 2020-10-15
- *BREAKING* Removed Business Services filter from all `/analytics` endpoints.
- Improved error messaging for all `/analytics` endpoints
- Added documentation for expected behavior of `Incident.assignments` and `Incident.acknowledgments`.

### 2020-10-13
- Clarified the process of getting authorization headers for IntegrationJiraService API
- Added Early-Access endpoints for the Subscriptions API used to manage V3 webhooks.

### 2020-10-05
- *BREAKING* Updated pagination for Early-Access Audit records endpoints.

### 2020-09-28
- *BREAKING* Temporarily removing early-Access endpoints around incident subscription management.
   - `GET /users/{id}/notification_subscriptions`
   - `POST /users/{id}/notification_subscriptions`
   - `POST /users/{id}/notification_subscriptions/unsubscribe`
   - `GET /incidents/{id}/status_updates/subscribers`
   - `POST /incidents/{id}/status_updates/subscribers`
   - `POST /incidents/{id}/status_updates/unsubscribe`

### 2020-09-17
- *BREAKING* Changed `total_assignment_count` metric to `mean_assignment_count` in `/analytics` Early Access endpoints.
- Added `up_time_pct` and `user_defined_effort_seconds` metrics to `/analytics` Early Access endpoints.
- Updated response examples and some definitions in `/analytics` Early Access Endpoints.

### 2020-09-16
- Add [Change Events](https://developer.pagerduty.com/docs/events-api-v2/send-change-events/) to Events API V2

### 2020-09-16
- Added Early-Access endpoints for Service-level Event Rules
   - `GET /services/{id}/rules`
   - `POST /services/{id}/rules`
   - `GET /services/{id}/rules/{rule_id}`
   - `PUT /services/{id}/rules/{rule_id}`
   - `DELETE /services/{id}/rules/{rule_id}`
- Added Early-Access `variables` field to Event Rule model.
- Added Early-Access `template` style extraction action to Event Rule model.

### 2020-09-15
- Clarified `status` on `POST /services` endpoint.

### 2020-09-08
- Fixed a lot of example requests and responses.

### 2020-09-02
- Added Audit Record description in API CONCEPTS document.
- Clarified in the descriptions of audit record endpoints that records are returned in lists.

### 2020-08-28
- Added Early-Access endpoint for audit trail records
   - `GET /services/{id}/audit/records`

### 2020-08-27
- Added Early-Access endpoint for audit trail records
   - `GET /escalation_policies/{id}/audit/records`

### 2020-08-27
- Documented [Events V2 integration](https://developer.pagerduty.com/docs/events-api-v2/overview/) type on `/services/{id}/integrations` endpoints.
    - Note: This existed previously and was missing from this documentation.

### 2020-08-24
- Clarified `contact_method` on various User Contact Method management endpoints.
- Clarified Notification Subscription endpoints current under the Early Access.

### 2020-08-18
- Added Early-Access endpoints for audit trail records
   - `GET /schedules/{id}/audit/records`

### 2020-08-12
- Added `conference_type` param to `ResponsePlay` model

### 2020-08-10
- Added documentation on `config` and `headers` options for webhooks v2.
- Added Request Examples with custom headers.

### 2020-08-07
- Updated models to include standard fields such as `id`, `type`, `summary`, `html_url`, and `self`.
- Fixed inconsistencies with the `Reference` model.

### 2020-08-06
- Added Early-Access endpoints for audit trail records
   - `GET /audit/records`
   - `GET /teams/{id}/audit/records`
   - `GET /users/{id}/audit/records`

### 2020-08-04
- Added 6 new Early-Access endpoints around incident subscription management.
    - `GET /users/{id}/notification_subscriptions`
    - `POST /users/{id}/notification_subscriptions`
    - `POST /users/{id}/notification_subscriptions/unsubscribe`
    - `GET /incidents/{id}/status_updates/subscribers`
    - `POST /incidents/{id}/status_updates/subscribers`
    - `POST /incidents/{id}/status_updates/unsubscribe`

### 2020-07-24
- Updated the request sample for `POST /extensions` and `PUT /extensions/{id}`.
- Clarified Content-Type header for all endpoints.

### 2020-07-10
- Updated filters for all 5 `/analytics/metrics` and `/analytics/raw` endpoints. The `business_service_ids` filter is added as a possible optional filter choice. This filter accepts an array, to allow filtering by multiple business service IDs.

### 2020-07-08
- Add limit to the number of incidents or alerts that can be updated in a single API call to multi-update (i.e. `PUT /incidents`) above which the client receives status 413.

### 2020-07-08
- Updated filters for all 5 `/analytics/metrics` and `/analytics/raw` endpoints. The `priority` filter is replaced by `priority_ids` and `priority_names` filters. Both of these new filters accept an array, to allow filtering by multiple priority IDs or names.

### 2020-07-01
- Added documentation for configuring JIRA integration via API

### 2020-06-29
- Updated required headers, and filters for `POST analytics/raw/incidents`, `POST analytics/metrics/incidents/all`, `POST analytics/metrics/incidents/services` and `POST analytics/metrics/incidents/teams`.
- Added `GET`, `DELETE`, and `PUT /users/{user_id}/status_update_notification_rules/{status_update_notitication_rule_id}`
- Added `GET`, `POST /users/{user_id}/status_update_notification_rules`

### 2020-06-22
- Document `POST extensions/{id}/enable` for extensions that are temporarily disabled.

### 2020-06-18
- Added `POST analytics/metrics/incidents/all`, `POST analytics/metrics/incidents/services` and `POST analytics/metrics/incidents/teams` endpoints for Early Access.

### 2020-06-17
- Moved `POST analytics/incidents` and `GET analytics/incidents/{id}` to `POST analytics/raw/incidents` and `GET analytics/raw/incidents/{id}`

### 2020-06-15
- Added `POST analytics/incidents` and `GET analytics/incidents/{id}` endpoints for Early Access.

### 2020-06-05
- Modified `optional_total` query param to `total` on the business service list endpoint.
- `optional_total` field will continue to be supported.

### 2020-06-01
- Added `suspend` event rule action to the API.

### 2020-05-29
- Added `GET /response_plays`, `POST /response_plays`, `GET /response_plays/{id}`, `PUT /response_plays/{id}`, and `DELETE /response_plays/{id}` endpoints.
- Updated Response Plays description in API CONCEPTS document.

### 2020-05-27
 - Documented `total` query parameter on paginated endpoints.

### 2020-05-19
 - Added a `PUT log_entries/{id}/channel` endpoint to enable updates to log entry channel details.

### 2020-05-12
 - Fix Schema of `/teams/{id}/members` endpoint to match reality of behaviour.

### 2020-04-30
 - Add `teams` field to `Schedule` model, which is supported for updates and included in responses.
 - Clarified Reference Model, `id` field is required.

### 2020-04-27
 - Document `include[]=temporarily_disabled` for extensions.

### 2020-04-24
 - Add `type` fields to `Log Entry` models.
 - Fixed issue with Postman build. New version available, and new ones will continue to be published with each new update here.

### 2020-04-21
 - Fixed model `type` fields in schema definitions.
 - Fix issues with Request Examples

### 2020-04-15
 - Updated all reference schemas to better match reality of API.
 - Added examples to all Request and Response body's that were missing them.

### 2020-04-15
 - Added Events V1 and Events V2 APIs.

### 2020-04-13
 - Modified response and request examples to match OpenAPI 3.0.1 schema

### 2020-04-09
 - Added a `GET /service_dependencies/technical_services/{id}` endpoint.
 - *BREAKING* `POST /service_dependencies/associate` was changed from 204 to 200 for successful changes.
 - *BREAKING* `POST /service_dependencies/disassociate` was changed from 204 to 200 for successful changes.
 - *Documentation Change* Fixed a mistake in the documentation. The `relationships` property in the request for `POST /service_dependencies/associate` and `POST /service_dependencies/disassociate` is an array and not an object.
 - *Documentation Change* The `service_dependencies` endpoints can now be found at the top level instead of under the `Business Services` section.

### 2020-04-06
 - Added new Rulesets endpoints

### 2020-04-01
 - Added `since` and `until` parameters to `GET /incidents/{id}/log_entries`.

### 2020-03-24
 - Added `teams` to all `/business_services` endpoints.

### 2020-03-23
 - Clarified language on `GET /tags` query parameter to better explain how matching happens.

### 2020-03-02
 - Add new Business Services endpoints

### 2020-02-26
 - `GET /oncalls OnCalls[].end` will now correctly respond `null` only when the user does not go off call.

### 2020-01-27
 - Clarified `POST /escalation_policies` description.

### 2020-01-10
- Added `on_call_handoff_notifications` to `EscalationPolicy` model.
  - The field allow users to set whether they would like on-call handoff notifications for escalation policies that have no attached services.
  - The field has been added to all `/escalation_policies` endpoints' request and response schema.
  - The field has two options `always` and `if_has_services`, and defaults to `if_has_services` on `PUT` and `POST`
