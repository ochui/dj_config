dj_config (Python Library)
==============================
.. image:: https://img.shields.io/pypi/v/dj-config.svg
    :target: https://pypi.python.org/pypi/dj-config
    :alt: Latest Version

This is a fork of the Django library for Heroku applications that ensures a seamless deployment and development experience.

This library provides:

-  Settings configuration (Static files / WhiteNoise).
-  Logging configuration.

--------------

Installation
////////////////
using pip::

    $ pip install dj-config

using pipenv::

    $ pipenv install dj-config

if installation fails, due to missing build dependencies required psycopg2. You can install the necessary build tools and Python development libraries::

For Ubuntu/Debian::
    $ sudo apt-get python3-dev build-essential libpq-dev



Django 4.0 is targeted, but older versions of Django should be compatible.

Usage of dj_config
///////////////////

In ``settings.py``, at the very bottom::

    …
    # Configure Django App for Heroku.
    import dj_config
    from dotenv import load_dotenv
    load_dotenv()  # take environment variables
    dj_config.settings(locals())

This will automatically configure ``DATABASE_URL``, ``ALLOWED_HOSTS``, WhiteNoise (for static assets), Logging, and Heroku CI for your application.

**Bonus points!** If you set the ``SECRET_KEY`` environment variable, it will automatically be used in your Django settings, too!

Disabling Functionality
///////////////////////

``settings()`` also accepts keyword arguments that can be passed ``False`` as a value, which will disable automatic configuration for their specific areas of responsibility:

- ``databases``
- ``staticfiles``
- ``allowed_hosts``
- ``logging``
- ``secret_key``
