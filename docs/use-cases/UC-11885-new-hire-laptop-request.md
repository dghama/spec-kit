# Use Case: Request a Laptop for a New Hire

## Overview

**Use Case ID:** UC-11885

**Use Case Name:** Request a laptop for a new hire

**Primary Actor:** Manager

**Goal:** Submit a laptop request linked to a new hire so the required equipment is ready on the employee's first working day.

**Status:** Draft

**Jira:** [FASAWE-11885 — Request a Laptop for a New Hire](https://mobelite.atlassian.net/browse/FASAWE-11885)

**UI:** No mockup or UI link was provided in the Jira issue.

## Preconditions

- The new hire has an onboarding record.
- Laptop profiles are configured and available for selection.
- The manager can access the laptop request form during onboarding.
- The IT team can access submitted laptop requests.

## Main Success Scenario

1. The manager opens the laptop request form for a new hire.
2. The manager selects or identifies the new hire.
3. The system displays the employee's first name, last name, and start date.
4. The manager selects an available laptop profile.
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

The manager must select an available laptop profile before the request can be submitted.

### BR-003: Required information

The system validates mandatory information and prevents submission when it is missing.

### BR-004: Duplicate active requests

The system prevents more than one active laptop request for the same new hire.

### BR-005: Initial request status

A successfully submitted laptop request is created with status **Pending**.

## Out of Scope

- Creating or maintaining employee onboarding records.
- Configuring or maintaining laptop profiles.
- IT request processing, laptop procurement, assignment, or delivery after submission.

## Open Questions

- Which request statuses count as **active** for duplicate prevention?
- What information about each laptop profile should managers see when choosing one?
- Is there an approved form mockup or UI reference?
- The Jira issue's listed child tasks concern Android sign-in rather than laptop requests. Are those child tasks unrelated or linked to this story in error?
