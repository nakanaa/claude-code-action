# Fork: nakanaa/claude-code-action

Personal fork of [anthropics/claude-code-action](https://github.com/anthropics/claude-code-action).

## Why This Fork

The upstream action always creates feature branches for issues, requiring manual PR creation or merge. This fork adds flexible workflow options.

## Modifications

### `commit_mode` Input

Controls how commits are handled for issues:

| Mode      | Behavior                                                |
| --------- | ------------------------------------------------------- |
| `link`    | Create branch, show PR creation link (upstream default) |
| `auto_pr` | Create branch, automatically create PR                  |
| `direct`  | Commit directly to main/base branch, no PR              |

**⚠️ Direct Mode Limitations:**

- Will fail if pushing to a protected branch (e.g., `main` with branch protection rules)
- No pre-check for branch protection - failure occurs during execution
- Uses `--depth=1` fetch which may limit git history analysis tasks

## Syncing with Upstream

```bash
git remote add upstream https://github.com/anthropics/claude-code-action.git
git fetch upstream
git merge upstream/main
# Resolve conflicts in modified files
```

## Usage

```yaml
- uses: nakanaa/claude-code-action@main
  with:
    commit_mode: "direct" # or 'auto_pr' or 'link'
    # ... other inputs
```
