# renovate-configs

Shared [Renovate](https://docs.renovatebot.com/) configuration presets for all personal repositories.

## Available presets

| Preset | File | Use for |
|---|---|---|
| `base` | `base.json` | All repos — schedule, grouping, vulnerability alerts, no automerge |

## Usage

Add a `renovate.json` to your repo:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["github>Jastchi/renovate-configs//base.json"],
  "enabledManagers": ["pep621", "github-actions"]
}
```

Then add only repo-specific rules: package freezes, version constraints, custom groups.

## Policy

- **No automerge** — all PRs require manual merge, including security fixes
- **Bi-weekly schedule** — PRs open every other Monday
- **7-day minimum release age** before PRs are created (security alerts bypass this)
- **Vulnerability alerts** fire immediately, bypass schedule, labelled `security`
- **`requires-python` never updated** — managed manually
- **All update types allowed** — minor, patch, major each get their own grouped PR

## Changing the policy

Edit `base.json` here. All repos extending the preset pick up the change automatically on Renovate's next run.
