# Goragit

The ultimate Git workflow, _not for people who cannot use Git properly._

[See in action](https://github.com/narze/goragit/commits/main)

## Prerequisites

- [Generate](https://github.com/settings/tokens/new) GitHub Personal Access Token (PAT) with `repo` scope
- Create repo secret e.g. `GH_TOKEN_WITH_REPO_SCOPE` using generated PAT
- Big Ego

## Usage

```yaml
name: Goragitize
on:
  push:
    branches: [main]
jobs:
  job:
    runs-on: ubuntu-latest
    
    steps:
      - uses: actions/checkout@v3
        with:
          # These options must be set
          fetch-depth: 0
          persist-credentials: false

      - uses: narze/goragit@main
        with:
          author_name: your-github-username
          author_email: your-email@example.com
          github_token_with_repo_scope: ${{ secrets.GH_TOKEN_WITH_REPO_SCOPE }}
          i_understand_that_this_workflow_will_goragodize_my_repo: true
          keep_git_history_in_message: false # Optional
```

## Options

- `author_name` Git commit author name (Default: `github-actions`)
- `author_email` Git commit author email (Default: `github-actions@noreply.github.com`)
- `github_token_with_repo_scope` [required] GitHub Personal Access Token (PAT) with Repo scope. See Prerequisites on how to setup.
- `i_understand_that_this_workflow_will_goragodize_my_repo` [required] You must accept this power.
- `keep_git_history_in_message` If true, your commit message will be prepended to the previous commit messages.
