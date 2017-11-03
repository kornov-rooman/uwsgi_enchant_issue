Enchant uWSGI Issue
===================

## Used packages
 - Python==3.6.3
 - pyenv
 - Django==1.11.7
 - django-uwsgi==0.2.1
 - pyenchant==1.6.11
 - pytz==2017.3
 - uWSGI==2.0.15
 - Ubuntu 16.04LTS

What's going on:
(You can reproduce this using uwsgi command itself without django-uwsgi, but it's omitted)
```
$ UWSGI_CHEAPER=1 ./manage.py runuwsgi
[uwsgi-static] added mapping for /static/ => None
*** Starting uWSGI 2.0.15 (64bit) on [Fri Nov  3 15:18:44 2017] ***
compiled with version: 5.4.0 20160609 on 03 November 2017 15:56:09
os: Linux-4.4.0-98-generic #121-Ubuntu SMP Tue Oct 10 14:24:03 UTC 2017
nodename: user-desktop
machine: x86_64
clock source: unix
pcre jit disabled
detected number of CPU cores: 6
current working directory: /home/user/PycharmProjects/encha/enchatest
detected binary path: /home/user/.pyenv/versions/3.6.3/envs/encha/bin/uwsgi
your processes number limit is 63732
your memory page size is 4096 bytes
detected max file descriptor number: 65536
building mime-types dictionary from file /etc/mime.types...552 entry found
lock engine: pthread robust mutexes
thunder lock: disabled (you can enable it with --thunder-lock)
*** Cache "enchatest" initialized: 82MB (key: 216 bytes, keys: 4320000 bytes, data: 81920000 bytes, bitmap: 0 bytes) preallocated ***
uwsgi socket 0 bound to TCP address :8000 fd 4
Python version: 3.6.2 (default, Aug 21 2017, 10:22:16)  [GCC 5.4.0 20160609]
PEP 405 virtualenv detected: /home/user/.pyenv/versions/encha
Set PythonHome to /home/user/.pyenv/versions/encha
Python main interpreter initialized at 0x1747130
python threads support enabled
your server socket listen backlog is limited to 100 connections
your mercy for graceful operations on workers is 60 seconds
setting request body buffering size to 1048576 bytes
mapped 15376179 bytes (15015 KB) for 12 cores
*** Operational MODE: preforking ***
added /home/user/PycharmProjects/encha/enchatest/ to pythonpath.
spawned uWSGI master process (pid: 8677)
spawned uWSGI worker 1 (pid: 8710, cores: 1)
cache sweeper thread enabled
Python auto-reloader enabled
Traceback (most recent call last):
  File "/home/user/PycharmProjects/encha/enchatest/enchatest/wsgi.py", line 16, in <module>
    application = get_wsgi_application()
  File "/home/user/.pyenv/versions/encha/lib/python3.6/site-packages/django/core/wsgi.py", line 13, in get_wsgi_application
    django.setup(set_prefix=False)
  File "/home/user/.pyenv/versions/encha/lib/python3.6/site-packages/django/__init__.py", line 27, in setup
    apps.populate(settings.INSTALLED_APPS)
  File "/home/user/.pyenv/versions/encha/lib/python3.6/site-packages/django/apps/registry.py", line 108, in populate
    app_config.import_models()
  File "/home/user/.pyenv/versions/encha/lib/python3.6/site-packages/django/apps/config.py", line 202, in import_models
    self.models_module = import_module(models_module_name)
  File "/home/user/.pyenv/versions/3.6.3/lib/python3.6/importlib/__init__.py", line 126, in import_module
    return _bootstrap._gcd_import(name[level:], package, level)
  File "/home/user/PycharmProjects/encha/enchatest/why/models.py", line 2, in <module>
    import enchant
  File "/home/user/.pyenv/versions/encha/lib/python3.6/site-packages/enchant/__init__.py", line 92, in <module>
    from enchant import _enchant as _e
  File "/home/user/.pyenv/versions/encha/lib/python3.6/site-packages/enchant/_enchant.py", line 52, in <module>
    from ctypes import *
  File "/home/user/.pyenv/versions/3.6.3/lib/python3.6/ctypes/__init__.py", line 7, in <module>
    from _ctypes import Union, Structure, Array
ImportError: /home/user/.pyenv/versions/3.6.3/lib/python3.6/lib-dynload/_ctypes.cpython-36m-x86_64-linux-gnu.so: undefined symbol: _PyUnicode_AsWideCharString
unable to load app 0 (mountpoint='') (callable not found or import error)
*** no app loaded. going in full dynamic mode ***
^CSIGINT/SIGQUIT received...killing workers...
worker 1 buried after 1 seconds
goodbye to uWSGI.
```
