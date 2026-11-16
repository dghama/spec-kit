# Use Case: Manage Laptop Requests for New Hires

## Overview

**Use Case ID:** UC-11926

**Use Case Name:** Manage laptop requests for new hires

**Primary Actor:** IT administrator

**Goal:** Review and update submitted laptop requests so equipment readiness is visible to managers before new employees start.

**Status:** Draft

**Jira:** [FASAWE-11926 - Manage Laptop Requests for New Hires](https://mobelite.atlassian.net/browse/FASAWE-11926)

**UI:** No approved mockup is referenced in the Jira story; follow existing application conventions.

## Preconditions

- Laptop requests have been submitted by managers through [UC-11885: Request a Laptop for a New Hire](./UC-11885-new-hire-laptop-request.md).
- Each request is linked to an onboarding record and a selected laptop profile.
- IT administrator roles and permissions are available.
- Equipment is prepared before an IT administrator marks a request **Ready**.

## Main Success Scenario

1. The IT administrator opens the laptop request management view.
2. The system displays submitted requests with the employee's name, start date, requested laptop profile, submission date, and current status, sorted by submission date with the most recent first.
3. The IT administrator optionally filters the list by status or searches by the employee's name.
4. The IT administrator opens a request.
5. The system displays the employee information, selected laptop profile, and request details, including the values shown in the request list and any rejection reason.
6. The IT administrator selects one of the available statuses: **Pending**, **Approved**, **In Progress**, **Ready**, or **Rejected**. If selecting **Rejected**, the IT administrator provides a rejection reason.
7. The system saves the selected status.
8. If the selected status is **Ready**, the system records the date and time of the status update.
9. The manager can see the updated status.

## Alternative Flows

### A1: The IT administrator rejects a request without a reason

**Trigger:** The IT administrator selects **Rejected** without providing a rejection reason (step 6).

**Flow:**

1. The system prevents the status update because a rejection reason is mandatory.
2. The request remains unchanged. The IT administrator can provide a reason and retry.
3. Use case continues at step 6.

### A2: A manager attempts to change a request status

**Trigger:** A manager views one of their submitted requests and attempts to modify its status.

**Flow:**

1. The system allows the manager to view their own submitted request but does not allow them to modify its status.
2. Use case ends.

## Postconditions

### Success Postconditions

- The selected request status is saved.
- The manager can see the updated status.
- When a request is marked **Ready**, the date and time of that status update are recorded.
- A rejected request has a visible rejection reason.

### Failure Postconditions

- A rejected status without a reason is not saved.
- A manager cannot change the status of a submitted request.
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

## Out of Scope

- Submitting a new laptop request; that flow is defined in UC-11885.
- Creating or maintaining employee onboarding records or laptop profiles.
- Assigning a physical laptop or tracking asset allocation. The Product Owner clarified on 2026-11-16 that this use case covers request status and readiness only.

## Open Questions

None currently identified from the Jira acceptance criteria and Product Owner clarifications.
