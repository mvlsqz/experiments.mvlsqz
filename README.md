# Ansible Collections - Learning
These are my personal notes and learning material for Ansible Collections. It
also includes some practical examples, that demonstrate how to create, use and
test Ansible Collections, roles or playbooks.

# Environment Setup
To run the examples in this repository, you need to have the following tooling
available on your system:

## Python version management
Environment isolation is very important when working with Python projects, as
mixing of python versions and packages can lead to unexpected result of
failures, for that mater this project rely on `pyenv` and Python's `venv` module to
manage python versions and virtual environments.

## About `pyenv`
### Installation
In order to have `pyenv` available on your system, you can follow the official
guide on the official [GitHub](https://github.com/pyenv/pyenv) repository, and follow the installation instructions for your platform.

### Python 3.10
This project uses Python 3.10, but in theory you can use any Python version
later than 3.10, for sake of consistency, I recommend to use Python 3.10. But
I leave that up to you.

```bash
pyenv install 3.10
```

### pipx
The project uses pipx to install some python based CLI tooling to follow the
principle of isolating dependencies, so you don't end up with a mess of packages

To install pipx, you can follow the official guide on the official [Installation Guide](pipx.pypa.io/stable/installation)
### poetry for project specific dependencies
Again, to follow the principle of isolating dependencies, this project uses
`poetry` tool to manage project specific dependencies, to have them described in
the `pyproject.toml` file and ensure that the same versions are used across
different examples or implementations.

To install poetry, you can use pipx:

```bash
$ pipx install poetry
```

## Prepare the environment

To Setup the local python version for this project:

```bash
$ pyenv local 3.10
# to verify
$ python --version
Python 3.10.18
```

To create the virtual environment for this project:

```bash
$ python -m venv .ansible
```
Then to activate the virtual environment:

```bash
source .ansible/bin/activate
```

Finally, to install the project specific dependencies:

```bash
poetry install
```

## Python libraries
This project mostly on the `adt` (Ansible Development Tool) library, which is a suite
that helps to create, manage and test Ansible Collections, roles and playbooks.

To see what is included as tooling within the `adt` library, you can run:

```bash
collections adt --version
 ansible-builder                          3.1.0
 ansible-core                             2.17.13
 ansible-creator                          25.8.0
 ansible-dev-environment                  25.8.0
 ansible-dev-tools                        25.8.3
 ansible-lint                             25.8.2
 ansible-navigator                        25.8.0
 ansible-sign                             0.1.2
 molecule                                 25.7.0
 pytest-ansible                           25.8.0
 tox-ansible                              25.8.0
```

It will have a reasonable set of tools to work with Ansible Collections, the
versions can be customized via the `pyproject.toml` file, but the recommendation
is to stick with the versions that are known to work well together.

## Test environment setup
To run proper testings we will use `molecule` in combination with docker/podman
to run our E2E tests, so you need to have either docker or podman installed.

### Set collections path
By default, Ansible will look for collections in the `~/.ansible/collections`
but it will require to install the collections there, which is not ideal for
testing purposes, so we will set the `ANSIBLE_COLLECTIONS_PATHS` to a folder
that we can delete and recreate as needed.

```bash
export ANSIBLE_COLLECTIONS_PATHS=$PWD/.ansible/collections
mkdir -p $ANSIBLE_COLLECTIONS_PATHS
```

## Cleanup
Many of the commands above will leave files and folders behind, that you might
want to ignore from your repository, so here is included a basic `.gitignore`
file but chances are that other files and folders will be created that you want
to ignore, so feel free to customize it as needed.
