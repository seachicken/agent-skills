# Agent Skills

Reusable development workflows. Each skill is packaged as a separate plugin in the `seachicken` marketplace, so repositories can enable only what they need.

## Plugins

- `change-understanding`: assess understanding of a code change through questions grounded in the diff. Skill: `change-understanding:change-understanding`.

## Register the marketplace

```sh
codex plugin marketplace add seachicken/agent-skills
```

The shared catalog makes plugins available for individual installation; it does not request default installation of every plugin.

## Use in a repository

After registering the marketplace and installing the required plugin, enable it in the repository's `.codex/config.toml`:

```toml
[plugins."change-understanding@seachicken"]
enabled = true
```

For repository-driven default installation, put a catalog at `.agents/plugins/marketplace.json` containing only the required plugin entries from this marketplace, and set those entries' `policy.installation` to `INSTALLED_BY_DEFAULT`. Keep the Git source and plugin subdirectory paths unchanged. Do not copy unrelated entries as the shared catalog grows.

Project configuration requires a trusted project and a client that supports local plugin marketplaces. Restart or refresh the client after adding the configuration. The GitHub source must be pushed and accessible before installation can succeed.

To require the understanding check in the assistant's commit workflow, add this to the consuming repository's `AGENTS.md`:

```markdown
Before every commit, use the `change-understanding:change-understanding` skill. Commit only after the user scores 100 and relevant checks pass, unless the user explicitly waives the quiz.
```

Default installation does not enforce execution or restrict manual Git commits.
