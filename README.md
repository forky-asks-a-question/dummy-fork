# dummy-action

This template can be used to quickly start a new custom js action repository.  Click the `Use this template` button at the top to get started.

## Index

- [Inputs](#inputs)
- [Outputs](#outputs)
- [Usage Examples](#usage-examples)
- [Contributing](#contributing)
  - [Incrementing the Version](#incrementing-the-version)
  - [Recompiling Manually](#recompiling-manually)
  - [Updating the README.md](#updating-the-readmemd)
- [Code of Conduct](#code-of-conduct)
- [License](#license)

## Inputs

| Parameter | Is Required | Default | Description           |
|-----------|-------------|---------|-----------------------|
| `input`   | true        |         | Description goes here |

## Outputs

| Output   | Description           | Possible Values |
|----------|-----------------------|-----------------|
| `output` | Description goes here |                 |

## Usage Examples

```yml
jobs:
  jobname: # TODO: fix the job name
    runs-on: ubuntu-20.04
    steps:
      - uses: actions/checkout@v3

      - name: 'Try it once'
        uses: im-open/dummy@v1.0.0
        with:
          input: ''
      - name: 'Try it again'
        uses: im-open/dummy@v1.0.0
        with:
          input: ''
```

## Contributing

When creating new PRs from a fork please review the following items:
| PR Contribution Requirements/Tasks                                                                                                                    | Required<br/>for Branches | Required<br/>for Forks |
|-------------------------------------------------------------------------------------------------------------------------------------------------------|:-------------------------:|:----------------------:|
| The action code does not contain sensitive information.                                                                                               |            Yes            |          Yes           |
| For major or minor changes, at least one of the commit messages contains the appropriate `+semver:` keywords listed under [Incrementing the Version]. |            Yes            |          Yes           |
| The action has been re-compiled.  See [Recompiling Manually] for more details.                                                                        |            No*            |          Yes           |
| The README.md action versions have been updated.  See [Updating the README.md] for details.                                                           |            No*            |          Yes           |

\* When a pull request is created from a branch, the build workflow will automatically recompile the action, update the README.md with the next version and push a commit to the branch if those changes have not already been made.

### Incrementing the Version

This repo uses [git-version-lite] in its build and PR merge workflows to examine commit messages to determine whether to perform a major, minor or patch increment on merge.  The following table provides the fragment that should be included in a commit message to active different increment strategies.

| Increment Type | Commit Message Fragment                     |
|----------------|---------------------------------------------|
| major          | +semver:breaking                            |
| major          | +semver:major                               |
| minor          | +semver:feature                             |
| minor          | +semver:minor                               |
| patch          | *default increment type, no comment needed* |

If a contributor is unsure what the next version will be, create a PR and the first build workflow that runs will calculate the value.

### Recompiling Manually

If changes are made to the action's code in this repository, or its dependencies, the action can be re-compiled by running the following command:

```sh
# Installs dependencies and bundles the code
npm run build

# Bundle the code (if dependencies are already installed)
npm run bundle
```

These commands utilize [esbuild] to bundle the action and its dependencies into a single file located in the `dist` folder.

This step does not need to be completed if only ancillary files like the README.md have been changed.

If a pull request is made from a branch, this step will be automatically performed by the build workflow unless the PR author has already done so.  Pull requests made from forked repositories will need to perform this step manually.  

### Updating the README.md

If changes are made to the action's source code, the README.md file should be updated to reflect the next version of the action.  Each instance of the action in the examples should be updated.  This helps users know what the latest tag is without having to navigate to the Tags page of the repository.

This step does not need to be completed if only ancillary files like the README.md have been changed.

If a pull request is made from a branch, this step will be automatically performed by the build workflow unless the PR author has already done so.  Pull requests made from forked repositories will need to perform this step manually.  See [Incrementing the Version] for details on how to determine what the next version will be.

## Code of Conduct

This project has adopted the [im-open's Code of Conduct](https://github.com/im-open/.github/blob/main/CODE_OF_CONDUCT.md).

## License

Copyright &copy; 2023, Extend Health, LLC. Code released under the [MIT license](LICENSE).

[git-version-lite]: https://github.com/im-open/git-version-lite
[esbuild]: https://esbuild.github.io/getting-started/#bundling-for-node
[Incrementing the Version]: #incrementing-the-version
[Recompiling Manually]: #recompiling-manually
[Updating the README.md]: #updating-the-readmemd
