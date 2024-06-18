# Contribution Workflow

The steps below assume that you have
[set up your local development environment](development_setup.md)
and [configured Git and GitHub](config.md).
It also assumes that you have
[discussed the planned changes in a GitHub issue](../CONTRIBUTING.md#issue-management).
Here, we will only go over the technicalities of creating a pull request.

1. Unless you just created a fork, you need to update the local main branch
   by *pulling* the latest commits from the original repository.
   Assuming you have no uncommitted changes, this can be done with the following commands:

    ```bash
    git checkout main
    git pull
    ```


2. Create a new branch, with a name that indicates the purpose of your change:

    ```bash
    git checkout -b new-feature
    ```

    (Take something more descriptive than `new-feature`.)

3. Make changes to the source code.
   To make these easier to process and to maintain the code quality,
   general recommendations can be found in the
   [Code Quality section of the main Contributing Guide](../CONTRIBUTING.md#code-quality).


4. Verify that all the tests pass and that the documentation builds without warnings or errors.
   The exact commands for these tests will be slightly different in each repository.
   See the `CONTRIBUTING.md` file in the forked repository for more details.

5. Commit your changes to your `new-feature` branch.
   This step is the most tecnically challenging.
   Providing a few copy-pasteable commands here would be misleading,
   because you often need to adapt them to your specific situation.

   Roughly speaking, you run the following commands:

   - `git status` and `git diff` to assess the status of your local files.
   - `git add` to select the files with changes that you want to include in the commit.
   - `git commit` to actually create the commit.

   If you want to commit all changes, run `git commit -a`.
   (You will still need to `git add` new files.)

   You will notice that `pre-commit` checks for and possibly fixes minor problems.
   If it finds something (even if it is automatically fixed), it will abort the commit.
   This gives you a chance to fix those problems or check the automatic fixes first.
   When you are happy with all the cleanup, run `git add` and `git commit` again.

   When prompted, write a meaningful commit message.
   The first line is a short summary, written in the imperative mood.
   Optionally, this can be followed by a blank line and a longer description.

   Some repositories follow the [Pansini style] for commit messages,
   in order to derive changelogs and to make the history of the project easier to understand.

[Pansini style]: https://gist.github.com/robertpainsi/b632364184e70900af4ab688decf6f53#rules-for-a-great-git-commit-message-style


6. Push your branch to your forked repository on GitHub:

    ```bash
    git push mine -u new-feature
    ```

    A link should appear in the terminal that will take you to the next step.


7. Make a pull request (PR) from your `new-feature` branch in your forked repository
   to the `main` branch in the original repository.

   The PR should have a clear title and description (of what it does and how).
   If it fixes a specific issue,
   it should reference that issue in the description (not title) with a line like `Fixes #123`,
   where 123 is the issue number.

   It's much easier to review several small pull requests than one gargantuan one,
   so it is preferable to make small pull requests as you go along.


8. Wait for the GitHub Actions to complete.
   These should pass.
   If not, you are encouraged to fix the reported problems by committing and pushing more changes.
   Typically, someone should review your pull request within a few days or weeks.
