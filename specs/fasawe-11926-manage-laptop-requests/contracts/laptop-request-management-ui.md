# UI Contract: Laptop Request Management

This contract describes required interaction behavior from UC-11926, not visual layout. No approved mockup is referenced; the implementation should follow the target application's existing conventions.

## IT administrator flow

1. An authorized IT administrator opens the laptop request management view.
2. The system shows submitted requests with the employee's name, start date, requested laptop profile, submission date, and current status, sorted by submission date with the most recent first.
3. The IT administrator may filter the list by status or search by employee name. The displayed list reflects the selected filter or search.
4. The IT administrator opens a request.
5. The system displays the employee information, selected laptop profile, onboarding record, all values shown in the list, and any rejection reason.
6. If the request is Pending, Approved, or In Progress, the IT administrator may edit its details. The administrator may change the laptop profile to an available profile and update requested equipment specifications. Employee and onboarding information are not editable through this flow.
7. The system validates mandatory values and the selected profile before saving. Invalid details prevent the update and leave the existing request unchanged.
8. A successful detail update changes the existing request without creating a duplicate, preserves the request ID, records the update date/time and administrator, retains prior request information in update history, and confirms the update.
9. If the request changed after the administrator began editing, the system rejects the stale save and asks the administrator to reload the latest request. The other administrator's saved changes remain intact.
10. The IT administrator may select Pending, Approved, In Progress, Ready, or Rejected as the request status. Any listed status may be selected; detail-edit eligibility does not restrict status selection.
11. When Rejected is selected, the IT administrator must provide a rejection reason. Without one, the update is prevented and the request remains unchanged.
12. When Ready is selected, the system records the date and time of that status update. Equipment must be prepared before this status is selected.
13. The system saves a valid status update, and the manager can see the updated status.

## Detail edit availability

- Offer the Edit action only for Pending, Approved, and In Progress requests.
- Do not offer the Edit action for Ready or Rejected requests. Viewing the request and using the existing status-management flow remain available.
- Do not permit edits to employee information or information linked to the onboarding record.
- No specific conflict-resolution UI, storage version field, or persistence mechanism is prescribed beyond rejecting stale saves and requiring reload.

## Manager access

- A manager can view their own submitted request and its current status.
- A manager cannot modify request details or status.

## Not specified

- Page layout, control labels, visual styling, and interaction patterns beyond the behaviors above.
- API endpoints, request/response payloads, and persistence schema.
- Status-transition restrictions beyond the listed statuses and the Ready and Rejected rules.
- The concrete set of requested equipment specification fields, beyond their being editable and subject to mandatory-value validation.
