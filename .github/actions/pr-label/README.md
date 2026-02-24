# PR-label

Labels pull requests based on which files changed.

## Inputs

- `rules` (required): JSON array of rules. Each rule:
  - `label`: label name to apply
  - `anyChanged`: array of path prefixes; if any changed file starts with one of these, the label matches
- `github-token`: token used to read PR files + apply labels (defaults to `${{ github.token }}`)
- `remove-unmatched`: if `"true"`, remove rule labels when they no longer match (default: `"false"`)
- `debug`: if `"true"`, logs PR changed files + extra details (default: `"false"`)

## Example

```yaml
- uses: ./.github/actions/pr-label
  with:
    rules: |
      [
        { "label": "db-migration", "anyChanged": ["packages/database/src/postgres/drizzle/"] }
      ]
```
