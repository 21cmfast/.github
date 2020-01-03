============
Contributing
============

Contributions are welcome, and they are greatly appreciated! Every
little bit helps, and credit will always be given.

Bug reports/Feature Requests/Feedback/Questions
===============================================
It is incredibly helpful to us when users report bugs, unexpected behaviour, or request
features. To do any of these things, go to the "Issues" tab in the Github project, and add a new issue.
It will prompt you to do one of the following:

* Report a bug
* Request a Feature
* Ask a Question

When doing any of these, please try to be as succinct, but detailed, as possible, and use
a "Minimum Working Example" whenever applicable. If your issue doesn't correspond to any
of these, make a new blank issue.

Documentation improvements
==========================

``21cmFAST`` projects could always use more documentation, whether as part of the
official docs, in docstrings, or even on the web in blog posts,
articles, and such. If you do the latter, take the time to let us know about it!

Development
===========

This is an abbreviated guide to getting started with development of ``21cmFAST`` projects
(whether `21cmFAST`` itself, ``21CMMC`` or any number of plugins and/or extensions),
focusing on the discrete high-level steps to take. Each specific code should 
have a set of more detailed *developer documentation* which you should read in addition 
to these notes. That will get you up to speed on how the actual internals work.

There are two avenues for you to develop ``21cmFAST`` codes. If you plan on making significant
changes, and working with the ``21cmFAST`` project for a long period of time, please consider
becoming a member of the 21cmFAST GitHub organisation (by emailing any of the owners
or admins). You may develop as a member or as a non-member.

The difference between members and non-members only applies to the first step
of the development process. These steps should apply to *all* codes in the 
``21cmFAST`` organization. If for some reason these steps *do not work* for a
given code, please make an issue for it!


As a *member*:

1. Clone the repo::

    git clone git@github.com:21cmFAST/repo-name.git

As a *non-member*:

1. First fork `21cmFAST <https://github.com/21cmFAST/repo-name>`_
   (look for the "Fork" button), then clone the fork locally::

    git clone git@github.com:your_name_here/repo-name.git

The following steps are the same for both *members* and *non-members*:

2. Install a fresh new isolated environment. This can be either a basic ``virtualenv``
   or a ``conda`` env (suggested). So either::

       virtualenv ~/21cmfast
       source ~/21cmfast/bin/activate

   or::

       conda create -n 21cmfast python=3
       conda activate 21cmfast

3. Install the *development* requirements for the project. If using the basic `virtualenv`::

    pip install -r requirements_dev.txt

   or if using `conda` (suggested)::

    conda env update -f environment.yml

4. Install pre-commit hooks::

    pre-commit install

3. Create a branch for local development::

    git checkout -b name-of-your-bugfix-or-feature

   Now you can make your changes locally. **Note: as a member, you _must_ do this step. If you
   make changes on master, you will _not_ be able to push them**.

3. When you're done making changes, run all the checks, doc builder and spell checker
   with `tox <http://tox.readthedocs.io/en/latest/install.html>`_ one command::

    tox

4. Commit your changes and push your branch to GitHub::

    git add .
    git commit -m "Your detailed description of your changes."
    git push origin name-of-your-bugfix-or-feature

   Note that if the commit step fails due to a pre-commit hook, *most likely* the act
   of running the hook itself has already fixed the error. Try doing the `add` and
   `commit` again (up, up, enter). If it's still complaining, manually fix the errors
   and do the same again.

5. Submit a pull request through the GitHub website.

Pull Request Guidelines
-----------------------

If you need some code review or feedback while you're developing the code just make the
pull request. You can mark the PR as a draft until you are happy for it to be merged.

Tips
----

To run a subset of tests::

    tox -e envname -- py.test -k test_myfeature

To run all the test environments in *parallel* (you need to ``pip install detox``)::

    detox
