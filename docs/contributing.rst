Contributing
============

Process
-------

As an open source project, ``cryptography`` welcomes contributions of all
forms. These can include:

* Bug reports and feature requests
* Pull requests for both code and documentation
* Patch reviews

You can file bugs and submit pull requests on `GitHub`_. To discuss larger
changes you can start a conversation on `our mailing list`_.

Because cryptography is so complex, and the implications of getting it wrong so
devastating, ``cryptography`` has a strict code review policy:

* Patches must *never* be pushed directly to ``master``, all changes (even the
  most trivial typo fixes!) must be submitted as a pull request.
* A committer may *never* merge their own pull request, a second party must
  merge their changes. If multiple people work on a pull request, the merger
  may not be any of them.
* A patch which breaks tests, or introduces regressions by changing or removing
  existing tests should not be merged. Tests must always be passing on
  ``master``.
* If somehow the tests get into a failing state on ``master`` (such as by a
  backwards incompatible release of a dependency) no pull requests may be
  merged until this is rectified.

The purpose of these policies is to minimize the chances we merge a change
which jeopardizes our users' security.

We do not yet have a formal security contact. To report security issues in
``cryptography`` you should email ``alex.gaynor@gmail.com``, messages may be
encrypted with PGP to key fingerprint
``E27D 4AA0 1651 72CB C5D2  AF2B 125F 5C67 DFE9 4084`` (this public key is
available from most commonly-used keyservers).

Code
----

When in doubt, refer to `PEP 8`_ for Python code.

Every code file must start with the boilerplate notice of the Apache License.
Additionally, every Python code file must contain

.. code-block:: python

    from __future__ import absolute_import, division, print_function

Documentation
-------------

All features should be documented with prose.

Docstrings should be written like this:

.. code-block:: python

    def some_function(some_arg):
        """
        Does some things.

        :param some_arg: Some argument.
        """

So, specifically:

- Always use three double quotes.
- Put the three double quotes on their own line.
- No blank line at the end.
- Use Sphinx parameter/attribute documentation `syntax`_.

Development Environment
-----------------------

Working on ``cryptography`` requires the installation of a small number of
development dependencies. These are listed in ``dev-requirements.txt`` and they
can be installed in a `virtualenv`_ using `pip`_. Once you've installed the
dependencies, install ``cryptography`` in ``editable`` mode. For example:

.. code-block:: console

   $ # Create a virtualenv and activate it
   $ pip install --requirement dev-requirements.txt
   $ pip install --editable .

You are now ready to run the tests and build the documentation.

Running Tests
-------------

``cryptography`` unit tests are found in the ``tests/`` directory and are
designed to be run using `pytest`_. `pytest`_ will discover the tests
automatically, so all you have to do is:

.. code-block:: console

   $ py.test
   ...
   4294 passed in 15.24 seconds

This runs the tests with the default Python interpreter.

You can also verify that the tests pass on other supported Python interpreters.
For this we use `tox`_, which will automatically create a `virtualenv`_ for
each supported Python version and run the tests. For example:

.. code-block:: console

   $ tox
   ...
   ERROR:   py26: InterpreterNotFound: python2.6
    py27: commands succeeded
   ERROR:   pypy: InterpreterNotFound: pypy
   ERROR:   py32: InterpreterNotFound: python3.2
    py33: commands succeeded
    docs: commands succeeded
    pep8: commands succeeded

You may not have all the required Python versions installed, in which case you
will see one or more ``InterpreterNotFound`` errors.

Building Documentation
----------------------

``cryptography`` documentation is stored in the ``docs/`` directory. It is
written in `reStructured Text`_ and rendered using `Sphinx`_.

Use `tox`_ to build the documentation. For example:

.. code-block:: console

   $ tox -e docs
   ...
   docs: commands succeeded
   congratulations :)

The HTML documentation index can now be found at ``docs/_build/html/index.html``


.. _`GitHub`: https://github.com/pyca/cryptography
.. _`our mailing list`: https://mail.python.org/mailman/listinfo/cryptography-dev
.. _`PEP 8`: http://www.peps.io/8/
.. _`syntax`: http://sphinx-doc.org/domains.html#info-field-lists
.. _`pytest`: https://pypi.python.org/pypi/pytest
.. _`tox`: https://pypi.python.org/pypi/tox
.. _`virtualenv`: https://pypi.python.org/pypi/virtualenv
.. _`pip`: https://pypi.python.org/pypi/pip
.. _`sphinx`: https://pypi.python.org/pypi/sphinx
.. _`reStructured Text`: http://docutils.sourceforge.net/rst.html
