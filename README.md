# CastleForge Community Mods

![CastleForge Preview](Assets/Branding/Preview.png)

This repository is the **community catalog** for third-party CastleForge content.

It supports three content types:

- **Mods**
- **Texture Packs**
- **Weapon Addons**
- **World Gen**

This repository is meant to be **easy to contribute to**.
If you made something for CastleForge and want people to discover it, you can open a pull request and add it here.

---

## Browse community content online

Want to look through community content instead of submitting something?

➡️ **[Open the Browser](https://russdev7.github.io/CastleForge-CommunityMods/)**

Use the website to:

- preview community entries
- open each entry's README
- jump to source repositories
- find release/download links
- filter by content type

Use this GitHub repository when you want to:

- submit a new community entry
- update your existing entry
- fix entry information
- improve documentation or previews

---

## What belongs here

This repository is for **catalog entries**, not for storing every full project.

A normal entry includes:

- a small manifest file (`mod.json`)
- a README
- a preview image or GIF
- links to the real project, release page, or download page

In most cases, creators should keep the full mod or content pack in their **own repository** and use this repo as the public catalog listing.

---

## Quick start: how to submit something

If you are new, this is the simple version:

1. **Fork** this repository.
2. Pick the correct folder:
   - `Mods/`
   - `TexturePacks/`
   - `WeaponAddons/`
   - `WorldGen/`
3. Copy that category's `_template/` folder.
4. Rename it to your project name.
5. Fill in your required files:
   - mod.json
   - README.md
   - preview.png or preview.gif
6. Open a **pull request**.

That is the basic flow.

You do **not** need to add your project to a separate manual index.
Each entry lives in its own folder.

---

## Which folder do I use?

Choose **one** category only:

### Use `Mods/` if your project:

- adds gameplay features
- changes logic or behavior
- adds systems, tools, commands, UI, or game functionality

### Use `TexturePacks/` if your project:

- replaces or enhances textures
- is mainly visual/art-focused
- does not primarily add gameplay systems

### Use `WeaponAddons/` if your project:

- adds new weapons or weapon-focused content
- expands weapon behavior, weapon sets, or weapon content packs

### Use `WorldGen/` if your project:

- adds or changes procedural world generation
- creates custom terrain styles, biome regions, or generation presets
- focuses on cliffs, mountains, valleys, caves, or large-scale terrain overhauls
- is primarily a world creation or terrain-generation project

---

## Folder layout

Each submission should be added as a **new folder** inside the correct category.

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

## Files each entry should include

Every entry should include these files:

### `mod.json`
Your metadata file.
This is what the catalog uses to understand your entry.

### `README.md`
Your project page.
Use it to explain what your project is, what it does, how to install it, and where to download it.

### `preview.png` or `preview.gif`
Your preview image.
This helps people quickly understand what your project looks like.

---

## Required category value in `mod.json`

Every entry uses the same `mod.json` format.
The important part is the `category` value.

Use one of these:

- `"category": "mod"`
- `"category": "texture-pack"`
- `"category": "weapon-addon"`
- `"category": "world-gen"`

That tells the catalog where your entry belongs.

---

## What your entry should explain

Your entry should make it easy for a new user to understand:

- **what it is**
- **who made it**
- **what version it works with**
- **where to download it**
- **where the source repo is**
- **how to install it**
- **what screenshots or preview media show it off**

A strong entry usually includes:

- project name
- author or maintainer
- short description
- CastleForge compatibility
- game compatibility
- source repository link
- release or download link
- license
- preview image or GIF

---

## Simple pull request guide

If you have never opened a PR before, use this flow:

### 1) Fork the repository
Click **Fork** at the top of this GitHub repository.

### 2) Create your entry folder
Inside your fork, add a new folder in the correct category.

Examples:

- `Mods/MyCoolMod/`
- `TexturePacks/MyTexturePack/`
- `WeaponAddons/MyWeaponAddon/`
- `WorldGen/MyWorldGen/`

### 3) Copy the template
Copy the `_template/` folder from the category you are using, then rename it to your project name.

### 4) Edit the files
Update:

- `mod.json`
- `README.md`
- `preview.png` or `preview.gif`

### 5) Commit your changes
Use a clear commit message, such as:

- `Add MyCoolMod community entry`
- `Add MyTexturePack texture pack entry`
- `Add MyWeaponAddon weapon addon entry`
- `Add MyWorldGen biome entry`

### 6) Open a pull request
Submit your PR back to this repository.

A good PR title looks like:

- `Add MyCoolMod community entry`
- `Add MyTexturePack texture pack entry`
- `Add MyWeaponAddon weapon addon entry`
- `Add MyWorldGen biome entry`

### 7) Wait for review
A maintainer can then review it, request changes if needed, and merge it.

---

## Tips for a clean submission

To help your PR get accepted faster:

- keep the folder name clean and readable
- make sure links work
- make sure the README is easy to understand
- include a preview image or GIF
- make sure your `category` value is correct
- do not submit broken, malicious, or intentionally harmful content
- do not put your entry in more than one category

---

## Example beginner checklist

Before opening your PR, quickly check:

- [ ] I used the correct category folder
- [ ] I copied the `_template/` folder
- [ ] I renamed the folder to my project name
- [ ] I filled out `mod.json`
- [ ] I updated `README.md`
- [ ] I added `preview.png` or `preview.gif`
- [ ] My links work
- [ ] My `category` value matches the folder type

---

## What happens after a PR is merged?

Once accepted, your entry becomes part of the community catalog.
It can then appear in the community browser and help other people discover your project.

Being listed here does **not** automatically mean the project is officially supported by the main CastleForge maintainers.
Community entries may be maintained by independent creators.

---

## Relationship to the main CastleForge repo

The main **[CastleForge](https://github.com/RussDev7/CastleForge)** repository is the home of the official CastleForge ecosystem.

This repository is different:

- **CastleForge** = official platform and official projects
- **CastleForge-CommunityMods** = community catalog for third-party content

This separation keeps the official repo cleaner and makes community submissions easier to organize.

---

## Need help?

If you need help with the catalog or submission process:

- **DM me on Discord:** [dannyruss](https://discordapp.com/users/364835156587970580) (_RussDev7)
- **Join the CastleForge Discord server:** [Discord Server](https://discord.gg/j3PcNJmry5)

If your question is about a specific community project, check that project's own README, repository, and release page first.

---

## Support CastleForge

Want to support the main CastleForge project?

[![Buy Me A Coffee](https://www.buymeacoffee.com/assets/img/custom_images/yellow_img.png)](https://buymeacoffee.com/castleforge)

> This supports the main CastleForge project and its infrastructure. Community-listed projects may be maintained by independent creators.
