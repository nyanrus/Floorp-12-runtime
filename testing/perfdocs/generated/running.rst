Running a performance test
==========================

You can run `perftest` locally or in Mozilla's CI

Running locally
---------------

Running a test is as simple as calling it using `mach perftest` in a mozilla-central source
checkout::

    $ ./mach perftest

The `mach` command will bootstrap the installation of all required tools for the
framework to run, and display a selection screen to pick a test. Once the
selection is done, the performance test will run locally.

If you know what test you want to run, you can use its path explicitly::

    $ ./mach perftest perftest_script.js

`mach perftest` comes with numerous options, and the test script should provide
decent defaults, so you don't need to adjust them. If you need to tweak some
options, you can use `./mach perftest --help` to learn about them.


Running in the CI
-----------------

.. warning::

    If you are looking for how to run performance tests in CI and ended up here, you might want to check out :ref:`Mach Try Perf`.

.. warning::

   If you plan to run tests often in the CI for Android, you should contact the Android
   infra team to make sure there's availability in our pool of devices.

You can run in the CI directly from the `mach perftest` command by adding the `--push-to-try` option
to your locally working perftest call.

This call will run the fuzzy selector and then send the job into our CI::

    $ ./mach perftest --push-to-try

We have phones on bitbar that can run your android tests. Tests are fairly fast
to run in the CI because they use sparse profiles. Depending on the
availability of workers, once the task starts, it takes around 15 min to start
the test.


