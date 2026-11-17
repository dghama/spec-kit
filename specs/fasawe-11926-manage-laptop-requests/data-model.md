# Data Model: Manage Laptop Requests for New Hires

This is a behavior-level model derived from UC-11926. It does not prescribe database tables, field types, concurrency tokens, or persistence technology.

## Entities

### Employee

The employee associated with a laptop request through an onboarding record.

| Attribute | Meaning | Validation / behavior |
|---|---|---|
| Name | Employee's name | Shown in the request list and details; searchable by IT administrators. |
| Start date | Employee's start date | Shown in the request list and details. |
| Onboarding record | Existing record linked to the request | The request details identify the linked record. |

### Laptop Profile

The selected laptop profile associated with a request.

| Attribute | Meaning | Validation / behavior |
|---|---|---|
| Profile | Selected laptop profile | Shown in the request list and details; an edit must select an available profile. |
| Availability | Whether the profile can currently be selected | Only available profiles may be selected during a detail edit. |

### Laptop Request

A submitted request for equipment linked to an employee and selected laptop profile.

| Attribute | Meaning | Validation / behavior |
|---|---|---|
| Request ID | Stable identity of the submitted request | Remains unchanged after a successful detail update; updates do not create a duplicate request. |
| Employee | Employee receiving the equipment | Shown in the list and details; linked to an onboarding record and not editable through this flow. |
| Laptop profile | Selected profile | Shown in the list and details; editable only to an available profile for an eligible request. |
| Requested equipment specifications | Equipment details requested for the employee | Editable only for eligible requests; required values are validated before saving. The specific fields are defined by the target application and are not enumerated by the use case. |
| Submission date | Date the request was submitted | Shown in the list and details; list is ordered newest first. |
| Status | Current request status | One of Pending, Approved, In Progress, Ready, or Rejected. Any listed status may be selected. |
| Rejection reason | Explanation for a rejected request | Required when selecting Rejected and visible in request details. |
| Ready status update date/time | Time the request was marked Ready | Recorded when the selected status is Ready. |
| Detail update date/time | Time of the latest successful detail update | Recorded for each successful detail update. |
| Detail updated by | IT administrator responsible for the latest successful detail update | Recorded for each successful detail update. |
| Update history | Prior request information for successful detail updates | Previous values remain available after each successful detail update. |

## Actors and access

- **IT administrator**: Can view the submitted request list and details, search and filter requests, edit eligible request details, and update request statuses.
- **Manager**: Can view their own submitted request and its updated status, but cannot change request details or status.

## Relationships

- Each laptop request references one employee and the employee's onboarding record.
- Each laptop request references one selected laptop profile.
- A manager's view is limited to their own submitted requests.
- Each successful detail update is attributable to an IT administrator and retains the prior request information in update history.

## Validation and state behavior

- The IT administrator's list shows employee name, start date, requested laptop profile, submission date, and current status, ordered by submission date from most recent to oldest.
- IT administrators can filter the list by status and search by employee name.
- Request details include the employee information, selected profile, onboarding-record link, the list values, and any rejection reason.
- Only IT administrators may edit details, and only while status is Pending, Approved, or In Progress. The Edit action is unavailable for Ready and Rejected requests.
- Detail edits may change only the laptop profile and requested equipment specifications. Employee and onboarding information are not editable through this flow.
- Invalid mandatory values or an unavailable profile prevent saving and leave the request ID and existing details unchanged.
- A successful detail update preserves the request ID, creates no duplicate request, records update date/time and administrator, and preserves prior request information in history.
- A stale edit is rejected and the administrator is asked to reload the latest request; the other administrator's saved changes remain intact. The concrete concurrency mechanism is implementation-specific.
- Selecting Rejected without a reason prevents the update; the request remains unchanged.
- Selecting Ready records the date and time of that status update. The equipment must be prepared before this status is selected.
- Managers can see the updated status, but attempts by a manager to change request details or status are not allowed.
