# Documentation contribution workflow

The following guidelines explain how to contribute to the [Besu documentation repository](https://github.com/hyperledger/besu-docs).

## Your first contribution

Start by looking for [issues](https://github.com/hyperledger/besu-docs/contribute/) that have a **Good First Issue** label. **Good First Issues** might require only a few lines of documentation, or have enough information for a newcomer to easily document.

When you’ve identified an issue you want to work on, assign it to yourself, or message us on the [Besu Discord](https://discord.gg/hyperledger) and we’ll assign it to you.

## Contribution workflow

The Besu documentation uses a [docs-as-code](https://www.writethedocs.org/guide/docs-as-code/) approach, meaning documentation is created using the same tools as code. The contribution workflow involves proposing changes to the docs by creating [forks and pull requests (PRs)](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/getting-started/about-collaborative-development-models#fork-and-pull-model) on the documentation GitHub repository. This facilitates open contributions, testing, and review.

To contribute changes:

1. [Fork](https://docs.github.com/en/get-started/quickstart/fork-a-repo) the Besu documentation repository.
2. [Clone](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository) your fork to your computer.
  - `git clone <FORKED-REPO>`
  - `cd besu-docs`
3. [Add an upstream remote](https://docs.github.com/en/github/collaborating-with-pull-requests/working-with-forks/configuring-a-remote-for-a-fork).
  - `git remote add upstream <ORIGINAL-REPO>`
4. [Create and checkout a topic branch](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging), naming it appropriately. We recommend using the issue number and short description, which is a reminder to fix only one issue in a PR. For example, `183-doc-cli-option`.
  - `git checkout -b <ISSUE-NUM>-<ISSUE-DESC>`
5. Open the Besu documentation repository in a text editor of your choice (for example, [VS Code](https://code.visualstudio.com/)) and make your changes to the documentation content located in the `/docs`  folder. Make sure to [follow the style guidelines](https://docs-template.consensys.net/contribute/style-guide) and [format your Markdown correctly](https://docs-template.consensys.net/contribute/format-markdown). If you delete, rename, or move a documentation file, make sure to add a [redirect](https://docs-template.consensys.net/create/configure-docusaurus#redirects).
6. [Preview your changes locally](https://docs-template.consensys.net/contribute/preview) to check that the changes render correctly. Make sure you switch to the **development** version of the docs in the preview.
7. Add and commit your changes, using a clear commit message. Make sure to add a [DCO message](https://lf-hyperledger.atlassian.net/wiki/display/BESU/DCO) to each commit. Push your changes to your remote fork (usually named `origin`).
  - `git add *`
  - `git commit -m "<COMMIT-MESSAGE>"`
  - `git push origin`
8. Navigate to the [original Besu documentation repository](https://github.com/hyperledger/besu-docs), and you’ll see a banner prompting you to create a PR with your recent changes. Create a PR, filling out the description according to the template. Remember to [link the issue](https://help.github.com/en/github/managing-your-work-on-github/linking-a-pull-request-to-an-issue) that the PR fixes in the description.
  - `fixes #<ISSUE-NUM>`
9. The bottom of the PR page displays a list of checks that verify links, Markdown syntax, and more. If you have any errors, make any required changes to your PR, repeating steps 5-7. If you want to include a new word that causes a spell check error, you can add that word to the `project-words.txt` file.
10. In the right sidebar of your PR, select the reviewer(s) who should review your PR (typically the original issue raiser). If you don’t know who to choose or can’t because you’re not a maintainer yet, select the reviewers listed by GitHub or keep the default value.
11. Make any required changes to your PR based on reviewer feedback, repeating steps 5-7.
12. After your PR is validated, all checks have passed, and your branch has no conflicts with the target branch, you can merge your PR. You can delete the topic branch after merging your PR.

*Tip: You can use a Git client such as [Fork](https://fork.dev/) instead of the command line.*

*Note: The Besu documentation repository default branch is now named main.*