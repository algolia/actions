# Actions

Use this repository as a sandbox to test and debug GitHub Actions.

## Tips

- `git commit --allow-empty --message "Empty commit"` to add a commit, even if
  no file changed
- Add `[skip ci]` to the commit message to skip workflow execution
- Workflows do not run on PR if the PR can't be merged

## Triggers

### `on.pull_request`

- Triggered on all local PRs, not PRs from forks
- Executed on the head of the PR
- Has full write access to the repository

### `on.pull_request_target`

- Triggered on all PRs, including PRs from forks
- Executed on the base branch of the PR, not the head
- Has full write access to the repository
- Should be considered INSECURE by default, as it allow potential execution of
  untrusted external code

[Keeping your GitHub Actions and workflows secure Part 1: Preventing pwn
requests](https://securitylab.github.com/research/github-actions-preventing-pwn-requests/)

## Links

- [actionlint](https://github.com/rhysd/actionlint): A linter for workflow files
- [act](https://github.com/nektos/act): A way to run actions locally
