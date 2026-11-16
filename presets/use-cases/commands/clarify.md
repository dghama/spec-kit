## Clarify the linked use case

Before any hook or prerequisite step below, run
`.\scripts\resolve-feature-context.ps1` from the repository root and check its
exit status. Stop on failure; never use an old `.specify/feature.json`.
On a branch that does not match `feature/<JIRA-ID>-<short-name>`, ask the user
to select an existing `specs/<JIRA-ID>-<short-name>` directory explicitly,
then run the resolver with `-FeatureDirectory` and the selected value. A
previous pointer or environment variable is not an explicit selection. Do not
silently override conflicting `SPECIFY_FEATURE_DIRECTORY` or `SPECIFY_FEATURE`
environment variables; tell the user to clear or correct them. Run the
resolver again if the branch or selection changes before a subsequent command.
This is an agent instruction; direct script calls do not automatically run it.

After resolving `FEATURE_DIR`, read `FEATURE_DIR/spec.md`. Treat a file
containing the sentence `This feature is specified by` as a use case pointer,
even if its link is malformed. Resolve its relative link from the pointer's
directory and read the entire use case. Stop if the link is missing, ambiguous,
or unreadable. For an older full specification that is not a pointer, follow
the standard command below unchanged.

For a pointer, treat the linked use case as `FEATURE_SPEC` for the
clarification scan and writes below; keep the pointer unchanged. Ask the
Product Owner about missing or ambiguous behavior, record unanswered questions
under Open Questions, and apply actual answers to the relevant use case
sections. Do not turn assumptions into requirements. Adapt any core
user-story/FR/SC or assumptions guidance to the use case format. An Approved
use case must have no open questions: if new questions arise, do not silently
change its status or leave it Approved with open questions; ask the user how
to proceed before writing. Never claim approval without explicit authorization.
