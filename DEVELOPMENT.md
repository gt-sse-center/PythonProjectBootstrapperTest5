# Local Development

This document describes the following development activities:
- [Enlistment](#enlistment)
- [Formatting](#formatting)
- [Static Code Analysis](#static-code-analysis)
- [Testing](#testing)
- [Semantic Version Generation](#semantic-version-generation)
- [Python Package Creation](#python-package-creation)
- [Python Package Publishing](#python-package-publishing)
- [Building Executables](#building-binaries)
- [Development Docker Image](#development-docker-image)

## Enlistment
Enlistment in this repository involves:

| Step | Command Line | Description |
| --- | --- | --- |
| 1. Clone the repository locally          | `git clone https://github.com/gt-sse-center/PythonProjectBootstrapperTest5`                                                                                                                           | https://git-scm.com/docs/git-clone                                                                                                                    |
| 2. Bootstrap the repository              | <table><tr><td>Linux / MacOS:</td><td><code>Bootstrap.sh [--python-version <python version>] [--package]</code></td></tr><tr><td>Windows:</td><td><code>Bootstrap.cmd [--python-version <python version> [--package]</code></td></tr></table> | Prepares the repository for local development by enlisting in all dependencies.                                                                       |
| 3. Activate the environment              | <table><tr><td>Linux / MacOS:</td><td><code>. ./Activate.sh</code></td></tr><tr><td>Windows:</td><td><code>Activate.cmd</code></td></tr></table>                                                                                              | Activates the terminal for development. Each new terminal window must be activated.                                                                   |
| 4. [Optional] Deactivate the environment | <table><tr><td>Linux / MacOS:</td><td><code>. ./Deactivate.sh</code></td></tr><tr><td>Windows:</td><td><code>Deactivate.cmd</code></td></tr></table>                                                                                          | Deactivates the terminal environment. Deactivating is optional, as the terminal window itself may be closed when development activities are complete. |

## Formatting
Code is formatted using [black](https://github.com/psf/black) based on settings in [pyproject.toml](https://github.com/gt-sse-center/PythonProjectBootstrapperTest5/blob/main/pyproject.toml).

Run `python Build.py black` to validate that your code is formatted correctly. This validation is enforced by a [Continuous Integration workflow](https://github.com/gt-sse-center/PythonProjectBootstrapperTest5/blob/main/.github/workflows/standard.yaml).

Run `python Build.py black --format` to format your code.

## Static Code Analysis
Code is validated using [pylint](https://github.com/pylint-dev/pylint) based on settings in [pyproject.toml](https://github.com/gt-sse-center/PythonProjectBootstrapperTest5/blob/main/pyproject.toml).

Run `python Build.py pylint` to perform this validation. This validation is enforced by a [Continuous Integration workflow](https://github.com/gt-sse-center/PythonProjectBootstrapperTest5/blob/main/.github/workflows/standard.yaml). The minimum linting score can be found in [Build.py](https://github.com/gt-sse-center/PythonProjectBootstrapperTest5/blob/main/Build.py).

## Testing
Automated tests are run using [pytest](https://docs.pytest.org/) and code coverage information is extracted using [coverage](https://coverage.readthedocs.io/) based on settings in [pyproject.toml](https://github.com/gt-sse-center/PythonProjectBootstrapperTest5/blob/main/pyproject.toml).

Run `python Build.py pytest [--code-coverage]` to execute these tests. This validation is enforced by a [Continuous Integration workflow](https://github.com/gt-sse-center/PythonProjectBootstrapperTest5/blob/main/.github/workflows/standard.yaml). The minimum code coverage percentage can be found in [Build.py](https://github.com/gt-sse-center/PythonProjectBootstrapperTest5/blob/main/Build.py).

## Semantic Version Generation
[Semantic Versions](https://semver.org) are generated based on git commits using [AutoGitSemVer](https://github.com/davidbrownell/AutoGitSemVer). Version information is stored [here](https://github.com/gt-sse-center/PythonProjectBootstrapperTest5/blob/main/src/PythonProjectBootstrapperTest5/__init__.py).

Run `python Build.py update_version` if you want to update this version locally. However, keep in mind that the version will be automatically updated by a [Continuous Integration workflow](https://github.com/gt-sse-center/PythonProjectBootstrapperTest5/blob/main/.github/workflows/standard.yaml) and there should never be a need to manage the version manually.

## Python Package Creation
Python packages are created using [setuptools](https://github.com/pypa/setuptools) based on settings in [pyproject.toml](https://github.com/gt-sse-center/PythonProjectBootstrapperTest5/blob/main/pyproject.toml).

Run `python Build.py package` if you want to build a python wheel locally. Packages are created by a [Continuous Integration workflow](https://github.com/gt-sse-center/PythonProjectBootstrapperTest5/blob/main/.github/workflows/standard.yaml).

## Python Package Publishing
Python packages are published to [PyPi](https://pypi.org) as part of a [Continuous Integration workflow](https://github.com/gt-sse-center/PythonProjectBootstrapperTest5/blob/main/.github/workflows/standard.yaml).

Run `python Build.py publish <pypi_api_token> [--production]` if you want to publish a package build locally (this is not recommended).

## Building Binaries
Python binaries are created using [cx_Freeze](https://cx-freeze.readthedocs.io/) for Linux, MacOS, and Windows by a [Continuous Integration workflow](https://github.com/gt-sse-center/PythonProjectBootstrapperTest5/blob/main/.github/workflows/standard.yaml).

Run `python Build.py build_binaries` locally to create a binary for your current operating system.

## Development Docker Image
A [docker](https://docker.com) image for a bootstrapped development environment is created as part of a [Continuous Integration workflow](https://github.com/gt-sse-center/PythonProjectBootstrapperTest5/blob/main/.github/workflows/standard.yaml). This functionality can be useful when adhering to the [FAIR principles for research software](https://doi.org/10.1038/s41597-022-01710-x) by creating a development environment and its dependencies as they existed at the moment when the image was created.

Run `python Build.py create_docker_image` locally to create a development docker image.

