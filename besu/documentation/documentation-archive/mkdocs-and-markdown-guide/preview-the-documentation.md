# Preview the documentation

Preview the Besu documentation with MkDocs on your local machine and on Read the Docs.

## Preview locally

We recommend previewing your work locally before pushing your changes in a PR. Since the final documentation is built with MkDocs, you must build the documentation locally with MkDocs to ensure the Markdown is correctly rendered. To preview the documentation locally:

1. [Install Python 3](https://www.python.org/downloads/).
2. Create a virtual environment for the project:
  - ```
python3 -m venv env
```
3. Activate the virtual environment:
  - ```
source env/bin/activate
```
  - An (env) now appears at the beginning of your prompt.
4. Install all the required dependencies in this virtual environment.  
We use two requirements files because we have an [insider (sponsored) version of material design theme](https://squidfunk.github.io/mkdocs-material/insiders/) and only readthedocs preview and build can use it.  
You will have to use the non insider version for local preview. There's a few differences but it's mostly compatible and a good smoke test. The real preview is rendered in the PR, see next section.  
The requirements.txt is for the common dependencies, the requirements-mkdocs-material.txt is for installing the mkdocs material theme.  
Run command with both requirement files:
  - ```
pip install -r CI/requirements.txt -r CI/requirements-mkdocs-material.txt
```
5. Run the following command in the project directory:
  - ```
mkdocs serve
```
6. In the output of this command, follow the link displayed on the line that looks like the following:
  - ```
[I 190206 18:48:47 server:298] Serving on http://127.0.0.1:8000
```
  - In this case, go to `[http://127.0.0.1:8000](http://127.0.0.1:8000)`. You can let this server run while you work on the documentation. It updates the local website automatically when you save changes in your Markdown files.
7. Deactivate the virtual environment if you work on another Python project, by running `deactivate`. You can preview the same documentation site again starting from step 3 and skipping step 4, until you update Python.

## Preview on Read the Docs

When you create a PR on a documentation repository, the PR triggers [CircleCI](https://circleci.com/) checks to verify links, Markdown syntax, writing style, and more. The documentation is also built on [Read the Docs (RTD)](https://readthedocs.org/) as a PR preview. This preview uses the [insider version of material theme for MkDocs](https://squidfunk.github.io/mkdocs-material/insiders/).

You can find the link to this preview in the checklist at the bottom of your PR page. The preview only works for registered and permitted RTD users. Ask for help on [Discord](https://discord.gg/hyperledger) if needed.

![PR checklist containing preview link](https://consensys.net/docs/doctools/en/latest/assets/images/rtd_pr_preview.png)