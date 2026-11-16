## Authoritative use case workflow

These instructions override conflicting instructions in the standard command
below, but retain its pre- and post-hooks, feature directory resolution,
feature.json persistence, and completion reporting. Apply the Jira naming preset
too when installed; decide the use case ID before any branch or file changes.

### Updating an existing use case

When the user explicitly asks `/speckit-specify` to update an existing use
case, stay in the specify workflow. "Edit in place" changes the document
target, not the command lifecycle. Do not switch to `/speckit-clarify` or
skip the mandatory `before_specify` hook. These update rules override
conflicting new-feature, Jira directory-naming, and UC-number allocation
instructions; all other naming checks and hooks still apply.

1. Read the requested use case and locate the existing `FEATURE_DIR/spec.md`
   pointer. Resolve its link relative to the pointer's directory and verify
   that it targets the requested use case. If the target is missing or
   ambiguous, stop and ask the user before changing files or branches.
2. Derive `GIT_BRANCH_NAME` from the current Jira story and its short name,
   not from the existing use case's Jira reference or UC ID. Keep
   `SPECIFY_FEATURE_DIRECTORY` set to the existing feature directory;
   preserve its pointer. Set `SPECIFY_FEATURE` to the current story's branch,
   not the existing use case's branch.
   Do not allocate a UC number or create a new use case or feature directory.
   Ask before changing conflicting explicit environment overrides.
3. Execute the enabled mandatory `before_specify` hooks. The Git hook must
   receive `GIT_BRANCH_NAME` in the same process that runs its branch script.
   Stop if the hook is missing, disabled, not executable, or fails. Emitting
   an `EXECUTE_COMMAND` block or loading a hook skill alone is not execution.
4. Before writing any file, and again if the branch changes, verify with Git
   that the current branch exactly matches `GIT_BRANCH_NAME` and that the
   existing pointer still resolves to the requested use case. Stop on any
   mismatch; never edit on `main` as a fallback. Do not replace these checks
   with the new-feature context resolver, which derives a directory from
   the story branch rather than the existing use case.
5. After branch verification, persist the existing feature directory in
   `.specify/feature.json`. Edit only sections affected by the story. Preserve
   the existing use case ID, filename, and item IDs; continue numbering for new items. Retain
   evidence-based writing, clarification questions, quality validation,
   `after_specify` hooks, and completion reporting in this workflow.

### Creating a new use case

- A new feature has one authoritative use case under
  `docs/use-cases/UC-NNN-<slug>.md` and a pointer at `FEATURE_DIR/spec.md`.
  The slug is a concise goal name of one to five lowercase ASCII words,
  hyphen-separated, with accents removed and punctuation omitted. Use this
  exact slug as the feature short name, branch short name, and use-case
  filename suffix. When the Jira naming preset is installed, lowercase the
  Jira key in the branch and feature directory too; for example, use
  `feature/proj-123-user-auth`, `specs/proj-123-user-auth`, and
  `docs/use-cases/UC-123-user-auth.md`. Keep the `UC-` identifier uppercase.
- Derive the numeric part of `UC-NNN` from the selected Jira issue number,
  preserving its numeric value and padding to at least three digits
  (`PROJ-7` becomes `UC-007`; larger numbers are not truncated). If no Jira
  issue was selected, ask the user for a numeric UC ID. Scan all existing
  `docs/use-cases/UC-<number>-*.md` files by numeric ID, not just filename.
  If that ID is already in use, ask the user for a different unused numeric
  ID; do not overwrite or silently renumber. An explicit request to update
  an existing use case follows the update workflow above. Use
  `/speckit-clarify` for a standalone clarification of an existing feature,
  not as a replacement for an invoked `/speckit-specify` lifecycle.
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
