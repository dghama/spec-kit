# Tasks: Request a Laptop for a New Hire

**Input**: Design documents in `specs/fasawe-11885-new-hire-laptop-request/`

**Prerequisites**: `plan.md`, `spec.md`, `research.md`, `data-model.md`, `contracts/`, `quickstart.md`

**Scope**: Readiness tasks only, as requested. This repository has no application source tree, and the target application repository/stack has not been identified. These tasks make the feature ready for implementation without inventing code paths. The unresolved in-progress status names remain a Product Owner decision.

**Organization**: The authoritative use case defines a goal and flows, not prioritized user stories. Tasks are therefore grouped by setup, the main success scenario, and the two alternative flows. No user-story IDs or priorities are invented.

## Phase 1: Setup

**Purpose**: Identify the application target so implementation paths and tools can be specified from evidence.

- [ ] T001 Obtain the target application repository, language/framework, and existing source, test, and documentation conventions; record the repository and concrete project structure in `specs/fasawe-11885-new-hire-laptop-request/plan.md`.

**Checkpoint**: The target application and its established conventions are recorded before application-specific work is planned.

---

## Phase 2: Foundational

**Purpose**: Resolve blocking product and application-context questions before preparing implementation-specific work.

- [ ] T002 [P] Ask the Product Owner which exact request statuses besides Pending count as in-progress for duplicate prevention, then record the decision in `docs/use-cases/UC-11885-new-hire-laptop-request.md`.
- [ ] T003 Map the target application's existing onboarding employee, laptop profile, and request entities and their concrete source paths into `specs/fasawe-11885-new-hire-laptop-request/data-model.md`.
- [ ] T004 Identify the target application's test runner, test locations, setup prerequisites, and runnable commands; record them in `specs/fasawe-11885-new-hire-laptop-request/quickstart.md`.

**Checkpoint**: T001–T004 provide the product decision and application paths needed to create implementation tasks. T003 and T004 depend on T001; T002 is independent.

---

## Phase 3: Main Success Scenario — Submit a Laptop Request

**Goal**: Map the manager's successful request flow to the target application's existing UI, request handling, and validation conventions.

**Independent validation criteria**: A manager can identify an onboarded new hire, see first name, last name, and start date, select an available profile shown with its name and key specifications, submit, and observe a linked Pending request available to IT plus confirmation.

- [ ] T005 Map the manager form and profile-selection behavior to concrete target UI paths and conventions in `specs/fasawe-11885-new-hire-laptop-request/contracts/laptop-request-ui.md`.
- [ ] T006 Map request creation, new-hire/profile linkage, initial Pending status, and IT visibility to concrete target application paths in `specs/fasawe-11885-new-hire-laptop-request/data-model.md`.
- [ ] T007 Add a runnable successful-submission validation scenario using the discovered test command and test locations in `specs/fasawe-11885-new-hire-laptop-request/quickstart.md`.

---

## Phase 4: Alternative Flow A1 — Required Information Is Missing

**Goal**: Map the missing-information behavior to existing validation and test conventions.

**Independent validation criteria**: A submission missing mandatory employee information or a laptop profile creates no request; the manager can correct the information and retry.

- [ ] T008 Map required-field validation, no-request-on-failure, and retry behavior to concrete target UI/test paths; record the validation scenario in `specs/fasawe-11885-new-hire-laptop-request/contracts/laptop-request-ui.md` and `specs/fasawe-11885-new-hire-laptop-request/quickstart.md`.

---

## Phase 5: Alternative Flow A2 — An Active Request Already Exists

**Goal**: Map duplicate prevention to the confirmed active statuses and target application conventions.

**Independent validation criteria**: For a new hire with an existing Pending or confirmed in-progress request, another submission creates no request and leaves the existing request unchanged.

- [ ] T009 After T002, map the exact active-status set and duplicate check to concrete target application/test paths; update `specs/fasawe-11885-new-hire-laptop-request/data-model.md`, `specs/fasawe-11885-new-hire-laptop-request/contracts/laptop-request-ui.md`, and `specs/fasawe-11885-new-hire-laptop-request/quickstart.md`.

---

## Phase 6: Polish and Implementation Handoff

**Purpose**: Keep the planning artifacts consistent and generate implementation tasks only after blockers are resolved.

- [ ] T010 Review `specs/fasawe-11885-new-hire-laptop-request/plan.md`, `specs/fasawe-11885-new-hire-laptop-request/data-model.md`, `specs/fasawe-11885-new-hire-laptop-request/contracts/laptop-request-ui.md`, and `specs/fasawe-11885-new-hire-laptop-request/quickstart.md` against the authoritative use case; preserve its Out of Scope items and flag any remaining Product Owner decision.
- [ ] T011 Once T001–T010 are complete, regenerate `specs/fasawe-11885-new-hire-laptop-request/tasks.md` in the target application context with concrete implementation and focused test tasks for the success, missing-information, and duplicate-request flows.

---

## Dependencies and Execution Order

### Phase Dependencies

- **Setup (Phase 1)**: T001 starts immediately and blocks application-specific mapping.
- **Foundational (Phase 2)**: T002 can run independently. T003 and T004 depend on T001. Complete the foundational tasks before flow mapping.
- **Main Success Scenario (Phase 3)**: T005 and T006 depend on T001 and T003; T007 depends on T004–T006.
- **A1 (Phase 4)**: T008 depends on T001, T004, and T005.
- **A2 (Phase 5)**: T009 depends on T002–T004.
- **Polish/Handoff (Phase 6)**: T010 depends on T005–T009. T011 depends on all prior readiness tasks and the resolution of their blockers.

### Parallel Opportunities

- T001 and T002 can proceed in parallel: one establishes the application target; the other obtains the Product Owner's active-status decision.
- After T001, T003 and T004 can proceed in parallel because they update separate planning artifacts.
- Once their prerequisites are complete, T005 and T006 can be mapped independently to separate artifacts.
- A1 and A2 validation mapping can proceed in parallel after the relevant foundational details and status decision are available.

### Parallel Example: Foundational Mapping

```text
Task: Map application entities and source paths in specs/fasawe-11885-new-hire-laptop-request/data-model.md (T003)
Task: Record test runner, test locations, and commands in specs/fasawe-11885-new-hire-laptop-request/quickstart.md (T004)
```

## Implementation Strategy

This list intentionally covers readiness only. The MVP implementation scope is the main success scenario, with A1 and A2 required for the complete use case. Do not start implementation from this repository's current context: the application target and named in-progress statuses are unresolved. After those inputs and the concrete paths are documented, regenerate the task list in the application context with implementation, focused tests, and documentation updates.
