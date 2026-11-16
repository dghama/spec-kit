## Linked use case is the specification

After resolving `FEATURE_DIR` and before using feature requirements, read
`FEATURE_DIR/spec.md`. Treat a file containing `This feature is specified by`
as a use case pointer, even if its link is malformed. Resolve its relative link
from the pointer file's directory and read the complete linked use case.
If the link is missing, ambiguous, or unreadable, stop and report the problem;
do not infer the use case from its filename or proceed from the pointer alone.
For older full specifications that are not pointers, follow the standard
command below unchanged.

For a pointer, the use case is the authoritative specification: wherever the
standard command refers to spec content, stories, requirements, acceptance
scenarios, or the specification as a source of intent, use the linked use
case's goal, flows, preconditions, postconditions, business rules, scope, and
open questions instead. Do not require absent FR/SC IDs or invent user stories,
priorities, decisions, or requirements to fit the core format. Organize work
around the evidenced goal and flows; distinguish derived technical work from
Product Owner decisions. Report unresolved questions and never present
unsupported assumptions as approved requirements. Respect Out of Scope.
The standard constitution, plan, task, checklist, and hook rules still apply.
Do not modify the use case or pointer during read-only commands.

On Windows, if `python3` is an unusable Microsoft Store alias, find a working
Python 3 executable with PyYAML and set `SPECKIT_PYTHON_EXECUTABLE` in each
process running a Spec Kit resolver or setup script. Report missing Python or
PyYAML instead of bypassing template composition.
