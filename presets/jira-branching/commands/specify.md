## Jira feature naming

Apply these instructions before the pre-execution checks below. They augment
the standard workflow; do not skip its hooks, template resolution, or
specification steps.

1. Look for Jira issue keys in the user's feature description. A key consists
   of a project key beginning with a letter, followed by letters or digits,
   a hyphen, and one or more digits (for example `PROJ-123`). Match keys
   case-insensitively and normalize the selected key to uppercase.
2. If there are multiple distinct keys, ask the user which one identifies the
   feature before doing anything that changes files or branches. If there is
   no key, use the standard workflow below without setting Jira overrides.
3. For a single selected key, derive one concise 2-4 word lowercase,
   hyphen-separated short name using letters and digits from the feature
   description, excluding the issue key. If the description does not provide
   enough information to derive a meaningful name, ask for a feature
   description.
4. Treat the following as explicitly supplied values for this invocation:
   - `GIT_BRANCH_NAME=feature/<KEY>-<short-name>`
   - `SPECIFY_FEATURE_DIRECTORY=specs/<KEY>-<short-name>`
   - `SPECIFY_FEATURE=feature/<KEY>-<short-name>`
   Use the same key and short name in all three. Do not use a stale value from
   an earlier invocation. If the user also supplied a conflicting explicit
   override, ask which value to use before changing anything.
5. Before creating a branch, verify that Git is available, that the Git
   `before_specify` hook is enabled and executable, and that the branch name
   is valid and at most 244 UTF-8 bytes. Stop with an error if any check fails.
   Check whether the target spec directory already exists. If it does, stop
   and ask how to proceed; never overwrite it.
   The standard Git hook must receive `GIT_BRANCH_NAME` as an environment
   variable in the same process that runs its branch creation script. If the
   hook fails or the current branch does not match the selected branch after
   the hook, stop instead of creating a specification on the wrong branch.
6. Pass the selected `SPECIFY_FEATURE_DIRECTORY` as the explicit directory to
   the standard workflow below. The standard workflow creates the spec and
   persists the directory in `.specify/feature.json`. Do not assume environment
   variables set by a child process survive into later tool calls.
