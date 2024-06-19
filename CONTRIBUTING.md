# QC-Devs Contributor Guide

Welcome to the **QC-Devs** community!
We are excited to have you here.
In order to make your contribution process as smooth, efficient, and inclusive as possible,
we have created these guidelines.
All contributors are expected to abide by the [QC-Devs Code of Conduct](CODE_OF_CONDUCT.md).


## Working with Git and GitHub

Contributions to QC-Devs packages are made through GitHub.
If you are not familiar with Git or GitHub,
we encourage you to explore some of the online documentation and tutorials:

- The [GitHub guides](https://guides.github.com/) describe Git and GitHub in detail.
  It provides reading material and documentation to help you become familiar with all the relevant concepts.
- The [Git book](https://git-scm.com/book/en/v2) focuses on the Git program itself
  and discusses various online providers, including GitHub,
- The gamified [Learn Git Branching](https://learngitbranching.js.org/) is a fun way,
  to learn the basics of the `git` command in an interactive and visual way.
- The [GitHub Skills](https://skills.github.com/) courses
  provide online, interactive, GitHub tutorials.


### Configure Git and GitHub

Your Git and GitHub configuration ensures that your contributions are properly attributed
and that your local `git` commands can easily communicate with GitHub.
You can find step-by-step instructions in our
[Git and GitHub Configuration](contributing/config.md) guide.


### Issue Management

Before starting to work on a contribution,
please check the issues of the project you want to contribute to.

If your contribution will solve an existing [issue],
please [assign yourself] to the issue and let the maintainers know that you are working on it.
If you plan to add a new feature, please create a new issue
and let the maintainers know that you are working on it by assigning yourself.

Also use the issue to plan your changes.
Try to solve only one problem at a time,
rather than fixing multiple problems and adding several features at once.
For example, see the [IOData issue on refactoring the continuous integration], which has been addressed in many pull requests.

[issue]: https://docs.github.com/en/issues
[assign yourself]: https://docs.github.com/en/issues/tracking-your-work-with-issues/assigning-issues-and-pull-requests-to-other-github-users
[IOData issue on refactoring the continuous integration]: https://github.com/theochem/iodata/issues/313


### Development Setup

Setting up a local development environment can be summarized as follows
(only needed once per repo):

- [Fork] the repository on GitHub.
- Clone the original repository on your local machine.
- Add your fork as a second remote to the local clone of the repository.
- Set up the software environment in your local clone.

Detailed instructions with copy-pasteable commands can be found in our
[Development Setup](contributing/development_setup.md) guide.

[Fork]: https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo


### Contribution Workflow

A contributions is made in the form of a [pull requests] (PR),
in which you propose a set of changes to the source code.
A PR should be small and focused:
Fix one issue (or even part of one) or add just one feature.
This makes the review process faster and easier for everyone.

[pull requests]: https://docs.github.com/en/pull-requests

The contribution workflow involves steps on your local and online repositories.
It can be summarized as follows:

1. Create a new branch in your local clone of the repository.
2. Make your changes and commit them locally.
3. Push your new branch with the changes to your fork on GitHub.
4. [Create a pull request] to the `main` branch of the original repository.

Detailed instructions with copy-pasteable commands can be found in our
[Contribution workflow](contributing/workflow.md) guide.

[Create a pull request]: https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request


## Code Quality

Code contributions are the most common type of contribution.
We welcome all types of code contributions, including bug fixes, new features, and documentation updates.
All code contributions should follow the guidelines below.


#### 1. Code should be well-written.

In general, we follow the [PEP 8](https://peps.python.org/pep-0008/) style guide for Python code.
Most of the style conventions are taken care of by pre-commit.
If you have it installed as described above, the basics are covered.

To improve the readability of changes on GitHub or in `git diff` output,
use [semantic line breaks](https://sembr.org/) to wrap long sentences.

We strive to write compact and elegant Python code.
The linters configured in pre-commit can only detect or fix local style issues.
Anything beyon the scope of the linters, will be addressed when reviewing a pull request.


#### 2. Code should be well-documented.

- All functions and classes (except tests) should have a docstring
  that explain what they do and how to use them.
- We encourage the use of mathematical equations in docstrings, using LaTeX notation.
- We do not encourage the use of example code in docstrings,
  as it can become outdated and difficult to maintain.
  Instead, we encourage the use of Python scripts or Jupyter Notebooks for examples and tutorials.
- Use `type hinting` to document the types of function (and method) arguments and return values.
- Your code will be read by other developers, so it should be easy to understand.
  If a piece of code seems complex, it should have comments explaining what it does.
  (When in doubt, add a comment!)
  Good comments emphasize the intent of the code, rather than literally describing it.


#### 3. Code should be tested.

- All code should be tested. We use [pytest](https://docs.pytest.org/en/stable/) for testing.
  When you add new code, you should also add tests for it.
  If you fix a bug, you should also add a test that fails without your code and passes with your code.
- We use [codecov](https://codecov.io/) in most of our packages to check the code coverage of our tests.
  Please make sure that your code is well-tested and that the coverage does not decrease.


#### 4. Code should be consistent.

Code needs to be consistent with the rest of the codebase.
This makes it easier to review and maintain. This includes:

- Variable names, function names, and class names should be consistent with the rest of the codebase.
  Most QC-Devs repositories use [atomic units](https://en.wikipedia.org/wiki/Atomic_units) internally.
  We ask that you try to preserve this (for consistency), but still document units.

- Even more, variable names should be consistent across all QC-Devs packages.
  We are in the process of creating a glossary, but for now,
  please take a look at the existing code on [GitHub](https://github.com/theochem) and try to match them.

We value your contributions and appreciate your efforts to improve QC-Devs packages.
By following these guidelines, you can ensure smoother collaboration and enhance the overall quality of the project.
