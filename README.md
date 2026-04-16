# CastleForge Community Mods

![CastleForge Preview](Assets/Branding/Preview.png)

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
├─ Mods/
│  ├─ _template/
│  └─ ExampleCommunityMod/
│     ├─ mod.json
│     ├─ README.md
│     └─ preview.png
│
└─ Index/
   └─ mods.json
```

## Promotion path

A community mod can later be promoted into the main CastleForge repository if it becomes:

- actively maintained
- widely used
- well documented
- something the CastleForge maintainers want to officially support

## Main CastleForge repo relationship

The main **[CastleForge](https://github.com/RussDev7/CastleForge)** repository is the home of the official CastleForge ecosystem, including:

- the core **ModLoader**
- **ModLoaderExtensions**
- official first-party mods
- official tools
- official servers
- platform documentation and installation guidance

This **CastleForge-CommunityMods** repository exists alongside it as the dedicated home for **community-created mod listings and discovery**.

### In simple terms

- **CastleForge** = official platform + officially maintained mods
- **CastleForge-CommunityMods** = third-party community mod catalog

### Why they are separated

Keeping the repositories separate helps:

- keep the main CastleForge repo clean and focused
- make official support boundaries clearer
- avoid mixing unrelated third-party source projects into the core platform
- make community submissions easier to review and organize
- allow community mods to grow without bloating the main CastleForge solution

### Support expectations

In general:

- mods in the main **CastleForge** repository are part of the official CastleForge ecosystem
- mods listed in **CastleForge-CommunityMods** may be community-maintained and may have different update schedules, support levels, or compatibility guarantees

Each catalog entry should make ownership, source links, release links, and compatibility notes as clear as possible.

### Possible promotion to official status

A community mod listed here may later be promoted into the main **CastleForge** repository if it becomes:

- actively maintained
- widely used
- well documented
- compatible with current CastleForge standards
- something the CastleForge maintainers choose to officially support

## Support CastleForge

Want to support the core CastleForge project that powers the official ecosystem?

[![Buy Me A Coffee](https://www.buymeacoffee.com/assets/img/custom_images/yellow_img.png)](https://buymeacoffee.com/castleforge)

> This supports the main CastleForge project and its infrastructure. Community-listed mods may be maintained by independent creators.
