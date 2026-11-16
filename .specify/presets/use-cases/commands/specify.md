## Authoritative use case workflow

These instructions override conflicting instructions in the standard command
below, but retain its pre- and post-hooks, feature directory resolution,
feature.json persistence, and completion reporting. Apply the Jira naming preset
too when installed; decide the use case ID before any branch or file changes.

- A new feature has one authoritative use case under
  `docs/use-cases/UC-NNN-<slug>.md` and a pointer at `FEATURE_DIR/spec.md`.
  The slug is a concise lowercase hyphenated goal name. Use the same slug as
  the feature short name when the Jira naming preset selects one.
- Derive the numeric part of `UC-NNN` from the selected Jira issue number,
  preserving its numeric value and padding to at least three digits
  (`PROJ-7` becomes `UC-007`; larger numbers are not truncated). If no Jira
  issue was selected, ask the user for a numeric UC ID. Scan all existing
  `docs/use-cases/UC-<number>-*.md` files by numeric ID, not just filename.
  If that ID is already in use, ask the user for a different unused numeric
  ID; do not overwrite or silently renumber. Use `/speckit-clarify` to
  update an existing linked use case instead of creating a new feature.
- Resolve `use-case-template` using the project's standard template resolver
  and use the composed template as the use case structure. Stop if resolution
  fails. On Windows, if `python3` is an unusable Microsoft Store alias, find
  a working Python 3 executable with PyYAML and set
  `SPECKIT_PYTHON_EXECUTABLE` in each process that runs a Spec Kit resolver or
  setup script. Report a missing Python or PyYAML dependency instead of
  bypassing composition. Fill the use case from evidence and Product Owner
  answers; never invent facts,
  requirements, UI links, Jira stories, business rules, or guarantees.
  Place unsupported assumptions and unresolved decisions in Open Questions
  addressed to the Product Owner. Ask targeted questions where possible;
  leave unanswered questions in the use case rather than guessing.
- Create use cases with status `Draft`. Allowed statuses are Draft, Reviewed,
  Approved, Implemented, Tested, Done, and Obsolete. Do not claim Product
  Owner approval or change status without explicit authorization. Open
  Questions must be empty before setting status to Approved.
- Write the populated use case, not its requirements, to the use case file.
  Resolve `spec-template` with the standard resolver and write its pointer
  content to `FEATURE_DIR/spec.md`, substituting the actual filename and a
  relative link calculated from the spec file's directory. Verify the link
  resolves to the created use case. Do not duplicate use case content in
  `spec.md`. Preserve existing spec or use case files unless the user
  explicitly requests an update; do not overwrite either on a new feature.
- Treat the linked use case as `SPEC_FILE` for specification writing,
  clarification, and quality validation. The pointer remains
  `FEATURE_DIR/spec.md` for Spec Kit's prerequisite scripts. Ignore the core
  command's required user-story/FR/SC sections, assumptions-as-facts guidance,
  and instruction to write the full spec into `FEATURE_DIR/spec.md`; they
  conflict with this format. Validate the use case's own sections, flows,
  business rules, and unresolved questions, and report missing evidence.
  A Draft with open questions is not Approved.
- Keep any requirements quality checklist linked to the use case; do not mark
  unresolved criteria as passing. Report both the pointer and use case paths
  and any outstanding Product Owner questions.
