# QC-Devs Maintainer Guide

## Introduction

This document discusses our default repository setup.
It can be used as a set of step-by-step instructions for starting a new repository
or upgrading an existing one.
The goal is to achieve more consistency across all [QC-Devs](https://qcdevs.org/) projects,
and to provide tools to make your repository welcoming to contributions
in a way that is consistent with our
[Contributor Guide](CONTRIBUTING.md) and [Code of Conduct](CODE_OF_CONDUCT.md).

This guide is a modular collection of mini-tutorials
for setting up your repository and learning best practices.
As with all of our work, contributions to this document are welcome.

## Repository Setup

### A. Minimal Repository

The [Minimal Initial Repository](maintaining/minimal.md) walks you through the first steps
of setting up a Git repository (locally and on GitHub)
and adding a few files that should always be present.
This is only the minimal setup,
meaning that more files will be added in the following mini-tutorials,
if they apply to your use case, such setting up a Python package.


### B. Project-specific Steps

There are several types of repositories, and each comes with its own set of recommendations:

1. Python packages

    - Setuptools (TODO)
    - Recommended Packages to facilitate developemnt (TODO)

2. Research Project

    - Reproducible Python environment with pip-tools (TODO)


### C. Continuous Integration

A good continuous integration setup lowers the maintenance burden
and automates part of the review process.

- [Pre-commit](maintaining/pre-commit.md) is strongly recommended for any type of project,
  and therefore included in the minimal setup.
  This tutorial documents the integration with [pre-commit.ci](http://pre-commit.ci/).
- Unit testing (TODO)
- Code coverage (TODO)
- Documentation build and deployment (TODO)
- Deployment on PyPI (TODO)
- Deepsource analysis (TODO)
- Sourcery AI pull request review (TODO)


### D. Documentation

Documentation is always useful, for which we have several recommendations.
They can be combined, but don't have to:

- Changelogs (TODO)
- Sphinkx (TODO)
- Jupyter Book (TODO)
