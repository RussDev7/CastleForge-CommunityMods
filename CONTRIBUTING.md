# Contributing to CastleForge Community Mods

Thanks for helping grow the CastleForge community catalog.

This repository is for **community listings** for:

- **Mods**
- **Texture Packs**
- **Weapon Addons**
- **World Gen**

You do **not** need to edit a separate index file.
Just add your project as a new folder in the correct category.

---

## The simple version

If you only want the fast version, do this:

1. **Fork** this repository.
2. Pick the correct folder:
   - `Mods/`
   - `TexturePacks/`
   - `WeaponAddons/`
   - `WorldGen/`
3. Copy that folder's `_template/`.
4. Rename it to your project name.
5. Fill out `mod.json`, `README.md`, and your preview image.
6. Open a **pull request**.

That is the whole submission process.

---

## Pick the right category

Choose **one** category for your entry.

### `Mods/`
Use this for projects that add or change:

- gameplay
- commands
- systems
- UI
- features
- logic or behavior

### `TexturePacks/`
Use this for projects that mainly change:

- textures
- visual presentation
- art style
- appearance

### `WeaponAddons/`
Use this for projects that mainly add or expand:

- weapons
- weapon packs
- weapon-focused content
- weapon behavior or weapon content sets

### `WorldGen/`
Use this for projects that mainly add or change:

- custom terrain generation
- biome generation
- world presets
- mountain / cave / terrain overhauls
- procedural world layout systems

Do **not** submit the same entry in multiple folders.

---

## Folder structure

Each submission should be a **new folder** inside the correct category.

```text
CastleForge-CommunityMods/
│  README.md
│  CONTRIBUTING.md
│
├─ Mods/
│  ├─ _template/
│  └─ MyCoolMod/
│     ├─ mod.json
│     ├─ README.md
│     └─ preview.png
│
├─ TexturePacks/
│  ├─ _template/
│  └─ MyTexturePack/
│     ├─ mod.json
│     ├─ README.md
│     └─ preview.png
│
├─ WeaponAddons/
│  ├─ _template/
│  └─ MyWeaponAddon/
│     ├─ mod.json
│     ├─ README.md
│     └─ preview.png
│
└─ WorldGen/
   ├─ _template/
   └─ MyWorldGen/
      ├─ mod.json
      ├─ README.md
      └─ preview.png
```

---

## Files you should include

Every entry should include:

### `mod.json`
This is your catalog metadata file.
It tells the site what your project is.

### `README.md`
This explains your project.
Tell people what it does, how to install it, and where to find more information.

### `preview.png` or `preview.gif`
This is your preview media.
Use a screenshot, banner, or animation that helps people understand your project quickly.

---

## Required `category` value in `mod.json`

Your `mod.json` must use the correct category value for the folder you chose.

### If your entry is in `Mods/`
```json
"category": "mod"
```

### If your entry is in `TexturePacks/`
```json
"category": "texture-pack"
```

### If your entry is in `WeaponAddons/`
```json
"category": "weapon-addon"
```

### If your entry is in `WorldGen/`
```json
"category": "world-gen"
```

Make sure the folder and the `category` value match.

---

## What your README should explain

Your README should help a new user understand your project quickly.

Try to include:

- project name
- author or maintainer
- short description
- CastleForge compatibility
- game compatibility
- installation steps
- source repository link
- release or download link
- screenshots or preview media
- license information if available

---

## Step-by-step: how to open a PR

### 1) Fork the repository
Click **Fork** on GitHub to create your own copy.

### 2) Create your entry folder
Add a new folder inside the correct category.

Examples:

- `Mods/MyCoolMod/`
- `TexturePacks/MyTexturePack/`
- `WeaponAddons/MyWeaponAddon/`
- `WorldGen/MyWorldGen/`

### 3) Copy the template
Copy the `_template/` folder from the category you are using.
Then rename it to your project name.

### 4) Edit the template files
Update:

- `mod.json`
- `README.md`
- `preview.png` or `preview.gif`

### 5) Commit your changes
Use a clear commit message.

Examples:

- `Add MyCoolMod community entry`
- `Add MyTexturePack texture pack entry`
- `Add MyWeaponAddon weapon addon entry`
- `Add MyWorldGen biome entry`

### 6) Open a pull request
Submit your branch as a PR to this repository.

Good PR title examples:

- `Add MyCoolMod community entry`
- `Add MyTexturePack texture pack entry`
- `Add MyWeaponAddon weapon addon entry`
- `Add MyWorldGen biome entry`

### 7) Respond to review if needed
A maintainer may ask for small fixes before merging.
That is normal.

---

## Quick checklist before you submit

- [ ] I used the correct category folder
- [ ] I copied the correct `_template/`
- [ ] I renamed the folder to my project name
- [ ] I filled out `mod.json`
- [ ] I updated `README.md`
- [ ] I added `preview.png` or `preview.gif`
- [ ] My links work
- [ ] My `category` value matches the folder type

---

## What not to do

Please avoid these common mistakes:

- do not add your entry to more than one category
- do not leave template placeholder text unchanged
- do not forget preview media
- do not use broken download or source links
- do not submit intentionally harmful, malicious, or deceptive content
- do not assume listing here means official CastleForge support

---

## Source code hosting

Your full source code or content files do **not** need to live in this repository.

In most cases, it is better to:

- keep your full project in your own repository
- keep releases in your own repo or release page
- use this repo as the public catalog listing

---

## After your PR is merged

Once accepted, your entry can appear in the CastleForge community catalog and help other people discover your project.

Listing here does **not** automatically mean the project is officially maintained or supported by the main CastleForge maintainers.

---

## Need help?

If you need help with the submission process:

- **DM on Discord:** [dannyruss](https://discordapp.com/users/364835156587970580) (_RussDev7)
- **CastleForge Discord:** [Join the server](https://discord.gg/j3PcNJmry5)

If your question is about a specific project, check that project's own README, repository, and release page first.
