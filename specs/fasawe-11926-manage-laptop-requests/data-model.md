# Data Model: Manage Laptop Requests for New Hires

This is a behavior-level model derived from UC-11926. It does not prescribe database tables, field types, or persistence technology.

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
| Profile | Selected laptop profile | Shown in the request list and details. |

### Laptop Request

A submitted request for equipment linked to an employee and selected laptop profile.

| Attribute | Meaning | Validation / behavior |
|---|---|---|
| Employee | Employee receiving the equipment | Shown in the list and details; linked to an onboarding record. |
| Laptop profile | Selected profile | Shown in the list and details. |
| Submission date | Date the request was submitted | Shown in the list and details; list is ordered newest first. |
| Status | Current request status | One of Pending, Approved, In Progress, Ready, or Rejected. Any listed status may be selected. |
| Rejection reason | Explanation for a rejected request | Required when selecting Rejected and visible in request details. |
| Ready status update date/time | Time the request was marked Ready | Recorded when the selected status is Ready. |

## Actors and access

- **IT administrator**: Can view the submitted request list and details, search and filter requests, and update request statuses.
- **Manager**: Can view their own submitted request and its updated status, but cannot change its status.

## Relationships

- Each laptop request references one employee and the employee's onboarding record.
- Each laptop request references one selected laptop profile.
- A manager's view is limited to their own submitted requests.

## Validation and state behavior

- The IT administrator's list shows employee name, start date, requested laptop profile, submission date, and current status, ordered by submission date from most recent to oldest.
- IT administrators can filter the list by status and search by employee name.
- Request details include the employee information, selected profile, onboarding-record link, the list values, and any rejection reason.
- Selecting Rejected without a reason prevents the update; the request remains unchanged.
- Selecting Ready records the date and time of that status update. The equipment must be prepared before this status is selected.
- Managers can see the updated status, but attempts by a manager to change it are not allowed.
