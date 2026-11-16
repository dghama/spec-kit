# spec-kit Constitution

## Core Principles

### I. Tests for Every Change (NON-NEGOTIABLE)
Every change MUST include tests that verify the new or modified behavior, including relevant edge cases and failure paths. Bug fixes MUST include a regression test that fails without the fix. Existing tests MUST pass before a change is considered complete. A change with no testable behavior (for example, a pure documentation edit) MUST state why no test applies.

### II. Documentation for Every Change (NON-NEGOTIABLE)
Every change MUST update the documentation affected by it, such as README, usage guides, configuration references, and feature artifacts under `specs/`. Public interfaces, commands, and configuration options MUST be documented when added or changed. Documentation MUST be updated in the same change as the code, not deferred.

## Development Workflow

- Specs, plans, and task lists MUST include explicit test and documentation tasks for each change.
- Reviews MUST verify that tests and documentation accompany the change before approval.

## Governance

This constitution supersedes other practices. All pull requests and reviews MUST verify compliance with it. Amendments require a documented rationale and a version bump (MAJOR for removed or redefined principles, MINOR for added principles or sections, PATCH for clarifications).

**Version**: 1.0.0 | **Ratified**: 2026-11-16 | **Last Amended**: 2026-11-16
