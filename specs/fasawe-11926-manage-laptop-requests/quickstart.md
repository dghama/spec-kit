# Quickstart: Validate Laptop Request Management

This guide is technology-agnostic because the application repository and stack have not been identified. Run these scenarios in the target application once its environment and test commands are known.

## Prerequisites

- An authorized IT administrator account and a manager account.
- Submitted laptop requests linked to employees, onboarding records, and selected laptop profiles.
- Requests in multiple statuses, including at least one request that can be used to verify rejection and Ready updates.
- Equipment prepared for any request used in the Ready scenario.
- The target application's documented setup and test/run commands (not available in this repository).

## Scenarios

1. **Request list and ordering**: Open the management view as an IT administrator. Verify the list shows employee name, start date, requested profile, submission date, and status, with the most recently submitted request first.
2. **Search and filter**: Search by an employee name and filter by a status. Verify the displayed requests match the active search or filter.
3. **Request details**: Open a request. Verify employee information, selected profile, linked onboarding record, list values, and any rejection reason are displayed.
4. **Status updates**: Select each of Pending, Approved, In Progress, Ready, and Rejected on an appropriate request. Verify each selected status is saved; provide a reason when selecting Rejected.
5. **Rejection without a reason**: Select Rejected without a reason. Verify the update is prevented and the request remains unchanged. Supply a reason and retry; verify the rejection is saved and its reason is visible.
6. **Ready timestamp and manager visibility**: With prepared equipment, mark a request Ready. Verify the status update date and time are recorded and the manager can see the updated status.
7. **Manager cannot update status**: View one of the manager's own requests and attempt to change its status. Verify the manager can view the request but cannot change it.
8. **Authorization**: Verify only authorized IT administrators can manage requests and change statuses.

## Expected outcome

The observable behavior matches [the UI contract](./contracts/laptop-request-management-ui.md) and entity relationships in [the data model](./data-model.md). Record the target application's setup, run, and test commands here when its repository is identified.
