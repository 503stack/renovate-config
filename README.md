# renovate-config

Shared [Renovate](https://docs.renovatebot.com/) presets for the 503stack org.

| Preset | File | What it does |
| --- | --- | --- |
| `local>503stack/renovate-config` | `default.json` | `config:recommended` + `platformAutomerge` |
| `local>503stack/renovate-config:automerge` | `automerge.json` | Automerge every update once checks pass |

## Usage

`renovate.json` in a repo:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": [
    "local>503stack/renovate-config"
  ]
}
```

Add `"local>503stack/renovate-config:automerge"` to opt in to automerge. Repo-specific
managers and `packageRules` stay in the repo's own `renovate.json`.
