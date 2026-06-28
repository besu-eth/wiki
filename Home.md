This is the project wiki for [Besu](https://github.com/besu-eth/besu). It's a home for contributor guides, project process, and reference material for people working on Besu.

## Besu overview

Besu project status:

- **Status**                 : Graduated
- **OpenSSF Best Practices** : [![OpenSSF Best Practices](https://www.bestpractices.dev/projects/3174/badge)](https://www.bestpractices.dev/projects/3174)
- **Community**              : [Discord](https://discord.com/invite/hyperledger) (`#besu`, `#besu-contributors`)
- **Documentation**          : [docs.besu-eth.org](https://docs.besu-eth.org/)
- **Repositories**           : [besu-eth/besu](https://github.com/besu-eth/besu), [besu-eth/besu-docs](https://github.com/besu-eth/besu-docs)

Besu is an open source Ethereum client developed under the Apache 2.0 license and written in Java. It runs on public Ethereum networks, private permissioned networks, and test networks.

Core capabilities include:

- Ethereum Virtual Machine (EVM)
- Consensus support, including Proof of Stake and Proof of Authority variants (IBFT 2.0, QBFT)
- User-facing APIs (JSON-RPC over HTTP/WebSocket and GraphQL)
- Plugin architecture for extending Besu behavior
- Monitoring integrations and metrics endpoints

View the [Besu documentation](https://docs.besu-eth.org/) to get started with
public networks, private networks, plugins, and configuration.

## About this wiki

This wiki is maintained from the [`besu-eth/wiki`](https://github.com/besu-eth/wiki)
source repository. Changes are reviewed through pull requests and then published
to the rendered [Besu wiki](https://github.com/besu-eth/besu/wiki). If you spot
something to fix or add, open a pull request against the source repo rather than
editing the rendered wiki directly. Direct wiki edits are overwritten on the
next publish.

Most pages began as a Hyperledger Confluence export and are being ported one
topic at a time into clean GitHub wiki pages. The full raw export is preserved
on the [`confluenceExport`](https://github.com/besu-eth/wiki/tree/confluenceExport)
branch. If a topic you expect is missing, it likely still lives in that backup
awaiting a port.

### Continuing the wiki migration

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

3. **Move and rename** it to a flat, root-level wiki page using `Hyphen-Separated-Words.md`. The filename becomes the page title (for example, `Working-through-Hive-tests.md` becomes "Working through Hive tests").
4. **Clean up Confluence artifacts:** leftover macros, broken `lf-hyperledger.atlassian.net` links, and "export flag not set" boilerplate.
5. **Fix cross-links** to use bare page names, for example `[Working with DCO](Contributing-Working-with-DCO)` (no `.md`, no leading slash).
6. **Surface the page** by adding it to `_Sidebar.md` (and linking from [Home](Home) where appropriate), then open a PR.

When a ported page links to something not yet migrated, leave an inline `<!-- TODO -->` marking it.