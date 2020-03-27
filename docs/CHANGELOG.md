# Changelog

PagerDuty aims to have no breaking changes to our API, we do fix bugs and add new functionality continously. This document serves as a reference for any bug fixes or additions to our API.

Currently we do not deprecate or remove any API functionality.

----

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