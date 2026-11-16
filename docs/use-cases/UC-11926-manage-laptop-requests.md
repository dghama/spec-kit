# Use Case: Manage Laptop Requests for New Hires

## Overview

**Use Case ID:** UC-11926

**Use Case Name:** Manage laptop requests for new hires

**Primary Actor:** IT administrator

**Goal:** Review laptop requests, update eligible request details, and manage readiness so equipment information is accurate and visible to managers before new employees start.

**Status:** Draft

**Jira:** [FASAWE-11926 - Manage Laptop Requests for New Hires](https://mobelite.atlassian.net/browse/FASAWE-11926)

**Related Jira:** [FASAWE-11886 - Update Laptop Request Details](https://mobelite.atlassian.net/browse/FASAWE-11886)

**UI:** No approved mockup is referenced in the Jira story; follow existing application conventions.

## Preconditions

- Laptop requests have been submitted by managers through [UC-11885: Request a Laptop for a New Hire](./UC-11885-new-hire-laptop-request.md).
- Each request is linked to an onboarding record and a selected laptop profile.
- IT administrator roles and permissions are available.
- Equipment is prepared before an IT administrator marks a request **Ready**.
- For detail edits, the request status is **Pending**, **Approved**, or **In Progress**.

## Main Success Scenario

1. The IT administrator opens the laptop request management view.
2. The system displays submitted requests with the employee's name, start date, requested laptop profile, submission date, and current status, sorted by submission date with the most recent first.
3. The IT administrator optionally filters the list by status or searches by the employee's name.
4. The IT administrator opens a request.
5. The system displays the employee information, selected laptop profile, and request details, including the values shown in the request list and any rejection reason.
6. If the request is **Pending**, **Approved**, or **In Progress** and its details need correction, the IT administrator selects the Edit action.
7. The system allows the IT administrator to change the laptop profile to an available profile and update requested equipment specifications. Employee information cannot be edited through the laptop request.
8. The IT administrator updates the editable details and saves the request.
9. The system validates the modified fields, preserves mandatory values, and saves valid changes to the existing request without creating a duplicate. The request ID remains unchanged, the update date and time and administrator are recorded, previous request information remains available in the update history, and the system confirms the successful update.
10. The IT administrator may select one of the available statuses: **Pending**, **Approved**, **In Progress**, **Ready**, or **Rejected**. If selecting **Rejected**, the IT administrator provides a rejection reason.
11. The system saves the selected status.
12. If the selected status is **Ready**, the system records the date and time of the status update.
13. The manager can see the updated status.

## Alternative Flows

### A1: The IT administrator rejects a request without a reason

**Trigger:** The IT administrator selects **Rejected** without providing a rejection reason (step 6).

**Flow:**

1. The system prevents the status update because a rejection reason is mandatory.
2. The request remains unchanged. The IT administrator can provide a reason and retry.
3. Use case continues at step 6.

### A2: A manager attempts to modify a request

**Trigger:** A manager views one of their submitted requests and attempts to modify its status or details.

**Flow:**

1. The system allows the manager to view their own submitted request but does not allow them to modify its status or request details.
2. Use case ends.

### A3: The IT administrator attempts to edit a request that is not eligible

**Trigger:** The IT administrator opens a request with **Ready** or **Rejected** status and looks for the Edit action.

**Flow:**

1. The system does not offer the Edit action for the request.
2. The request details remain unchanged. The IT administrator can continue to view the request or use the existing status-management flow.
3. Use case ends.

### A4: The IT administrator submits invalid request details

**Trigger:** The IT administrator attempts to save an update with a missing mandatory value or an invalid laptop profile selection.

**Flow:**

1. The system prevents the update and displays validation messages for the invalid fields.
2. The existing request details and request ID remain unchanged. The IT administrator can correct the values and retry.
3. Use case continues at step 8.

## Postconditions

### Success Postconditions

- The selected request status is saved.
- The manager can see the updated status.
- When a request is marked **Ready**, the date and time of that status update are recorded.
- A rejected request has a visible rejection reason.
- A valid detail update changes the existing request without creating a duplicate; the request ID is preserved.
- The update date and time and the responsible IT administrator are recorded, and prior request information remains available in the update history.

### Failure Postconditions

- A rejected status without a reason is not saved.
- A manager cannot change the status or details of a submitted request.
- Request details cannot be edited when the status is **Ready** or **Rejected**.
- An invalid detail update leaves the existing request information unchanged.
- Requests remain available with their existing status when an update is prevented.

## Business Rules

### BR-001: Request list

The IT administrator can view submitted laptop requests. Each list item shows the employee's name, start date, requested laptop profile, submission date, and current status. Requests are ordered from most recent to oldest by submission date.

### BR-002: Request details

The request details show the employee information and selected laptop profile and identify the onboarding record linked to the request.

### BR-003: Status updates

IT administrators can select any of the listed statuses: **Pending**, **Approved**, **In Progress**, **Ready**, or **Rejected**. The system saves the selected status. This reflects the Product Owner's clarification on 2026-11-16 that any listed status may be selected.

### BR-004: Rejection reason

A rejection reason is required to set a request to **Rejected** and is visible in the request details.

### BR-005: Ready status

An IT administrator may mark a request **Ready** once the equipment is prepared. The system records the date and time of that status update, and the manager can see the updated status.

### BR-006: Request search and filtering

IT administrators can filter requests by status and search by the employee's name. The list reflects the selected filter or search.

### BR-007: Access control

Only authorized IT administrators can manage requests and change their statuses. Managers can view their own submitted requests but cannot change their statuses.

### BR-008: Request detail access

Only IT administrators can edit laptop request details. Managers cannot edit request details through this use case.

### BR-009: Eligible request statuses for detail edits

IT administrators can edit details for requests with **Pending**, **Approved**, or **In Progress** status. Requests with **Ready** or **Rejected** status cannot be edited, and the Edit action is unavailable for those requests. This restriction applies to detail edits; the existing status-management behavior remains governed by BR-003.

### BR-010: Editable request details

The editable details are limited to the laptop profile and requested equipment specifications. A new laptop profile must be selected from the available profiles. Employee information, including information linked to the onboarding record, cannot be edited through the laptop request.

### BR-011: Detail validation and save

The system validates modified details before saving. Mandatory fields cannot be left empty. A successful update preserves the existing request ID and does not create a duplicate request; the system confirms the update.

### BR-012: Detail update history

For each successful detail update, the system records the update date and time and the administrator who made the change. Previous request information remains available in the update history.

### BR-013: Failed detail updates

If detail validation fails, the system prevents the update, displays appropriate validation messages, and leaves the existing request information unchanged.

## Out of Scope

- Submitting a new laptop request; that flow is defined in UC-11885.
- Creating or maintaining employee onboarding records or laptop profiles.
- Assigning a physical laptop or tracking asset allocation. The Product Owner clarified on 2026-11-16 that this use case covers request status and readiness only.

## Open Questions

None currently identified from the Jira acceptance criteria and clarifications. For FASAWE-11886, editable details are limited to the laptop profile and requested equipment specifications.
