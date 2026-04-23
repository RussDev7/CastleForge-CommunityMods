# Community Workflows Setup

Included workflows:

- `.github/workflows/validate-catalog.yml`
- `.github/workflows/validate-links.yml`
- `.github/workflows/deploy-pages.yml`

## What they do

### Validate Catalog
Checks that every real entry under these roots has:

- `mod.json`
- `README.md`
- `preview.*`
- matching data in `Index/mods.json`

Supported roots:

- `Mods/`
- `TexturePacks/`
- `WeaponAddons/`
- `WorldGen/`

It ignores `_template` folders so you can keep starter scaffolding in the repo.

### Validate Links
Checks external URLs found in:

- root `README.md`
- root `CONTRIBUTING.md`
- each real entry `README.md`
- each real entry `mod.json` (`source_repo`, `releases_url`)

### Deploy Catalog Site
Builds a lightweight static catalog site, supports category filtering, and deploys it with GitHub Pages.

## One-time GitHub setup

1. Go to **Settings → Pages**.
2. Under **Build and deployment**, set **Source** to **GitHub Actions**.
3. Make sure GitHub Actions is enabled for the repository.
4. Merge the workflow files into your default branch.

After that, pushes to `main` or `master` that touch `Mods/`, `TexturePacks/`, `WeaponAddons/`, `WorldGen/`, `Index/`, or the relevant docs will rebuild the site.
