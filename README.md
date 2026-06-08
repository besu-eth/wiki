# Besu Wiki — Source Repository

This repository (`besu-eth/wiki`) is the **source of truth** for the [Besu project wiki](https://github.com/besu-eth/besu/wiki). Content is edited here through normal pull requests and then automatically published to the rendered GitHub wiki.

> **Why a separate source repo?**
> A GitHub wiki is itself a git repository, but it cannot accept pull requests and has no review or branch-protection workflow. By keeping the canonical content in this regular repo, every change goes through PR review before it is published. The rendered wiki at `besu-eth/besu.wiki` is treated as a **build artifact**, not something edited directly.

---

## What's in here

Each wiki page is a Markdown file at the **repository root**. This matches how GitHub renders a wiki: the page namespace is flat, and the filename *is* the page title (hyphens render as spaces, e.g. `Working-through-Hive-tests.md` → "Working through Hive tests").

| File | Purpose |
| --- | --- |
| `Home.md` | The wiki landing page and primary index. |
| `About-This-Wiki.md` | What the wiki is, its Confluence origin, and how to continue the migration. |
| `Contributing-First-Contribution.md` | Guide for first-time contributors to Besu. |
| `Defect-Prioritization-Guide.md` | How defects are triaged and prioritized. |
| `Devnet-Testing-and-Tooling.md` | Devnet testing workflow and tooling. |
| `EPF-project-ideas.md` | Ethereum Protocol Fellowship project ideas. |
| `LFDT-mentorship-project-ideas.md` | LFDT mentorship project ideas. |
| `Working-through-Hive-tests.md` | Working with the Hive test suite. |
| `.github/workflows/publish-wiki.yml` | CI that publishes this content to the rendered wiki. |
| `LICENSE` | Apache 2.0. |

### The `confluenceExport` branch — backup, not content

Most of this wiki originated as a large export from a Confluence instance. That full, nested export is preserved on the [`confluenceExport`](https://github.com/besu-eth/wiki/tree/confluenceExport) branch as a **read-only backup**; `main` only contains pages that have been deliberately ported and cleaned up. The origin story and step-by-step instructions for porting more pages live in the [About This Wiki](About-This-Wiki.md) page.

---

## How it's deployed

```
  ┌─────────────────────┐   PR + review + merge to main   ┌──────────────────────┐
  │  besu-eth/wiki       │ ──────────────────────────────▶ │  publish-wiki.yml    │
  │  (this repo, source) │                                  │  runs on push: main  │
  └─────────────────────┘                                  └──────────┬───────────┘
                                                                       │ pushes pages
                                                                       ▼
                                                            ┌──────────────────────┐
                                                            │  besu-eth/besu wiki   │
                                                            │  (rendered, read-only)│
                                                            └──────────────────────┘
```

Deployment runs via the [GitHub Wiki Action](https://github.com/Andrew-Chen-Wang/github-wiki-action), configured in [`.github/workflows/publish-wiki.yml`](.github/workflows/publish-wiki.yml), on every merge to `main`:

1. A contributor opens a PR against this repo.
2. The PR is reviewed and merged to `main`.
3. The workflow pushes the root Markdown pages to the `besu-eth/besu` wiki backend (`.wiki.git`). Repo metadata (`README.md`, `LICENSE`, `.gitignore`, `.github/`) is ignored and never published.
4. GitHub renders the wiki and it becomes immediately visible to end users.

> **One-time setup:** because the workflow pushes to a *different* repo's wiki, the default `GITHUB_TOKEN` is not sufficient. Create a Personal Access Token with push access to the `besu-eth/besu` wiki — a fine-grained PAT scoped to `besu-eth/besu` with **Contents: Read and write** (or a classic token with `public_repo`) — and add it as `WIKI_PUBLISH_TOKEN` under the **`Production` environment** (Settings → Environments → Production), not as a plain repo secret. The publish job is bound to that environment. See the header comment in the workflow file for details.

---

## How end users use it

End users never see this repo. They read the published wiki at:

**https://github.com/besu-eth/besu/wiki**

There they get a navigable, searchable, cross-linked set of pages, rendered by GitHub with a sidebar, search, and a home page.

---

## Contributing

We use a **feature-branch + pull-request** workflow. Direct pushes to `main` are not permitted.

1. **Branch off `main`:**
   ```bash
   git switch -c docs/short-description
   ```
2. **Edit or add a page** at the repo root. Use standard GitHub-Flavored Markdown, one topic per page.
3. **Name files for the wiki.** The filename becomes the page title and URL; use `Hyphen-Separated-Words.md`. Encode any grouping in the name (e.g. `Contributing-First-Contribution.md`).
4. **Link between pages** using the target page's name without the extension, e.g. `[First Contribution](Contributing-First-Contribution)`. Update `Home.md` (and the sidebar, once one exists) to surface new pages.
5. **Open a PR** against `main` with a clear description.
6. **Review & merge.** Once merged, the publish workflow updates the live wiki automatically.

### Authoring guidelines

- **One page = one topic**, with a single `#` H1 as the title.
- **Internal links** use bare page names (no `.md`, no leading slash) so they resolve in the rendered wiki.
- **Flag unfinished ports** with an inline `<!-- TODO -->` when a page links to something not yet migrated (see the `Contributing-Code-Reviews` reference in the First Contribution page).

> **Porting a page from the Confluence backup?** The origin story and step-by-step recovery instructions live in [About This Wiki](About-This-Wiki.md).

---

## GitHub wiki conventions

As more pages are ported, keep them aligned with how GitHub wikis work:

- **Flat namespace.** The wiki UI does not show folders; hierarchy lives in page names and in curated navigation.
- **`Home.md`** is the landing page and top-level index.
- **`_Sidebar.md`** (recommended next step) provides grouped navigation shown on every page — this replaces Confluence's page tree.
- **`_Footer.md`** (optional) shows license/community links on every page.
- **Spaces vs. hyphens:** GitHub maps `-` in filenames to spaces in titles, so prefer hyphenated names over literal spaces.

---

## License

Content is licensed under the [Apache License 2.0](LICENSE).
