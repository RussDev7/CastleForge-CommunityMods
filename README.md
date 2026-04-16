# CastleForge Community Mods

This repository is the **community catalog / hub** for third-party CastleForge mods.

It is intentionally separate from the main CastleForge repository so the core platform and official mods can stay stable, focused, and easy to maintain.

## What belongs here

This repository is a good home for:

- third-party CastleForge mods
- community-maintained mod listings
- preview images / GIFs
- mod metadata / manifests
- links to source repositories and releases
- compatibility notes

## Recommended model

The best long-term model is:

- each creator may keep their mod in its **own repository**
- this repository stores the **catalog entry** for discovery
- the catalog entry links to:
  - source repo
  - releases
  - documentation
  - preview images
  - compatibility metadata

That keeps ownership clear and avoids one giant source monorepo for unrelated community projects.

## Folder layout

```text
CastleForge-CommunityMods/
│  README.md
│  CONTRIBUTING.md
│
├─ mods/
│  ├─ _template/
│  └─ ExampleCommunityMod/
│     ├─ mod.json
│     ├─ README.md
│     └─ preview.png
│
└─ index/
   └─ mods.json
```

## Promotion path

A community mod can later be promoted into the main CastleForge repository if it becomes:

- actively maintained
- widely used
- well documented
- something the CastleForge maintainers want to officially support

## Main CastleForge repo relationship

The main CastleForge repository should link here as:

- **Community Mods**
- **Third-Party Mods**
- **Mod Catalog**

and clearly explain the difference between:

- **official first-party mods**
- **community catalog mods**
