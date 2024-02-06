# QC-Devs Contributing Guidelines

Welcome to the **QC-Devs** community! We are excited to have you here. In order to make your contribution process as smooth, efficient, and inclusive as possible, we have created these guidelines. All contributors are expected to abide by the [QC-Devs Code of Conduct](CodeOfConduct.md).

## GitHub Workflow
All contributions to QC-Devs packages are made through GitHub. If you are not familiar with git or GitHub, we recommend you to take a look at the [GitHub Guides](https://guides.github.com/) or this [git book](https://git-scm.com/book/en/v2).

To ensure clarity and effective collaboration, please follow these steps:

#### Issue Management
Before starting to work on a contribution, please check the issues of the project you want to contribute to.
- If your contribution will solve an existing issue, please [assign yourself](https://docs.github.com/en/issues/tracking-your-work-with-issues/assigning-issues-and-pull-requests-to-other-github-users) to the issue and let the maintainers know that you are working on it. If you plan to add a new feature, please create a new issue and let the maintainers know that you are working on it (assign yourself to the issue).
- Contributions or [pull requests](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests) (PR) should be short and focused (shorter PRs are easier to review and check for errors). One PR should solve one issue (or even part of one) or add just one feature. This makes the review process faster and easier for everyone.

#### Contribution Workflow
Here is a brief overview of QC-Devs contributing workflow:
    1. [Fork](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo) the repository
    2. Create a new branch
    3. Make your changes
    4. Push your changes to your fork
    5. [Create a pull request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request) to the `main` branch of the original repository. The PR should have a clear title and description (of what it does and how), and should reference the issue it solves (if it solves an issue). It's much easier to review several small pull requests than one gargantuan one, so it is preferable to make small pull requests as you go along. 

#### Commit Messages
We follow the [Pansini guide](https://gist.github.com/robertpainsi/b632364184e70900af4ab688decf6f53#rules-for-a-great-git-commit-message-style) style for commit messages. This makes it easier to generate changelogs and to understand the history of the project.

## Code Contributions
Code contributions are the most common type of contribution. We welcome all types of code contributions, including bug fixes, new features, and documentation updates. All code contributions should follow the guidelines below.

#### 1. Code should be well-written.
In general, we follow the [PEP 8](https://www.python.org/dev/peps/pep-0008/) style guide for Python code (using tools like [pycodestyle](https://pycodestyle.pycqa.org/en/latest/) and [pydocstyle](https://www.pydocstyle.org/en/stable/) can help ensure the quality of your code). We also use [Black](https://black.readthedocs.io/en/stable/) to format our code. Please make sure to run Black on your code before submitting a pull request.
``` black -l 100 your_file.py ```

#### 2. Code should be well-documented.
- All functions and classes (except tests) should have a docstring that explains what they do and how to use them.
- We encourage the use of mathematical equations in docstrings, using LaTeX notation.
- We do not encourage the use of example code in docstrings, as it can become outdated and difficult to maintain. Instead, we encourage the use of Jupyter Notebooks for examples and tutorials.
- Use `type hinting` to document the types of function (and method) arguments and return values.
- Your code will be read by other developers, so it should be easy to understand. When a part of the code seems complex, it should have comments explaining what it does. (If in doubt, add a comment!)

#### 3. Code should be tested.
- All code should be tested. We use [pytest](https://docs.pytest.org/en/stable/) for testing. When you add new code, you should also add tests for it. If you fix a bug, you should also add a test that fails without your code and passes with your code.
- We use [codecov](https://codecov.io/) in most of our packages to check the code coverage of our tests. Please make sure that your code is well-tested and that the coverage does not decrease.

#### 4. Code should be consistent.
Code needs to be consistent with the rest of the codebase. This makes it easier to review and maintain. This includes:
- Variable names, function names, and class names should be consistent with the rest of the codebase. Most QC-Devs repositories use [atomic units](https://en.wikipedia.org/wiki/Atomic_units) internally. We ask that you try to preserve this (for consistency), but still document units.
- Even more, variable names should be consistent with all QC-Devs packages. We are in the process of making a glossary but at the moment, please take a look at the existing code on [GitHub](https://github.com/theochem) and try to match them.

We value your contributions and appreciate your efforts to improve QC-Devs packages. By following these guidelines, you can ensure smoother collaboration and enhance the overall quality of the project.

