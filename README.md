# Agent Skills

Reusable development workflows, distributed as the `seachicken` plugin.

## Skills

- `seachicken:change-understanding`: assess understanding of a code change through questions grounded in the diff.

## Use in a repository

Copy `.agents/plugins/marketplace.json` into the consuming repository at the same path. It references this GitHub repository and requests default installation from `main`.

Add this to the consuming repository's `.codex/config.toml`:

```toml
[plugins."seachicken@seachicken"]
enabled = true
```

Project configuration requires a trusted project and a client that supports local plugin marketplaces. Restart or refresh the client after adding the configuration. The GitHub source must be pushed and accessible before installation can succeed.

To require the understanding check in the assistant's commit workflow, add this to the consuming repository's `AGENTS.md`:

```markdown
Before every commit, use the `seachicken:change-understanding` skill. Commit only after the user scores 100 and relevant checks pass, unless the user explicitly waives the quiz.
```

Default installation does not enforce execution or restrict manual Git commits.
