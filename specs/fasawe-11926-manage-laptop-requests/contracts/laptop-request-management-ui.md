# UI Contract: Laptop Request Management

This contract describes required interaction behavior from UC-11926, not visual layout. No approved mockup is referenced; the implementation should follow the target application's existing conventions.

## IT administrator flow

1. An authorized IT administrator opens the laptop request management view.
2. The system shows submitted requests with the employee's name, start date, requested laptop profile, submission date, and current status, sorted by submission date with the most recent first.
3. The IT administrator may filter the list by status or search by employee name. The displayed list reflects the selected filter or search.
4. The IT administrator opens a request.
5. The system displays the employee information, selected laptop profile, onboarding record, all values shown in the list, and any rejection reason.
6. The IT administrator selects Pending, Approved, In Progress, Ready, or Rejected. Any listed status may be selected.
7. When Rejected is selected, the IT administrator must provide a rejection reason. Without one, the update is prevented and the request remains unchanged.
8. When Ready is selected, the system records the date and time of that status update. Equipment must be prepared before this status is selected.
9. The system saves a valid status update, and the manager can see the updated status.

## Manager access

- A manager can view their own submitted request and its current status.
- A manager cannot modify the request status.

## Not specified

- Page layout, control labels, visual styling, and interaction patterns beyond the behaviors above.
- API endpoints, request/response payloads, and persistence schema.
- Status-transition restrictions beyond the listed statuses and the Ready and Rejected rules.
