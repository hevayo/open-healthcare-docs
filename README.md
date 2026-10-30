# open-healthcare-docs

The WSO2 Open Healthcare documentation. Two sites live in this repo until the cutover:

- `main` builds the current site, https://healthcare.docs.wso2.com/ (Docusaurus, `en/`). Writers still change the docs there.
- `docs-v2/main` is the same docs as a Content repo of WSO2 Docs, generated from `main` until the cutover. At the cutover it becomes the repo's main line.

## The WSO2 Docs layout (`docs-v2/main`)

| Directory | Doc space | Editions and branches |
|---|---|---|
| `healthcare/` | Open Healthcare | one unversioned Edition, built from `docs-v2/main` |

The Doc space directory holds `docspace.yaml` (the Doc space manifest), `redirects.yaml` (page moves), `docs/` (pages; folders are the menu) and `assets/` (images and downloads).

Every branch of this layout starts with `docs-v2/` until the cutover. Open Healthcare has no versions: there are no release branches. Docs releases are made by hand from `docs-v2/main` and tagged `cloud-<YYYY.MM.DD>.<n>`.

Its pages are converted from `main` by the site rebuild (`tools/rebuild/open-healthcare/` in the onboarding workspace), not merged: fix the source on `main` or the converter's rules, and don't edit them by hand until the cutover. Every page keeps its old path in its address (`/healthcare/<path>/`, without `/docs/`), with front-matter `slug:` wherever the sidebar puts it in another folder; keep the slug when you move a page.

The repo root holds only shared files: this README, `CODEOWNERS`, `LICENSE`, the release workflow (`.github/workflows/docs-bundle-release.yml`, "Release a Docs bundle"), the branch ruleset (`.github/branch-ruleset.json`), the editor settings, and `AGENTS.md` and `CLAUDE.md` for agents (they point to `npx @wso2-enterprise/docs help`), the Platform-managed ones from `templates/content-repo/` in `wso2-enterprise/choreolabs-docs`.

The tools are on GitHub Packages. Once per machine, make a classic personal access token with `read:packages` (authorised for the `wso2-enterprise` organisation's SSO if it asks), then run `npm login --scope=@wso2-enterprise --auth-type=legacy --registry=https://npm.pkg.github.com` with your GitHub user name and the token as the password. This repo's `.npmrc` names the registry for `@wso2-enterprise`; it holds no token.

Get started, from setting up your computer to a Docs release going live: the WSO2 Docs Platform's README, https://github.com/wso2-enterprise/choreolabs-docs#readme.
