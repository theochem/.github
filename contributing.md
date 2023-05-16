## Contributing Guidelines

We'd love you to contribute. Here are some practical hints to help out.

This document assumes you are familiar with `Bash` and `Python`.


## General recommendations

- Please, be careful with tools like autopep8, black or yapf. They may result in
  a massive number of changes, making pull requests harder to review. Also, when
  using them, use a maximum line length of 100. To avoid confusion, only clean
  up the code you are working on. A safer option is to use
  ``cardboardlint -F -r master``. This will only clean code where you have
  already made changes.

- Do not add module-level ``pylint: disable=...`` lines, except for the
  ``no-member`` warning in the unit test modules. When adding pylint exception,
  place them as locally as possible and make sure they are justified.

- Use `type hinting`_ to document the types of function (and method) arguments
  and return values. This is not yet consistently done throughout IOData at the
  moment, but it would be helpful to do so in future pull requests. Avoid using
  strings to postpone the evaluation of the type. (See `PEP 0563`_ for more
  details on postponed type annotation.)

- In unit testing, use ``np.testing.assert_allclose`` and
  ``np.testing.assert_equal`` for comparing floating-point and integer numpy
  arrays respectively. ``np.testing.assert_allclose`` can also be used for
  comparing floating point scalars. In all other cases (not involving floating
  point numbers), the simple ``assert a == b`` works equally well and is more
  readable.

- Most QC-Devs repositories use atomic units internally. Try to preserve this 
  for consistency.

- Make small pull requests.

- Abide by the QC-Devs Code of Conduct.


## Github work flow

Before diving into technicalities: if you intend to make major changes, beyond
fixing bugs and small functionality improvements, please open a Github issue
first, so we can discuss before coding. Please explain what you intend to
accomplish and why. That often saves a lot of time and trouble in the long run.

Use the issue to plan your changes. Try to solve only one problem at a time,
instead of fixing several issues and adding different features in a single shot.
Small changes are easier to handle, also for the reviewer in the last step
below.

Mention in the corresponding issue when you are working on it. "Claim" the issue
to avoid duplicate efforts.

1. Check your GitHub settings and your local git configuration:

   - If you don't have an SSH key pair yet, create one with the following
     terminal command:

     .. code-block:: bash

        ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

     A suitable name for this key would be ``id_rsa_github``.
     An empty pass phrase is convenient and should be fine.
     This will generate a private and a public key in ``${HOME}/.ssh``.

   - Upload your *public* SSH key to `<https://github.com/settings/keys>`_.
     This is a single long line in ``id_rsa_github.pub``, which you can
     copy-paste into the browser.

   - Configure SSH to use this key pair for authentication when pushing
     branches to Github. Add the following to your ``.ssh/config`` file:

     .. code-block::

       Host github.com
           Hostname github.com
           ForwardX11 no
           IdentityFile /home/your_user_name/.ssh/id_rsa_github

     (Make sure you have the correct path to the private key file.)

   - Configure git to use the name and e-mail address tied to your Github account:

     .. code-block:: bash

       git config --global user.name "Your Name"
       git config --global user.email "youremail@yourdomain.com"

2. Install Roberto, which is the driver for our CI setup. It can also replicate
   the continuous integration on your local machine, which makes it easier to
   prepare a passable pull request. See `<https://theochem.github.io/roberto/>`.

3. Sometimes we fork, and sometimes we branch.
   - a fork is made when you are working on an update by yourself.
   - for an update that is being done in close collaboration with several others
     on the QC-Devs team, it is preferable to make a new branch. This makes it 
     easy for others to see, and help with, your work. 
   - occassionally we have a private version of a public repository where 
     new scientific developments and experimental software development strategies
     are explored. If, based on your issue, we feel you should be working in the
     private repository, we will grant you access. Most QC-Devs software is 100%
     free and open source, with no private repository lurking in the shadows.

3. Make a fork of the project, using the Github "fork" feature.

4. Clone the original repository on your local machine and enter the directory

   .. code-block:: bash

    git clone git@github.com:theochem/iodata.git
    cd iodata

5. Add your fork as a second remote to your local repository, for which we will
   use the short name ``mine`` below, but any short name is fine:

   .. code-block:: bash

    git remote add mine git@github.com:<your-github-account>/iodata.git

6. Make a new branch, with a name that hints at the purpose of your
   modification:

   .. code-block:: bash

    git checkout -b new-feature

7. Make changes to the source. Please, make it easy for others to understand
   your code. Also, add tests that verify your code works as intended.
   Rules of thumb:

   - Write transparent code, e.g. self-explaining variable names.
   - Add comments to passages that are not easy to understand at first glance.
   - Write docstrings explaining the API.
   - Add unit tests when feasible.

8. Commit your changes with a meaningful commit message. The first line is a
   short summary, written in the imperative mood. Optionally, this can be
   followed by an empty line and a longer description.

   If you feel the summary line is too short to describe what you did, it
   may be better to split your changes into multiple commits.

9. Run Roberto and fix all problems it reports. Either one of the following
   should work

   .. code-block:: bash

    rob                 # Normal case
    python3 -m roberto  # Only if your PATH is not set correctly

   Style issues, failing tests and packaging issues should all be detected at
   this stage.

10. Push your branch to your forked repository on Github:

    .. code-block:: bash

        git push mine -u new-feature

    A link should be printed on screen, which will take the next step for you.

11. Make a pull request from your branch `new-feature` in your forked repository
    to the `master` branch in the original repository.

12. Wait for the tests on Travis-CI to complete. These should pass. Also
    coverage analysis will be shown, but this is merely indicative. Normally,
    someone should review your pull request in a few days. Ideally, the review
    results in minor corrections at worst. We'll do our best to avoid larger
    problems in step 1.


## Notes on `attrs`

QC-Devs software frequently uses the `attrs`_ library. This enables basic attribute
validation, which eliminates potentially silly bugs. (See ``theochem/iodata/attrutils.py`` 
and the usage of ``validate_shape`` in all those classes.)

The following ``attrs`` functions could be convenient when working with these
classes:

- The data can be turned into plain Python data types with the ``attr.asdict``
  function. Make sure you add the ``retain_collection_types=True`` option, to
  avoid the following issue: https://github.com/python-attrs/attrs/issues/646
  For example.

  .. code-block:: python

      from iodata import load_one
      import attr
      iodata = load_one("example.xyz")
      fields = attr.asdict(iodata, retain_collection_types=True)

  A similar ``astuple`` function works as you would expect.

- A `shallow copy`_ with a few modified attributes can be created with the
  evolve method, which is a wrapper for ``attr.evolve``:

  .. code-block:: python

      from iodata import load_one
      import attr
      iodata1 = load_one("example.xyz")
      iodata2 = attr.evolve(iodata1, title="another title")

  The usage of evolve becomes mandatory when you want to change two or more
  attributes whose shape need to be consistent. For example, the following
  would fail:

  .. code-block:: python

      from iodata import IOData
      iodata = IOData(atnums=[7, 7], atcoords=[[0, 0, 0], [2, 0, 0]])
      # The next line will fail because the size of atnums and atcoords
      # becomes inconsistent.
      iodata.atnums = [8, 8, 8]
      iodata.atcoords = [[0, 0, 0], [2, 0, 1], [4, 0, 0]]

  The following code, which has the same intent, does work:

  .. code-block:: python

      from iodata import IOData
      import attr
      iodata1 = IOData(atnums=[7, 7], atcoords=[[0, 0, 0], [2, 0, 0]])
      iodata2 = attr.evolve(
          iodata1,
          atnums=[8, 8, 8],
          atcoords=[[0, 0, 0], [2, 0, 1], [4, 0, 0]],
      )

   For brevity, lists (of lists) were used in these examples. These are always
   converted to arrays by the constructor or when assigning them to attributes.


.. _Bash: https://en.wikipedia.org/wiki/Bash_(Unix_shell)
.. _Python: https://en.wikipedia.org/wiki/Python_(programming_language)
.. _type hinting: https://docs.python.org/3/library/typing.html
.. _PEP 0563: https://www.python.org/dev/peps/pep-0563/
.. _attrs: https://www.attrs.org/en/stable/
.. _attr: https://github.com/denis-ryzhkov/attr
.. _shallow copy: https://docs.python.org/3/library/copy.html?highlight=shallow
Footer
© 2023 GitHub, Inc.
Footer navigation
Terms
Privacy
Security
Status
Docs
Contact GitHub
Pricing
API
Training
Blog
About
Create contributing.md by PaulWAyers · Pull Request #6 · theochem/QCDevs_www 
