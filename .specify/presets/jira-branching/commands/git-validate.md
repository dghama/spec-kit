## Jira feature branch validation

Before applying the standard validation below, inspect the current Git branch
(or `SPECIFY_FEATURE` when Git is unavailable). If it matches
`feature/<KEY>-<short-name>`, where `<KEY>` is an uppercase Jira project key
followed by a hyphen and digits, and `<short-name>` is a nonempty lowercase
hyphen-separated name:

- Report that the branch is valid.
- Check for `specs/<KEY>-<short-name>` and report whether it exists.
- Stop; do not apply the numeric/timestamp validation below to this branch.

For all other branch names, apply the standard validation below unchanged.

