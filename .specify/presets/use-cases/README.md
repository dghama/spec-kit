# Use case specifications preset

Install this preset alongside the Jira branching preset from the repository root:

```powershell
specify preset add --dev .\presets\use-cases
```

`/speckit-specify PROJ-123 Add user authentication` creates a use case such as
`docs/use-cases/UC-123-user-auth.md` and keeps only a relative link in
`specs/PROJ-123-user-auth/spec.md`. The use case is the authoritative source;
planning, clarification, tasks, analysis, checklists, implementation, and
convergence read it through the pointer. Existing full `spec.md` files keep
their normal behavior.

The Jira issue number supplies the UC number, padded to at least three digits.
When there is no Jira issue or the number is already in use (including by
another Jira project), the workflow asks for an unused number. Unsupported
assumptions belong in Open Questions for the Product Owner. New use cases are
Draft; approval is explicit and requires an empty Open Questions section.
Use `/speckit-clarify` to update an existing linked use case.

Before feature-scoped commands, the agent runs
`.\scripts\resolve-feature-context.ps1`. On a branch such as
`feature/PROJ-123-user-auth`, it verifies `specs/PROJ-123-user-auth/spec.md`
and updates the checkout-local `.specify/feature.json`. It stops on missing
paths or conflicting `SPECIFY_FEATURE_DIRECTORY` / `SPECIFY_FEATURE` values.
Clear those variables if they refer to a different feature. The resolver also
stops when `SPECIFY_FEATURE_NO_PERSIST` is enabled rather than writing state.

On app-managed or other nonmatching branches, select a feature explicitly:

```powershell
.\scripts\resolve-feature-context.ps1 -FeatureDirectory 'specs/PROJ-123-user-auth'
```

The agent must ask for that selection when running a feature-scoped command.
The resolver does not run on checkout, for `/speckit-specify` when creating a
new feature, or for direct calls to Spec Kit scripts. Direct callers must run
it themselves first. Avoid running commands for different features at the
same time in one checkout because they share `feature.json`.

The standard PowerShell template resolver requires Python 3 and PyYAML. If
Windows resolves `python3` to a nonfunctional Microsoft Store alias, set
`$env:SPECKIT_PYTHON_EXECUTABLE` to the path of a working Python executable
with PyYAML in the process running the resolver or setup script.

The source preset is separate from generated skills and the installed copy.
After editing it, regenerate with:

```powershell
specify preset update use-cases --dev .\presets\use-cases
```

The update command removes the installed preset before reinstalling, so check
the source and back up any edits to the installed copy first. After a Spec Kit
upgrade or reinitialization, inspect the generated skills and regenerate if
necessary. Composition reduces conflicts but does not guarantee future
compatibility. These are agent instructions, not a programmatic enforcement
mechanism; review generated artifacts before approval.
