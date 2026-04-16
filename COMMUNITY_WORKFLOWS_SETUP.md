# Community Workflows Setup

Included workflows:

- `.github/workflows/validate-catalog.yml`
- `.github/workflows/validate-links.yml`
- `.github/workflows/deploy-pages.yml`

## What they do

### Validate Catalog
Checks that every real mod entry under `mods/` has:
- `mod.json`
- `README.md`
- `preview.*`
- matching data in `index/mods.json`

It ignores the starter `_template` folder and the placeholder `ExampleCommunityMod` entry while the repo is still in scaffold mode.

### Validate Links
Checks external URLs found in:
- root `README.md`
- root `CONTRIBUTING.md`
- each real mod `README.md`
- each real mod `mod.json` (`source_repo`, `releases_url`)

### Deploy Catalog Site
Builds a lightweight static catalog site and deploys it with GitHub Pages.

## One-time GitHub setup

1. Go to **Settings → Pages**.
2. Under **Build and deployment**, set **Source** to **GitHub Actions**.
3. Make sure GitHub Actions is enabled for the repository.
4. Merge the workflow files into your default branch.

After that, pushes to `main` or `master` that touch `mods/`, `index/`, or the relevant docs will rebuild the site.
