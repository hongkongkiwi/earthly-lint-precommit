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

## Installation

To use Earthly-Lint, you need to install `pre-commit` and add this hook to your `.pre-commit-config.yaml` file.

1. First, install pre-commit if you haven't already:

    ```sh
    pip install pre-commit
    ```

2. Create a `.pre-commit-config.yaml` file in the root of your repository (if not already present) and add the following configuration:

    ```yaml
    - repo: git@github.com:yourusername/your-repo.git  # Replace with your repo URL
      rev: v1.0.0  # Replace with the latest version or a specific commit SHA
      hooks:
        - id: earthly-lint
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

## Configuration

The pre-commit hook configuration used for Earthly-Lint looks like this:

```yaml
- id: earthly-lint
  name: Lint earthly Earthfile's
  description: This hook lints any Earthfiles in the project using earthly ls
  entry: hooks/earthly-lint
  language: script
  stages: [pre-commit, pre-merge-commit, manual]
  files: "Earthfile"
  pass_filenames: true
```

- id: A unique identifier for the hook.
- name: A human-readable name for the hook.
- description: A brief description of what the hook does.
- entry: The command to run for the hook.
- language: The type of script used.
- stages: The Git stages at which the hook is run.
- files: Specifies the files to be checked by the hook.
- pass_filenames: Whether to pass filenames to the entry command.

## Contributing

If you'd like to contribute, please fork the repository and use a feature branch. Pull requests are warmly welcome.

1. Fork the repo
2. Create a feature branch: `git checkout -b new-feature`
3. Commit your changes: `git commit -am 'Add new feature'`
4. Push to the branch: `git push origin new-feature`
5. Create a new Pull Request

## License

This project is licensed under the MIT License. See the LICENSE file for more information.
