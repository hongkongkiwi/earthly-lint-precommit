# Earthly-Lint Pre-Commit Hook

This repository contains a custom pre-commit hook that lints Earthfiles using `earthly ls`. The hook ensures that any Earthfiles in your project are formatted and syntactically correct before committing or merging changes.

## Table of Contents
- [Overview](#overview)
- [Installation](#installation)
- [Usage](#usage)
- [Configuration](#configuration)
- [Contributing](#contributing)
- [License](#license)

## Overview

The Earthly-Lint pre-commit hook will automatically lint any Earthfiles in your project. It can be executed at various stages of your Git workflow, including pre-commit, pre-merge-commit, and manual execution.

Any file named "Earthfile" will be scanned not just the root Earthfile. So this also supports projects which have IMPORT statements to include multiple Earthfile's (as supported in earthly 0.8).

We do this via the `earthly ls` command and ignore the results. This command performs linting for us (although it's a tad slow compared to something like the [earthly language server](https://github.com/glehmann/earthlyls)).

## Installation

To use Earthly-Lint, you need to install `pre-commit` and add this hook to your `.pre-commit-config.yaml` file.

1. First, install pre-commit if you haven't already:

    ```sh
    pip install pre-commit
    ```

2. Create a `.pre-commit-config.yaml` file in the root of your repository (if not already present) and add the following configuration:

```yaml
repos:
  - repo: https://github.com/hongkongkiwi/earthly-lint-precommit.git
    rev: v0.0.3
    hooks:
      - id: earthly-lint
        verbose: false
```

3. Install the pre-commit hooks:

```sh
pre-commit install
```

## Usage

Once installed, the Earthly-Lint hook will automatically lint Earthfiles during the configured Git stages.

To manually run all pre-commit hooks on all files:

```sh
pre-commit run --all-files
```

If you want to show verbose output (meaning show all passes as well) then add `verbose: true` to the hook config.


## Contributing

If you'd like to contribute, please fork the repository and use a feature branch. Pull requests are warmly welcome.

1. Fork the repo
2. Create a feature branch: `git checkout -b new-feature`
3. Commit your changes: `git commit -am 'Add new feature'`
4. Push to the branch: `git push origin new-feature`
5. Create a new Pull Request

## License

This project is licensed under the MIT License. See the LICENSE file for more information.
