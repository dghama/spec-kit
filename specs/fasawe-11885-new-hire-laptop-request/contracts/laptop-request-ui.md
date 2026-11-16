# UI Contract: Laptop Request for a New Hire

This contract describes required interaction behavior from UC-11885, not visual layout. No approved mockup exists; the eventual implementation should follow the target application's existing form conventions.

## Manager flow

1. The manager can open the laptop request form for a new hire.
2. The manager can select or identify a new hire with an existing onboarding record.
3. The form displays the employee's first name, last name, and start date.
4. The form displays each available laptop profile's name and key specifications and allows the manager to select a profile.
5. The manager can submit the request after providing required information.
6. On success, the system creates a request linked to that new hire and profile with status Pending, makes it accessible to IT, and displays a confirmation.

## Rejection behavior

- If required information is missing, submission is prevented, no request is created, and the manager can correct the information and retry.
- If an active request already exists for the same new hire, another request is not created. The existing request remains unchanged.
- Active requests include Pending and every in-progress state. The exact named in-progress states are unresolved and must be confirmed before implementing the duplicate check.

## Not specified

- Page layout, control labels, visual styling, and interaction patterns beyond the behaviors above.
- API endpoints, request/response payloads, and persistence schema.
- The exact names of in-progress request statuses.
