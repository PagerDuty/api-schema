# Changelog

PagerDuty aims to have no breaking changes to our API, we do fix bugs and add new functionality continously. This document serves as a reference for any bug fixes or additions to our API.

Currently we do not deprecate or remove any API functionality.

----

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

### 2020-01-27
 - Clarified `POST /escalation_policies` description.

### 2020-02-26
 - `GET /oncalls OnCalls[].end` will now correctly respond `null` only when the user does not go off call.

### 2020-01-10
 - Added `on_call_handoff_notifications` to `EscalationPolicy` model.
   - The field allow users to set whether they would like on-call handoff notifications for escalation policies that have no attached services.
   - The field has been added to all `/escalation_policies` endpoints' request and response schema.
   - The field has two options `always` and `if_has_services`, and defaults to `if_has_services` on `PUT` and `POST`
