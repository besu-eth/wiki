# About This Wiki

This is the project wiki for [Hyperledger Besu](https://github.com/besu-eth/besu) — a home for contributor guides, project process, and reference material for people working on Besu.

## How this wiki is maintained

You're reading the *rendered* wiki. Its pages are **not edited here**. They're published from a source repository, [`besu-eth/wiki`](https://github.com/besu-eth/wiki), where every change goes through pull-request review and is then pushed to this wiki automatically. See that repo's README for the full editing and deployment workflow.

If you spot something to fix or add, open a pull request against [`besu-eth/wiki`](https://github.com/besu-eth/wiki) rather than editing the wiki directly — direct wiki edits would be overwritten on the next publish.

## Origin: the Confluence export

Most of these pages began life in a Hyperledger Confluence instance and were exported in bulk (the "Export 30 SEP 2025" snapshot). That raw export was deeply nested and full of Confluence-specific markup, so pages are being ported to clean, flat GitHub-wiki pages **one at a time** rather than dumped in wholesale.

The complete original export is preserved, read-only, on the **`confluenceExport` branch** of the source repo. The published wiki contains only pages that have been deliberately ported and cleaned up — so if a topic you expect is missing, it likely still lives in that backup awaiting a port.

## Continuing the migration

To port another page out of the Confluence backup:

1. **Clone the source repo** [`besu-eth/wiki`](https://github.com/besu-eth/wiki) and branch off `main`:
   ```bash
   git switch -c docs/port-<page>
   ```
2. **Find and pull the page** from the backup branch (the export lives under `besu/`):
   ```bash
   # browse what exists
   git ls-tree -r --name-only confluenceExport -- besu/

   # pull a single file onto your branch
   git checkout confluenceExport -- besu/path/to/page.md
   ```
3. **Move and rename** it to a flat, root-level wiki page using `Hyphen-Separated-Words.md` — the filename becomes the page title (e.g. `Working-through-Hive-tests.md` → "Working through Hive tests").
4. **Clean up Confluence artifacts:** leftover macros, broken `lf-hyperledger.atlassian.net` links, and "export flag not set" boilerplate.
5. **Fix cross-links** to use bare page names, e.g. `[First Contribution](Contributing-First-Contribution)` (no `.md`, no leading slash).
6. **Surface the page** by adding it to `_Sidebar.md` (and linking from [Home](Home) where appropriate), then open a PR.

When a ported page links to something not yet migrated, leave an inline `<!-- TODO -->` marking it (see the `Contributing-Code-Reviews` reference in [First Contribution](Contributing-First-Contribution)).
