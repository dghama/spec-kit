# Quickstart: Validate New-Hire Laptop Requests

This guide is technology-agnostic because the application repository and stack have not been identified. Run these scenarios in the target application once its environment and test commands are known.

## Prerequisites

- A manager account with access to the laptop request form.
- A new hire with an existing onboarding record, including first name, last name, and start date.
- At least one available laptop profile with a name and key specifications.
- Access as an IT user to verify submitted requests.
- The application's documented setup and test/run commands (not available in this repository).

## Scenarios

1. **Successful submission**: Select the new hire and an available profile, submit, and verify a linked request with status Pending is available to IT, while the manager sees confirmation.
2. **Required information missing**: Omit required employee information or the laptop profile and submit. Verify submission is prevented and no request is created; provide the missing information and verify retry is possible.
3. **Duplicate active request**: With an active laptop request for the same new hire, submit another request. Verify no second request is created and the existing request is unchanged. Active includes Pending and all in-progress states; the exact named in-progress statuses must be resolved before this scenario can be fully enumerated.
4. **Profile presentation and selection**: Verify available profiles show their names and key specifications and that a profile must be selected before successful submission.

## Expected outcome

The observable behavior matches [the UI contract](./contracts/laptop-request-ui.md) and entity relationships in [the data model](./data-model.md). Record the target application's setup, run, and test commands here when its repository is identified.
