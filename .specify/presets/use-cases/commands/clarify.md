## Clarify the linked use case

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
