# Quickstart: Validate Laptop Request Management

This guide is technology-agnostic because the application repository and stack have not been identified. Run these scenarios in the target application once its environment and test commands are known.

## Prerequisites

- An authorized IT administrator account and a manager account.
- Submitted laptop requests linked to employees, onboarding records, and selected laptop profiles.
- Requests in Pending, Approved, In Progress, Ready, and Rejected statuses; at least one request in each editable status; and two administrators able to edit the same request for the stale-save scenario.
- At least one available alternative laptop profile and valid requested equipment specifications.
- Equipment prepared for any request used in the Ready scenario.
- The target application's documented setup and test/run commands (not available in this repository). Use those commands to run the corresponding automated tests once the target repository is identified.

## Scenarios

1. **Request list and ordering**: Open the management view as an IT administrator. Verify the list shows employee name, start date, requested profile, submission date, and status, with the most recently submitted request first.
2. **Search and filter**: Search by an employee name and filter by a status. Verify the displayed requests match the active search or filter.
3. **Request details**: Open a request. Verify employee information, selected profile, linked onboarding record, list values, and any rejection reason are displayed.
4. **Eligible detail edits**: For requests in Pending, Approved, and In Progress, edit the laptop profile to an available profile and update requested equipment specifications. Verify employee/onboarding information is not editable, mandatory values are enforced, the existing request ID is preserved, no duplicate is created, and the update is confirmed.
5. **Edit ineligible statuses**: Open requests in Ready and Rejected. Verify the Edit action is unavailable and request details remain unchanged.
6. **Invalid details**: Attempt to save an eligible request with a missing mandatory value or an unavailable profile. Verify validation is displayed and the request ID and existing details remain unchanged.
7. **Update history**: Successfully update request details. Verify the update date/time and responsible administrator are recorded and the previous request information remains available in history.
8. **Stale detail save**: Have two administrators open the same eligible request. Save a detail change from the first administrator, then attempt to save the second administrator's stale edit. Verify the second save is rejected with a reload instruction and the first administrator's saved change remains intact.
9. **Status updates**: Select each of Pending, Approved, In Progress, Ready, and Rejected on an appropriate request. Verify each selected status is saved; provide a reason when selecting Rejected. Detail-edit eligibility must not impose additional status-transition restrictions.
10. **Rejection without a reason**: Select Rejected without a reason. Verify the update is prevented and the request remains unchanged. Supply a reason and retry; verify the rejection is saved and its reason is visible.
11. **Ready timestamp and manager visibility**: With prepared equipment, mark a request Ready. Verify the status update date and time are recorded and the manager can see the updated status.
12. **Manager cannot update**: View one of the manager's own requests and attempt to change its details or status. Verify the manager can view the request but cannot change it.
13. **Authorization**: Verify only authorized IT administrators can manage requests, edit eligible details, and change statuses; managers can see only their own submitted requests.

## Expected outcome

The observable behavior matches [the UI contract](./contracts/laptop-request-management-ui.md) and entity relationships in [the data model](./data-model.md). Record the target application's setup, run, and test commands here when its repository is identified; they cannot be supplied from this Spec Kit repository.
