CHANGES
=======

4.1.1 (unreleased)
------------------

- Nothing changed yet.


4.1.0 (2020-01-06)
------------------

- **New command:** ``requests_per_hour``.
  Just like the ``requests_per_minute`` but with hour granularity.
  Idea and first implementation done by ``valleedelisle``.
  [gforcada]

- Fix parsing truncated requests.
  Idea and first implementation by ``vixns``.
  [gforcada]

4.0.0 (2020-01-06)
------------------

**BREAKING CHANGES:**

- Complete rewrite to use almost no memory usage even on huge files.
  [gforcada]

- Add parallelization to make parsing faster by parsing multiple lines in parallel.
  [gforcada]

- Rename command ``counter_slow_requests`` to ``slow_requests_counter``,
  so it is aligned with all other ``_counter`` commands.
  [gforcada]

- Changed the ``counter_invalid`` command to a new command line switch ``--invalid``.
  [gforcada]

**Regular changes:**

- Drop Python 2 support, and test on Python 3.8.
  [gforcada]

- Remove the pickling support.
  [gforcada]

- Add `--json` output command line option.
  [valleedelisle]

3.0.0 (2019-06-10)
------------------

- Fix spelling.
  [EdwardBetts]

- Make ip_counter use client_ip per default.
  [vixns]

- Overhaul testing environment. Test on python 3.7 as well. Use black to format.
  [gforcada]

2.1 (2017-07-06)
----------------
- Enforce QA checks (flake8) on code.
  All code has been updated to follow it.
  [gforcada]

- Support Python 3.6.
  [gforcada]

- Support different syslog timestamps (at least NixOS).
  [gforcada]

2.0.2 (2016-11-17)
------------------

- Improve performance for ``cmd_print``.
  [kevinjqiu]

2.0.1 (2016-10-29)
------------------

- Allow hostnames to have a dot in it.
  [gforcada]

2.0 (2016-07-06)
----------------
- Handle unparseable HTTP requests.
  [gforcada]

- Only test on python 2.7 and 3.5
  [gforcada]

2.0b0 (2016-04-18)
------------------
- Check the divisor before doing a division to not get ``ZeroDivisionError`` exceptions.
  [gforcada]

2.0a0 (2016-03-29)
------------------
- Major refactoring:

  # Rename modules and classes:

    - haproxy_logline -> line
    - haproxy_logfile -> logfile
    - HaproxyLogLine -> Line
    - HaproxyLogFile -> Log

  # Parse the log file on Log() creation (i.e. in its __init__)

  [gforcada]

1.3 (2016-03-29)
----------------

- New filter: ``filter_wait_on_queues``.
  Get all requests that waited at maximum X amount of milliseconds on HAProxy queues.
  [gforcada]

- Code/docs cleanups and add code analysis.
  [gforcada]

- Avoid using eval.
  [gforcada]

1.2.1 (2016-02-23)
------------------

- Support -1 as a status_code
  [Christopher Baines]

1.2 (2015-12-07)
----------------

- Allow a hostname on the syslog part (not only IPs)
  [danny crasto]

1.1 (2015-04-19)
----------------

- Make syslog optional.
  Fixes issue https://github.com/gforcada/haproxy_log_analysis/issues/10.
  [gforcada]

1.0 (2015-03-24)
----------------

- Fix issue #9.
  log line on the syslog part was too strict,
  it was expecting the hostname to be a string and was
  failing if it was an IP.
  [gforcada]

0.0.3.post2 (2015-01-05)
------------------------

- Finally really fixed issue #7.
  ``namespace_packages`` was not meant to be on setup.py at all.
  Silly copy&paste mistake.
  [gforcada]

0.0.3.post (2015-01-04)
-----------------------

- Fix release on PyPI.
  Solves GitHub issue #7.
  https://github.com/gforcada/haproxy_log_analysis/issues/7
  [gforcada]

0.0.3 (2014-07-09)
------------------

- Fix release on PyPI (again).
  [gforcada]

0.0.2 (2014-07-09)
------------------

- Fix release on PyPI.
  [gforcada]

0.0.1 (2014-07-09)
------------------

- Pickle :class::`.HaproxyLogFile` data for faster performance.
  [gforcada]

- Add a way to negate the filters, so that instead of being able to filter by
  IP, it can output all but that IP information.
  [gforcada]

- Add lots of filters: ip, path, ssl, backend, frontend, server, status_code
  and so on. See ``--list-filters`` for a complete list of them.
  [gforcada]

- Add :method::`.HaproxyLogFile.parse_data` method to get data from data stream.
  It allows you use it as a library.
  [bogdangi]

- Add ``--list-filters`` argument on the command line interface.
  [gforcada]

- Add ``--filter`` argument on the command line interface, inspired by
  Bogdan's early design.
  [bogdangi] [gforcada]

- Create a new module :module::`haproxy.filters` that holds all available filters.
  [gforcada]

- Improve :method::`.HaproxyLogFile.cmd_queue_peaks` output to not only show
  peaks but also when requests started to queue and when they finsihed and
  the amount of requests that had been queued.
  [gforcada]

- Show help when no argument is given.
  [gforcada]

- Polish documentation and docstrings here and there.
  [gforcada]

- Add a ``--list-commands`` argument on the command line interface.
  [gforcada]

- Generate an API doc for ``HaproxyLogLine`` and ``HaproxyLogFile``.
  [bogdangi]

- Create a ``console_script`` `haproxy_log_analysis` for ease of use.
  [bogdangi]

- Add Sphinx documentation system, still empty.
  [gforcada]

- Keep valid log lines sorted so that the exact order of connections is kept.
  [gforcada]

- Add quite a few commands, see `README.rst`_ for a complete list of them.
  [gforcada]

- Run commands passed as arguments (with -c flag).
  [gforcada]

- Add a requirements.txt file to keep track of dependencies and pin them.
  [gforcada]

- Add travis_ and coveralls_ support. See its badges on `README.rst`_.
  [gforcada]

- Add argument parsing and custom validation logic for all arguments.
  [gforcada]

- Add regular expressions for haproxy log lines (HTTP format) and to
  parse HTTP requests path.
  Added tests to ensure they work as expected.
  [gforcada]

- Create distribution.
  [gforcada]

.. _travis: https://travis-ci.org/
.. _coveralls: https://coveralls.io/
.. _README.rst: http://github.com/gforcada/haproxy_log_analysis
