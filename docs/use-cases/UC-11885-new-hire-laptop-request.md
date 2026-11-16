# Use Case: Request a Laptop for a New Hire

## Overview

**Use Case ID:** UC-11885

**Use Case Name:** Request a laptop for a new hire

**Primary Actor:** Manager

**Goal:** Submit a laptop request linked to a new hire so the required equipment is ready on the employee's first working day.

**Status:** Draft

**Jira:** [FASAWE-11885 — Request a Laptop for a New Hire](https://mobelite.atlassian.net/browse/FASAWE-11885)

**UI:** No approved mockup is available. Follow existing form conventions.

## Clarifications

### Session 2026-11-16

- Q: Which requests count as active for duplicate prevention? -> A: Pending and all in-progress states. The exact named in-progress statuses remain unresolved.
- Q: What information should managers see for each laptop profile? -> A: The profile name and key specifications.
- Q: Are the Android sign-in child tasks part of this use case? -> A: No. They are unrelated and linked to this story in error.
- Q: Is there an approved form mockup? -> A: No. Follow existing form conventions.

## Preconditions

- The new hire has an onboarding record.
- Laptop profiles are configured and available for selection.
- The manager can access the laptop request form during onboarding.
- The IT team can access submitted laptop requests.

## Main Success Scenario

1. The manager opens the laptop request form for a new hire.
2. The manager selects or identifies the new hire.
3. The system displays the employee's first name, last name, and start date.
4. The system shows each available laptop profile's name and key specifications, and the manager selects a profile.
5. The manager submits the request.
6. The system validates the required employee information and laptop profile.
7. The system creates a laptop request linked to the new hire with status **Pending**.
8. The system displays a confirmation message.

## Alternative Flows

### A1: Required information is missing

**Trigger:** The system validates the submission at step 6.

**Flow:**

1. The system prevents submission because required information is missing.
2. No laptop request is created. The manager can provide the missing information and submit again.

### A2: An active laptop request already exists

**Trigger:** The system validates the submission at step 6 and finds an active laptop request for the same new hire.

**Flow:**

1. The system prevents submission of a duplicate active request.
2. No additional laptop request is created.

## Postconditions

### Success Postconditions

- A laptop request is linked to the selected new hire.
- The request status is **Pending** and the IT team can access it.
- The manager receives confirmation of submission.

### Failure Postconditions

- A request that fails validation is not created.
- An existing active request remains unchanged when a duplicate submission is blocked.

## Business Rules

### BR-001: New hire information

The request must identify a new hire with an existing onboarding record. The employee's first name, last name, and start date are displayed.

### BR-002: Laptop profile selection

The manager must select an available laptop profile before the request can be submitted. Each profile is shown with its name and key specifications.

### BR-003: Required information

The system validates mandatory information and prevents submission when it is missing.

### BR-004: Duplicate active requests

The system prevents more than one active laptop request for the same new hire. Active requests include **Pending** and all in-progress states. The exact named statuses that count as in-progress remain an Open Question.

### BR-005: Initial request status

A successfully submitted laptop request is created with status **Pending**.

## Out of Scope

- Creating or maintaining employee onboarding records.
- Configuring or maintaining laptop profiles.
- IT request processing, laptop procurement, assignment, or delivery after submission.
- Android sign-in work in the Jira story's child tasks; these tasks are unrelated and linked in error.

## Open Questions

- Which exact named request statuses besides **Pending** count as in-progress for duplicate prevention? This question was skipped and remains unanswered.
