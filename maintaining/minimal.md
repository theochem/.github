# Minimal Repository Setup

If you have not already gone through the
[Git and GitHub Configuration for Contributors](../contributing/config.md), please do so first.
This guide builds further on that configuration.
It also assumes that you have [Git] and [pre-commit] installed.

[Git]: https://git-scm.com/
[pre-commit]: https://pre-commit.com/


## Configure Your Local Git Software

We use `main` as the default branch in our repositories.
This is configured with the following command

```bash
git config --global init.defaultBranch main
```

## Create a Local Git Repository

Run the following in your terminal:

```bash
mkdir ${your-fancy-project-name}
cd ${your-fancy-project-name}
git init
```

where you replace `${your-fancy-project-name}` with the actual name of your repository.
Most GitHub projects use [kebab-case] for repository names.
(It's not clear why. My best guess is that weathered coders often suffer from [RSI]
and try to avoid the Shift key when they can.
It also looks cleaner.)

[kebab-case]: https://stackoverflow.com/a/17820138/494584
[RSI]: https://en.wikipedia.org/wiki/Repetitive_strain_injury


## Add a Few Essential Files

The following files should always be present from the start:

- `README.md` Markdown file containing:

    - A title with name of your project.
    - A brief description.
    - A statement that the documentation still needs to be written.
      You will eventually replace this by a link to the documentation.
    - References to our
      [Contributor Guide](CONTRIBUTING.md)
      and [Code of Conduct](CODE_OF_CONDUCT.md).

  For historical reasons, some projects use [ReStructuredText] instead of [Markdown].
  For new projects, we recommend using Markdown,
  as it has better support in IDEs and documentation build tools.

[ReStructuredText]: https://en.wikipedia.org/wiki/ReStructuredText
[Markdown]: https://en.wikipedia.org/wiki/Markdown

- `LICENSE.txt`:
  The open source license under which you publicly share your work.
  See [Choose an open source license](https://choosealicense.com/)
  Discuss this choice with your collaborators, supervisor, boss, etc.
  It is an important decision, and changing it later can be hard
  if others have already contributed under the terms of your original license.

- `.editor-config`:
  This file contains basic settings for source code editors and
  is widely supported.
  See [editorconfig.org](https://editorconfig.org/) for details.
  Some examples:

    - https://github.com/theochem/iodata/blob/main/.editorconfig
    - https://github.com/theochem/.github/blob/main/.editorconfig

- `.gitignore`
  This file lists all files that should never be included in the Git history.
  In general, all temporary and output files should be listed here.
  Some examples:

    - https://github.com/theochem/iodata/blob/main/.gitignore
    - https://github.com/theochem/.github/blob/main/.gitignore

- `.pre-commit-config.yaml`:
  This file configures [pre-commit], which checks and cleans contributions *before* they are committed.
  Some examples:

    - https://github.com/theochem/iodata/blob/main/.pre-commit-config.yaml
    - https://github.com/theochem/.github/blob/main/.pre-commit-config.yaml

  More can be found in the [list of supported pre-commit hooks](https://pre-commit.com/hooks.html).

  Note that some of the tools listed in `.pre-commit-config.yaml`
  rely on additional configuration settings,
  most notably in `pyproject.toml`, which we'll cover later.


## Enable pre-commit on Your Repository

Run the following command:

```bash
pre-commit install
```

This command is a bit misleading,
because the pre-commit software should already be installed on your computer
before you can run it.


## Create an Empty Repository on GitHub

At this stage, you can contact a member of QC-Devs
who has permission to create a new repository in the theochem organization.
This person will create an empty repository for you.


## Configure the Remote `origin`, Commit and Push

The following commands will upload your local work online:

```bash
git add .
git commit -a -m "Initial commit"
git remote add origin git@github.com:theochem/${your-fancy-project-name}.git
git push -u origin main
```
