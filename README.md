# channel3-ai Renovate config

Shared [Renovate](https://docs.renovatebot.com/) policy for `channel3-ai` repositories.

## Usage

In any repo's `renovate.json`:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["github>channel3-ai/renovate-config"]
}
```

The Renovate GitHub App must be installed on both this repo and the consuming repo.

## Presets

- `default.json` (default): standard policy — weekly grouped non-major updates, immediate vulnerability PRs, lockfile maintenance, OSV + GHSA advisories, no auto-merge.

To use a non-default preset, extend its name explicitly: `"github>channel3-ai/renovate-config:python-strict"`, etc.

## Changing policy

Edit `default.json`, open a PR, merge. All consuming repos pick up the change on their next Renovate run (within ~1 hour).
