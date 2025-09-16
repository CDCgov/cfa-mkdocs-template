# mkdocs template repo

## Overview

[mkdocs](https://www.mkdocs.org/) is a tool for building simple static documentation from Markdown files, with extensions allowing for:

- Auto-generating Python API documentation
- Deploying documents to GitHub Pages

See an example of what you can build on the GitHub Pages site for this repo: <https://cdcent.github.io/cfa-mkdocs-template>

## Getting started

### Essentials

To use this template, you'll need to copy over these files:

- `mkdocs.yaml`: Configure this file to account for your document structure, repo URL, etc.
- `docs/index.md`: You will always want an `index.md`. You can add other `.md`s under `docs/`.

The Python dependencies are in `requirements.txt`. For example, if you are using [uv](https://docs.astral.sh/uv), you could run:

    uv add --dev $(cat requirements.txt)

There is no need to keep this file in your repo.

The `.gitignore` in this repo has just one entry, `site/`, which is the default location where `mkdocs build` will put locally built docs.

You should now be able to `mkdocs serve` and `mkdocs build`!

### Optional things

#### YAML checking bugs

Some of the Markdown extensions in `mkdocs.yaml` are "unsafe" and will trip the pre-commit hook `check-yaml`. You can remove these extension, ignore this file in the hook configuration with `exclude: "mkdocs.yaml"`, or add `args: ["--unsafe"]` to the pre-commit hook.

#### Math rendering

`docs/javascript/katex.js` provides math rendering. It is referenced in `mkdocs.yaml`.

See the [mkdocs-material](https://squidfunk.github.io/mkdocs-material/reference/math/) for information on math rendering.

Note that rendering ` ```math ` blocks requires a "superfences" option in `mkdocs.yaml`.

#### API docs autogeneration

`docs/api.md` gives you an example of how to use [mkdocstrings](https://mkdocstrings.github.io/) to generate API documentation from doc strings.

#### GitHub continuous integration

`.github/workflows/mkdocs.yaml` runs two jobs. On each PR and push to main, check that `mkdocs build` runs without error, and upload a copy of the build docs. On a push to main, deploy those built docs to GitHub Pages.

Note that `mkdocs gh-deploy` uses the older strategy of using GitHub Pages, by pushing to a `gh-pages` branch. The action in this repo uses artifacts instead. See the [GitHub documentation](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site#publishing-with-a-custom-github-actions-workflow) for more details.

## Deployment

`mkdocs gh-deploy` should just work, _whether your repo is on CDCGov or CDCEnt_. For repos on CDCGov, this will make a publicly-available website at `cdcgov.github.io/[repo]/`.

> [!CAUTION] Publicly-available websites should only by used for documentation of software developed in the corresponding repository. See the [Git and GitHub practices](github.md) page for more information on public documentation.

If your repo is on CDCEnt, a redirect will be made to a website only accessible with the appropriate credentials. That is, `cdcent.github.io/[repo]/` will redirect to an automatically generated site name (e.g., `potential-adventure-637em36.pages.github.io/`). You will only be able to access this it you are logged in and can access repos on CDCEnt.

## Contributing to this template

- These files are a skeleton so that the API documentation can build:
  - `mkdtemp/`
- These files are to check that `mkdocs` runs and the template builds in this template repo:
  - `uv.lock`
  - `pyproject.toml`

## Project Admin

- Scott Olesen <ulp7@cdc.gov> (CDC/IOD/ORR/CFA)

---

## General Disclaimer

This repository was created for use by CDC programs to collaborate on public health related projects in support of the [CDC mission](https://www.cdc.gov/about/organization/mission.htm). GitHub is not hosted by the CDC, but is a third party website used by CDC and its partners to share information and collaborate on software. CDC use of GitHub does not imply an endorsement of any one particular service, product, or enterprise.

## Public Domain Standard Notice

This repository constitutes a work of the United States Government and is not subject to domestic copyright protection under 17 USC § 105. This repository is in the public domain within the United States, and copyright and related rights in the work worldwide are waived through the [CC0 1.0 Universal public domain dedication](https://creativecommons.org/publicdomain/zero/1.0/). All contributions to this repository will be released under the CC0 dedication. By submitting a pull request you are agreeing to comply with this waiver of copyright interest.

## License Standard Notice

This repository is licensed under ASL v2 or later.

This source code in this repository is free: you can redistribute it and/or modify it under the terms of the Apache Software License version 2, or (at your option) any later version.

This source code in this repository is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the Apache Software License for more details.

You should have received a copy of the Apache Software License along with this program. If not, see http://www.apache.org/licenses/LICENSE-2.0.html

The source code forked from other open source projects will inherit its license.

## Privacy Standard Notice

This repository contains only non-sensitive, publicly available data and information. All material and community participation is covered by the [Disclaimer](https://github.com/CDCgov/template/blob/master/DISCLAIMER.md) and [Code of Conduct](https://github.com/CDCgov/template/blob/master/code-of-conduct.md). For more information about CDC's privacy policy, please visit [http://www.cdc.gov/other/privacy.html](https://www.cdc.gov/other/privacy.html).

## Contributing Standard Notice

Anyone is encouraged to contribute to the repository by [forking](https://help.github.com/articles/fork-a-repo) and submitting a pull request. (If you are new to GitHub, you might start with a [basic tutorial](https://help.github.com/articles/set-up-git).) By contributing to this project, you grant a world-wide, royalty-free, perpetual, irrevocable, non-exclusive, transferable license to all users under the terms of the [Apache Software License v2](http://www.apache.org/licenses/LICENSE-2.0.html) or later.

All comments, messages, pull requests, and other submissions received through CDC including this GitHub page may be subject to applicable federal law, including but not limited to the Federal Records Act, and may be archived. Learn more at [http://www.cdc.gov/other/privacy.html](http://www.cdc.gov/other/privacy.html).

## Records Management Standard Notice

This repository is not a source of government records but is a copy to increase collaboration and collaborative potential. All government records will be published through the [CDC web site](http://www.cdc.gov).
