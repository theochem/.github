# Development setup

> :warning:
> The comments below are written for the [iodata] repository.
> You can replace the `iodata` substring with a different repository name.

> :warning:
> It is assumed that you have [Git], [Python] >=3.9 and [pre-commit] installed on your computer.

1. Create a [fork] of the repository on GitHub.
   This is essentially your online copy of the repository where you can draft your changes.

[fork]: https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo

2. Create a local clone of the original Git repository and enter the directory of the clone:

    ```bash
    git clone git@github.com:theochem/iodata.git
    cd iodata
    ```

3. Configure your fork as the second remote repository
   (in addition `origin` which was created in the previous step and refers on `theochem`):

    ```bash
    git remote add mine git@github.com:${your-github-account}/iodata.git
    ```

    where you replace `${your-github-account}` with your actual account name on GitHub.

4. Create a software environment that is suitable for development.
   (Feel free to adapt it to your personal preferences.
   For example, you can replace `python` with `python3.11` on Ubuntu 22
   to work with a newer Python version.)

    ```bash
    python -m venv venv
    source venv/bin/activate
    pip install -e .[dev]
    pre-commit install
    ```

You now have a Python virtual environment with the development version of the repository installed.
In this environment, you can
run specific unit tests you are working on,
build the documentation, or
experiment with the package as it would be installed in a production environment.

There are a few additional steps you can take to fine-tune your setup:

- The manual activation of the virtual environment with `source venv/bin/activate`
  has to be repeated every time you open a new terminal window, which is impractical.
  Some IDEs, like VSCode, will do this when you open a terminal inside the IDE.

    We do not recommend adding the `source` line to your `~/.bashrc`, `~/.bash_profile`,
    or other global recourse configuration file.
    Instead, you can use [direnv] to configure the venv locally in the `iodata/` directory.
    After installing and setting up direnv, run the following two commands in `iodata/`:

    ```bash
    echo 'source venv/bin/activate' > .envrc
    direnv allow
    ```

    Now, the virtual environment will be activated whenever you change to the `iodata/` directory.

- The line `pre-commit install` will enable pre-commit in your local clone of the repository.
  This step is important because it automatically cleans up changes
  *before* they are committed to the repository.

  If you ever make a second clone of the repository,
  you will need to run `pre-commit install` again in the new clone.

- QC-Devs repositories come with an `.editorconfig` file.
  This file contains some basic editor settings
  and is supported by most popular text editors and IDEs.
  See [editorconfig.org] for details.
  By including this file in the repository,
  we ensure a certain level of consistency across all contributions.
  Some IDEs, such as VSCode, require you to install a plugin to enable editorconfig support.

[iodata]: https://github.com/theochem/iodata
[Git]: https://git-scm.com/some
[Python]: https://www.python.org/
[pre-commit]: https://pre-commit.com/
[direnv]: https://direnv.net/
[editorconfig.org]: https://editorconfig.org/
