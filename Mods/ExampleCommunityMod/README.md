# ExampleCommunityMod

![Preview](preview.png)

> A sample **community catalog entry** for CastleForge that shows creators how to present a third-party mod inside the `CastleForge-CommunityMods` repository.

This folder is a **rebranded community version** of the official CastleForge `Example` starter mod concept. Instead of acting as an official first-party sample inside the main CastleForge source tree, it is formatted the way a creator would submit a mod entry to the community catalog.

---

## What this example is for

`ExampleCommunityMod` is meant to demonstrate:

- how to structure a mod folder under `Mods/<ModName>/`
- how to write a readable `README.md`
- how to provide a `mod.json` metadata file for catalog tooling
- how to include a preview image for the generated community mod site
- how to link back to a separate source repository and releases page

It is not intended to be treated as a real published gameplay mod.

---

## Included files

```text
Mods/
└─ ExampleCommunityMod/
   ├─ mod.json
   ├─ README.md
   └─ preview.png
```

### File purposes

| File | Purpose |
|---|---|
| `mod.json` | Machine-readable catalog metadata used by validation and site generation workflows. |
| `README.md` | Human-facing description of the mod entry. |
| `preview.png` | Visual preview used in the repository and generated catalog site. |

---

## Suggested submission model

The recommended long-term setup for a real community mod is:

- keep the actual mod source code in its **own repository**
- create a folder here only for the **catalog entry**
- use `mod.json` to point to:
  - the source repository
  - releases/downloads
  - documentation
  - preview media

That keeps ownership and support boundaries clear while still making the mod easy to discover.

---

## Recommended `mod.json` fields

This example includes the required metadata fields expected by the community catalog workflows:

- `name`
- `slug`
- `author`
- `summary`
- `game_version`
- `castleforge_version`
- `license`
- `source_repo`
- `releases_url`
- `readme_path`
- `preview_path`
- `tags`
- `official`

For real submissions:

- set `official` to `false`
- use a stable `slug`
- keep the `summary` short and clear
- make sure the README and preview paths match the real file names exactly

---

## How to adapt this example

To turn this into a real submission:

1. Rename `ExampleCommunityMod` to your actual mod name.
2. Replace `preview.png` with your own preview image or GIF.
3. Update `mod.json` with your real:
   - author name
   - summary
   - supported versions
   - source repository link
   - releases link
   - tags
4. Replace this README with real installation, usage, feature, and compatibility details.

---

## Relationship to the main CastleForge repo

This community entry format is intentionally different from the official `Example` mod found in the main CastleForge repository.

- The **main CastleForge repo** contains official source code, buildable projects, and first-party documentation.
- The **CastleForge-CommunityMods repo** contains discovery-focused catalog entries for third-party creators.

That separation helps the core project stay clean while giving community mods a dedicated place to be listed.

---

## Notes for maintainers

If this entry is used as a starter template:

- keep the placeholder links obviously fake until replaced
- keep the preview image lightweight
- make sure `mod.json` stays valid JSON
- make sure folder, README path, and preview path casing match exactly

---

## Status

This is a **template/example submission**, not an officially supported CastleForge mod.
