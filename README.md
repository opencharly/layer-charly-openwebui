# charly-openwebui

The `charly-openwebui` family — the owning skill for the Open WebUI chat-frontend
layer.

The `charly-openwebui` candy is a **concept candy**: it ships no install content
and owns the `openwebui` family's `skill:` entity whose name has no namesake
candy — the `openwebui-layer` skill. It documents the Open WebUI service: port
8080, the `data` volume, the auto-configuration entrypoint (LLM provider
detection, MCP server discovery, Jupyter code execution), the two-tier secrets
architecture, and the `ENABLE_PERSISTENT_CONFIG=false` design choice.

The image / box skill of the same family is owned by
`opencharly/box-openwebui` (`/charly-openwebui:openwebui`).
`candy/plugin-marketplace` regenerates the standalone
[opencharly/marketplace](https://github.com/opencharly/marketplace) corpus from
these entities, so the skill is authored here and projected there.

## What it provides

| Property | Value |
|---|---|
| Layer / candy | `charly-openwebui` (concept candy) |
| Install content | none — a `true` no-op `plan:` |
| Owns | 1 `skill:` entity: `openwebui-layer` |
| Projected to | `marketplace/openwebui/skills/` |
| Service / port | none (the `openwebui-layer` skill documents port 8080) |

## How to use it

This repo is consumed as a **skill source**, not as an image layer. Edit the
`skill:` entity in `charly.yml`; the marketplace regeneration projects it into
the `/charly-openwebui:openwebui-layer` page. To reference the repo directly,
compose it in a box. A box is a `candy:` node carrying the box's `base:` image
and a nested `candy:` list of layer refs (the nested `candy:` is the composition
list; the outer `candy:` is the box body):

```yaml
my-box:
  candy:                  # the box body (an IMAGE is a `candy:` node carrying `base:`)
    base: fedora          # the box's base image
    candy:                # the box's composition list
      - '@github.com/opencharly/layer-charly-openwebui:v2026.243.2107'
```

The Open WebUI service itself is installed by the `openwebui` image candy, not
by this concept candy — this repo only carries the projected skill.

## Layout

- `charly.yml` — the `charly-openwebui:` concept candy entity plus the
  `openwebui-layer-skill:` entity.
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `README.md` — this user overview.

## Related

- Owning skill: `/charly-openwebui:openwebui-layer`
- Image / box skill: `/charly-openwebui:openwebui`
- Authoring reference: `/charly-image:layer`
- [`opencharly/marketplace`](https://github.com/opencharly/marketplace) — the projected corpus
- [`opencharly/charly`](https://github.com/opencharly/charly) — the charly CLI and image builder
- [`opencharly/opencharly`](https://github.com/opencharly/opencharly) — the umbrella
