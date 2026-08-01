# channel3-ai Renovate config

Shared [Renovate](https://docs.renovatebot.com/) policy for `channel3-ai` repositories.

## Usage

Every repo in the org picks this policy up automatically via `org-inherited-config.json`
(see below) — no per-repo file is required.

To opt a repo into anything extra, add its own `renovate.json`:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["github>channel3-ai/renovate-config"]
}
```

The Renovate GitHub App must be installed on both this repo and the consuming repo.

## Org-wide inheritance

`org-inherited-config.json` is Renovate's [inherited config](https://docs.renovatebot.com/config-overview/#inherited-config).
Renovate reads it from `channel3-ai/renovate-config` and merges it into **every** repo in the
org before that repo's own config, so repos with no `renovate.json` still get this policy.

This requires `requireConfig` to be `optional` in the Mend app settings
(developer.mend.io → channel3-ai → Settings). While `requireConfig` is `required`, Renovate
skips any repo that has no config file of its own, and inheritance never applies.

Keep policy in `default.json`. `org-inherited-config.json` should stay a thin pointer at it so
there is one source of truth — repo-level config wins over inherited config, so duplicating
settings across both files causes the inherited copy to be silently ignored.

## Presets

- `default.json` (default): standard policy — weekly grouped non-major updates, immediate vulnerability PRs, lockfile maintenance, OSV + GHSA advisories, no auto-merge.

To use a non-default preset, extend its name explicitly: `"github>channel3-ai/renovate-config:python-strict"`, etc.

## Changing policy

Edit `default.json`, open a PR, merge. All consuming repos pick up the change on their next Renovate run (within ~1 hour).
