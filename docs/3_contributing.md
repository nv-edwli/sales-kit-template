# Contributing

All feedback and contributions to this project are welcome. When making changes to this project, either for personal use or for contributing, it is recomended to work on a fork on this project. Once the changes have been completed on the fork, a Merge Request should be opened.

## Updating documentation

Documentation is written in Github Flavored Markdown and then rendered to a final Markdown file by Pandoc. The documentation can be previewed in the Workbench file browser window.

### Table of Contents file

The most important file for the documentation is the table of contents file at `docs/_TOC.md`. This file defines a list of files that should be concatenated in order to generate the final README manual. Files must be on this list to be included.

### Header file

The only exception to the table of contents rule is the header file at `docs/_HEADER.md`. This file will preprend the README manual and exists before the Table of Contents. It will always be included and should not be included in the table of contents file.

### Static Content

Save all static content, including images, to the `_static` folder. This will help with organization.

### Dynamic documentation

It may be helpful to have documents that update and write themselves. To create a dynamic document, simply create an executable file that writes the Markdown formatted document to stdout. During build time, if an entry in the table of contents file is executable, it will be executed and its stdout will be used in its place.

### Rendering documentation

`Make` is used to manage the generation of the `README.md` file. Running the following make commands from the `docs/` directory will perform the following actions.

- `make` or `make ../README.md` will update the README file if any of the pages have changed since it was last generated.

- `make clean` will cleanup the existing README and static assets.

- `make all` will force the generation of the README manual.
# Managing your Development Environment

## Environment Variables

Most of the configuration for the development environment happens with Environment Variables. To make permanent changes to environment variables, modify [`variables.env`](./variables.env) or use the Workbench UI.

## Python Environment Packages

This project uses one Python environment at `/usr/bin/python3` and dependencies are managed with `pip`. Becuse all development is done inside a container, any changes to the Python environment will be ephemeral. To permanently install a Python package, add it to the [`requirements.txt`](./requirements.txt) file or use the Workbench UI.

## Operating System Configuration

The development environment is based on Ubuntu 22.04. The primary user has password-less sudo access, but all changes to the system will be ephemeral. To make permanent changes to installed packages, add them to the [`apt.txt`] file. To make other changes to the operating system such as manipulating files, adding environment variables, etc; use the [`postBuild.bash`](./postBuild.bash) and [`preBuild.bash`](./preBuild.bash) files.
