# Use Case Quality Checklist: Manage Laptop Requests for New Hires

**Purpose**: Validate the linked use case for completeness and readiness before planning
**Created**: 2026-11-16
**Feature**: [spec.md](../spec.md)
**Authoritative Use Case**: [UC-11926-manage-laptop-requests.md](../../../docs/use-cases/UC-11926-manage-laptop-requests.md)

## Structure and Evidence

- [x] Required use-case sections are populated using the composed use-case template
- [x] Actor, goal, preconditions, and postconditions are grounded in FASAWE-11926
- [x] The existing manager-submission use case is identified as a dependency
- [x] Status remains Draft; no approval is claimed
- [x] No implementation details or unsupported UI links are included

## Acceptance-Criteria Coverage

- [x] AC1: Request list fields and most-recent-first ordering are specified
- [x] AC2: Request details and onboarding-record linkage are specified
- [x] AC3: Status updates and the available statuses are specified
- [x] AC4: A rejection reason is required and visible
- [x] AC5: Ready status, preparation condition, update date/time, and manager visibility are specified
- [x] AC6: Status filtering and employee-name search are specified
- [x] AC7: IT administrator access and manager status restrictions are specified
- [x] Alternative flows describe rejected updates without a reason and manager status restrictions

## Product Decisions and Open Questions

- [x] Status-selection behavior reflects the Product Owner's answer: any listed status may be selected
- [x] Equipment assignment is excluded according to the Product Owner's answer
- [x] No unresolved Product Owner questions remain based on the provided story and answers

## FASAWE-11886: Update Laptop Request Details

- [x] AC1: IT administrators can access the edit action for eligible requests; managers cannot edit request details
- [x] AC2: Laptop profile changes use an available profile and are validated before saving
- [x] AC3: Editable details are limited to laptop profile and requested equipment specifications; onboarding-linked employee information cannot be changed through the request
- [x] AC4: Mandatory values are validated, successful updates preserve the request ID, and the administrator receives confirmation
- [x] AC5: Successful updates record the date/time and administrator, with prior request information available in update history
- [x] AC6: Detail editing is limited to Pending, Approved, and In Progress requests; Ready and Rejected requests cannot be edited
- [x] AC7: Invalid updates are prevented, validation messages are shown, and existing request information remains unchanged
- [x] Editable field scope reflects the clarification provided: laptop profile and requested equipment specifications only
- [x] No unresolved questions remain for this story based on its acceptance criteria and the field-scope clarification

## Notes

- The use case is Draft and has not been approved. Its current lack of Open Questions does not imply approval.
