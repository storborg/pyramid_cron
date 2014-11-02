pyramid_cron - Simple scheduled tasks for Pyramid
=================================================

Scott Torborg - `Cart Logic <http://www.cartlogic.com>`_

Provides the ability to register simple tasks (callback functions) for
scheduled execution with a cron-like syntax.

Why it's better than a typical task queue like Celery, Resque, etc:

* No user permissions to worry about: everything is run inside a web request,
  so the task has all the same permissions as your web app.
* Very simple setup, no additional daemons required.
* The API follows Pyramid idioms.

Why it's worse:

* It's not well suited to long-running tasks: everything is run inside a web
  request.
* It does not distribute jobs across workers.
* It does not allow for prioritization of jobs, or have any support for
  non-synchronous tasks.

Documentation is `hosted at Read the Docs <http://pyramid-cron.readthedocs.org/en/latest/>`_.


Installation
============

Install with pip::

    $ pip install pyramid_cron

For each web app which uses pyramid_cron, you'll need to fire the cron handler from a whitelisted IP once per minute. An easy way to do this is by adding a cron job on the app server:

    * * * * *   curl -o /dev/null http://localhost/cron


License
=======

pyramid_cron is licensed under an MIT license. Please see the LICENSE file
for more information.


Code Standards
==============

pyramid_cron has a comprehensive test suite with 100% line and branch coverage,
as reported by the excellent ``coverage`` module. To run the tests, simply run
in the top level of the repo::

    $ nosetests

There are no `PEP8 <http://www.python.org/dev/peps/pep-0008/>`_ or
`Pyflakes <http://pypi.python.org/pypi/pyflakes>`_ warnings in the codebase. To
verify that::

    $ pip install pep8 pyflakes
    $ pep8 .
    $ pyflakes .

Any pull requests must maintain the sanctity of these three pillars.
