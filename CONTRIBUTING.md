# Contributing to CastleForge Community Mods

This repository is a catalog and submission hub for third-party CastleForge content.

## Supported entry types

You can submit:

- mods
- texture packs
- weapon addons

## Submission model

A normal submission adds a folder under one of these roots:

- `Mods/<EntryName>/`
- `TexturePacks/<EntryName>/`
- `WeaponAddons/<EntryName>/`

Each entry should contain at least:

- `mod.json`
- `README.md`
- `preview.png` or `preview.gif`

## Required manifest field

Each `mod.json` must include a `category` field:

- `mod`
- `texture-pack`
- `weapon-addon`

## What the catalog entry should contain

Each submission should clearly state:

- entry name
- author / maintainer
- short description
- game compatibility
- CastleForge compatibility
- source repository link
- release / download link
- license
- screenshots / preview media

## Source code hosting

Source code or content files do **not** need to live in this repository.

In most cases, it is better for the creator to keep the full project in their own repository and use this repo as the shared index / discovery catalog.

## Quality bar

Submissions should be:

- clearly documented
- safe to redistribute
- named clearly
- packaged consistently
- not intentionally destructive or malicious

## Support expectations

Being listed here does **not** mean the project is officially supported by CastleForge maintainers unless the listing explicitly says so.
