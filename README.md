# Actions

Use this repository as a sandbox to test and debug GitHub Actions.

## Tips

- `git commit --allow-empty --message "Empty commit"` to add a commit, even if
  no file changed
- Add `[skip ci]` to the commit message to skip workflow execution
- You can identify which PR is coming from a fork with `github.event_name ==
  'pull_request' && github.event.pull_request.head.repo.fork`


## Gotchas

- Workflows do not run on PRs if the PR can't be merged
- PRs always use the workflow that was defined when they were opened. Updating
  workflows won't update the checks run on the PRs. You need to close those PRs
  and open new ones, or rebase the PRs and force push.
- Skipped job will always be displayed in the GitHub UI. The only way to make
  them completely silent is to somehow configure the workflow to not trigger.

## Triggers

### `on.pull_request`

- Triggered on all PRs, local and from forks
- Executed on the head of the PR
- Local PRs have write access, fork PRs only have read access

### `on.pull_request_target`

- Triggered on all PRs, local and from forks
- Executed on the base of the PR, not the head
- Has full write access to the repository (but should be considered INSECURE,
  and it's your responsibility to checkout or not the PR code)

[Keeping your GitHub Actions and workflows secure Part 1: Preventing pwn
requests](https://securitylab.github.com/research/github-actions-preventing-pwn-requests/)

## Links

- [actionlint](https://github.com/rhysd/actionlint): A linter for workflow files
- [act](https://github.com/nektos/act): A way to run actions locally
