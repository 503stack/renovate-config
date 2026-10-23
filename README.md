# renovate-config

Shared [Renovate](https://docs.renovatebot.com/) presets for the 503stack org.

| Preset | File | What it does |
| --- | --- | --- |
| `github>503stack/renovate-config` | `default.json` | `config:recommended`, automerge once checks pass (`platformAutomerge`), runs at any time, one PR per dependency straight to the newest version (majors included), annotated YAML versions (below) |
| `github>503stack/renovate-config:automerge` | `automerge.json` | Deprecated no-op; automerge is in the default |

## Usage

`renovate.json` in a repo:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": [
    "github>503stack/renovate-config"
  ]
}
```

To opt out of automerge (or keep majors manual), override `automerge` or add a `packageRules`
entry in the repo. Repo-specific managers and `packageRules` stay in the repo's own
`renovate.json`.

## Annotated versions

Any YAML value can be tracked by putting a comment on the line above it:

```yaml
env:
  # renovate: datasource=github-releases depName=containers/podman
  PODMAN_VERSION: v6.1.4
```

Options go in this order, all but `datasource` and `depName` optional:
`datasource= depName= packageName= versioning= extractVersion= registryUrl=`.
Only plain versions match (no `/`, `:` or `@`), so a comment above an `image:` line
is ignored and the image stays with the docker/kubernetes managers. Versioning
defaults to the datasource's own unless `versioning=` is given.
