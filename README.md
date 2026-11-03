# gh-cpr

A GitHub CLI extension that creates a branch and an empty commit from your current branch, creates a self-assigned draft pull request, and opens it in your browser.

## Installation

Requires [GitHub CLI](https://cli.github.com/) and Git. Authenticate with `gh auth login` first.

```sh
gh extension install c19yamamoto/gh-cpr
```

To install the development version from this repository:

```sh
gh extension install .
```

## Usage

```sh
gh cpr <new-branch> <pr-title>

# When run from develop, create a PR targeting develop.
gh cpr feat/add-search "Add search"
```

1. Record the current branch as the PR's base branch.
2. Create and switch to a new branch with the specified name.
3. Create an empty commit using the PR title as its message.
4. Create a draft PR assigned to you.
5. Open the PR in your browser.

Prompts for the PR body and where to push the branch follow the standard `gh pr create` behavior.
Working tree and staged changes are excluded from the empty commit and carried over to the new branch.
The command cannot run with an existing branch name, a detached HEAD, or a repository without an initial commit.

If a step fails, the command stops. Any branch or commit already created remains in place. Resolve the issue and continue with `gh pr create` or `gh pr view --web` as appropriate.

```sh
gh cpr --help
```
