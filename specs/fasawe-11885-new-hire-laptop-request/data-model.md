# Data Model: Request a Laptop for a New Hire

This is a behavior-level model derived from UC-11885. It does not prescribe database tables, field types, or persistence technology.

## Entities

### New Hire

An employee with an existing onboarding record.

| Attribute | Meaning | Validation / behavior |
|---|---|---|
| First name | Employee first name | Display on the request form. |
| Last name | Employee last name | Display on the request form. |
| Start date | Employee's first working date | Display on the request form. |
| Onboarding record | Existing record identifying the employee | Must exist for the request to be submitted. |

### Laptop Profile

A configured profile available for managers to select.

| Attribute | Meaning | Validation / behavior |
|---|---|---|
| Profile name | Human-readable profile name | Display for each available profile. |
| Key specifications | Summary of the profile's key specifications | Display with the profile name. |
| Availability | Whether the profile can currently be selected | Only available profiles may be selected. |

### Laptop Request

A request for equipment linked to a new hire and a selected laptop profile.

| Attribute | Meaning | Validation / behavior |
|---|---|---|
| New hire | The employee receiving the laptop | Required; must reference an existing onboarding record. |
| Laptop profile | The requested profile | Required; must reference an available profile. |
| Status | Request lifecycle state | Set to **Pending** on successful submission. Pending and all in-progress states count as active; exact in-progress names remain a Product Owner decision. |

## Relationships

- Each laptop request references one new hire.
- Each laptop request references one selected laptop profile.
- A new hire may have no more than one active laptop request. Active means Pending or an in-progress state; the named in-progress states are unresolved.
- IT must be able to access successfully submitted requests.

## Validation and state behavior

- Missing required employee information or laptop profile prevents creation.
- A duplicate active request for the same new hire prevents creation; the existing request remains unchanged.
- Successful creation links the new hire and profile, sets status to Pending, makes the request available to IT, and confirms submission to the manager.
- Further request lifecycle transitions and IT processing are out of scope.
