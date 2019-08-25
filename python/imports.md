
[Source](http://python-future.org/imports.html "Permalink to Imports — Python-Future documentation")

# Imports — Python-Future documentation

## __future__ imports

To write a Python 2/3 compatible codebase, the first step is to add this line to the top of each module:
    
    
    from __future__ import absolute_import, division, print_function
    

For guidelines about whether to import `unicode_literals` too, see below ([Should I import unicode_literals?][1]).

For more information about the `__future__` imports, which are a standard feature of Python, see the following docs:

These are all available in Python 2.6 and up, and enabled by default in Python 3.x.

## Imports of builtins

### Implicit imports

If you don't mind namespace pollution, the easiest way to provide Py2/3 compatibility for new code using `future` is to include the following imports at the top of every module:

On Python 3, this has no effect. (It shadows builtins with globals of the same names.)

On Python 2, this import line shadows 18 builtins (listed below) to provide their Python 3 semantics.

### Explicit imports

Explicit forms of the imports are often preferred and are necessary for using certain automated code-analysis tools.

The complete set of imports of builtins from `future` is:
    
    
    from builtins import (ascii, bytes, chr, dict, filter, hex, input,
                          int, map, next, oct, open, pow, range, round,
                          str, super, zip)
    

These are also available under the `future.builtins` namespace for backward compatibility.

Importing only some of the builtins is cleaner but increases the risk of introducing Py2/3 portability bugs as your code evolves over time. For example, be aware of forgetting to import `input`, which could expose a security vulnerability on Python 2 if Python 3's semantics are expected.

The internal API is currently as follows:
    
    
    from future.types import bytes, dict, int, range, str
    from future.builtins.misc import (ascii, chr, hex, input, next,
                                      oct, open, pow, round, super)
    from future.builtins.iterators import filter, map, zip
    

Please note that this internal API is evolving and may not be stable between different versions of `future`. To understand the details of the backported builtins on Python 2, see the docs for these modules.

For more information on what the backported types provide, see [What else you need to know][2].

#### Obsolete Python 2 builtins

Twelve Python 2 builtins have been removed from Python 3. To aid with porting code to Python 3 module by module, you can use the following import to cause a `NameError` exception to be raised on Python 2 when any of the obsolete builtins is used, just as would occur on Python 3:
    
    
    from future.builtins.disabled import *
    

This is equivalent to:
    
    
    from future.builtins.disabled import (apply, cmp, coerce, execfile,
                                 file, long, raw_input, reduce, reload,
                                 unicode, xrange, StandardError)
    

Running `futurize` over code that uses these Python 2 builtins does not import the disabled versions; instead, it replaces them with their equivalent Python 3 forms and then adds `future` imports to resurrect Python 2 support, as described in [Stage 2: Py3-style code with wrappers for Py2][3].

## Standard library imports

`future` supports the standard library reorganization (PEP 3108) through several mechanisms.

### Direct imports

As of version 0.14, the `future` package comes with top-level packages for Python 2.x that provide access to the reorganized standard library modules under their Python 3.x names.

Direct imports are the preferred mechanism for accesing the renamed standard library modules in Python 2/3 compatible code. For example, the following clean Python 3 code runs unchanged on Python 2 after installing `future`:
    
    
    >>> # Alias for future.builtins on Py2:
    >>> from builtins import str, open, range, dict
    
    >>> # Top-level packages with Py3 names provided on Py2:
    >>> import queue
    >>> import tkinter.dialog
    >>> etc.
    

Notice that this code actually runs on Python 3 without the presence of the `future` package.

Of the 44 modules that were refactored with PEP 3108 (standard library reorganization), 29 are supported with direct imports in the above manner. The complete list is here:
    
    
    ### Renamed modules:
    
    import builtins
    
    import copyreg
    
    import html
    import html.entities
    import html.parser
    
    import http.client
    import http.cookies
    import http.cookiejar
    import http.server
    
    import queue
    
    import reprlib
    
    import socketserver
    
    from tkinter import colorchooser
    from tkinter import commondialog
    from tkinter import constants
    from tkinter import dialog
    from tkinter import dnd
    from tkinter import filedialog
    from tkinter import font
    from tkinter import messagebox
    from tkinter import scrolledtext
    from tkinter import simpledialog
    from tkinter import tix
    from tkinter import ttk
    
    import winreg                    # Windows only
    
    import xmlrpc.client
    import xmlrpc.server
    
    import _dummy_thread
    import _markupbase
    import _thread
    

Note that, as of v0.16.0, `python-future` no longer includes an alias for the `configparser` module because a full backport exists (see ).

### Aliased imports

The following 14 modules were refactored or extended from Python 2.6/2.7 to 3.x but were neither renamed in Py3.x nor were the new APIs backported to Py2.x. This precludes compatibility interfaces that work out-of-the-box. Instead, the `future` package makes the Python 3.x APIs available on Python 2.x as follows:
    
    
    from future.standard_library import install_aliases
    install_aliases()
    
    from collections import UserDict, UserList, UserString
    
    import urllib.parse
    import urllib.request
    import urllib.response
    import urllib.robotparser
    import urllib.error
    
    import dbm
    import dbm.dumb
    import dbm.gnu                # requires Python dbm support
    import dbm.ndbm               # requires Python dbm support
    
    from itertools import filterfalse, zip_longest
    
    from subprocess import getoutput, getstatusoutput
    
    from sys import intern
    
    import test.support
    

The newly exposed `urllib` submodules are backports of those from Py3.x. This means, for example, that `urllib.parse.unquote()` now exists and takes an optional `encoding` argument on Py2.x as it does on Py3.x.

**Limitation:** Note that the `http`-based backports do not currently support HTTPS (as of 2015-09-11) because the SSL support changed considerably in Python 3.x. If you need HTTPS support, please use this idiom for now:
    
    
    from future.moves.urllib.request import urlopen
    

Backports also exist of the following features from Python 3.4:

* `math.ceil` returns an int on Py3
* `collections.OrderedDict` (for Python 2.6)
* `collections.Counter` (for Python 2.6)
* `collections.ChainMap` (for all versions prior to Python 3.3)
* `itertools.count` (for Python 2.6, with step parameter)
* `subprocess.check_output` (for Python 2.6)
* `reprlib.recursive_repr` (for Python 2.6 and 2.7)

These can then be imported on Python 2.6+ as follows:
    
    
    from future.standard_library import install_aliases
    install_aliases()
    
    from math import ceil      # now returns an int
    from collections import Counter, OrderedDict, ChainMap
    from itertools import count
    from subprocess import check_output
    from reprlib import recursive_repr
    

## External standard-library backports

Backports of the following modules from the Python 3.x standard library are available independently of the python-future project:
    
    
    import enum                       # pip install enum34
    import singledispatch             # pip install singledispatch
    import pathlib                    # pip install pathlib
    

A few modules from Python 3.4 and 3.3 are also available in the `backports` package namespace after `pip install backports.lzma` etc.:
    
    
    from backports import lzma
    from backports import functools_lru_cache as lru_cache
    

The following Python 2.6 backports of standard library packages from Python 2.7+ are also available:
    
    
    import argparse                   # pip install argparse
    import importlib                  # pip install importlib
    import unittest2 as unittest      # pip install unittest2
    

These are included in Python 2.7 and Python 3.x.

## Included full backports

Alpha-quality full backports of the following modules from Python 3.3's standard library to Python 2.x are also available in `future.backports`:
    
    
    http.client
    http.server
    html.entities
    html.parser
    urllib
    xmlrpc.client
    xmlrpc.server
    

The goal for these modules, unlike the modules in the `future.moves` package or top-level namespace, is to backport new functionality introduced in Python 3.3.

If you need the full backport of one of these packages, please open an issue [here][4].

## Using Python 2-only dependencies on Python 3

The `past` module provides an experimental `translation` package to help with importing and using old Python 2 modules in a Python 3 environment.

This is implemented using PEP 414 import hooks together with fixers from `lib2to3` and `libfuturize` (included with `python-future`) that attempt to automatically translate Python 2 code to Python 3 code with equivalent semantics upon import.

_Note_ This feature is still in alpha and needs further development to support a full range of real-world Python 2 modules. Also be aware that the API for this package might change considerably in later versions.

Here is how to use it:
    
    
    $ pip3 install plotrique==0.2.5-7 --no-compile   # to ignore SyntaxErrors
    $ python3
    

Then pass in a whitelist of module name prefixes to the `past.autotranslate()` function. Example:
    
    
    >>> from past import autotranslate
    >>> autotranslate(['plotrique'])
    >>> import plotrique
    

Here is another example:
    
    
    >>> from past.translation import install_hooks, remove_hooks
    >>> install_hooks(['mypy2module'])
    >>> import mypy2module
    >>> remove_hooks()
    

This will translate, import and run Python 2 code such as the following:
    
    
    ### File: mypy2module.py
    
    # Print statements are translated transparently to functions:
    print 'Hello from a print statement'
    
    # xrange() is translated to Py3's range():
    total = 0
    for i in xrange(10):
        total += i
    print 'Total is: %d' % total
    
    # Dictionary methods like .keys() and .items() are supported and
    # return lists as on Python 2:
    d = {'a': 1, 'b': 2}
    assert d.keys() == ['a', 'b']
    assert isinstance(d.items(), list)
    
    # Functions like range, reduce, map, filter also return lists:
    assert isinstance(range(10), list)
    
    # The exec statement is supported:
    exec 'total += 1'
    print 'Total is now: %d' % total
    
    # Long integers are supported:
    k = 1234983424324L
    print 'k + 1 = %d' % k
    
    # Most renamed standard library modules are supported:
    import ConfigParser
    import HTMLParser
    import urllib
    

The attributes of the module are then accessible normally from Python 3. For example:
    
    
    # This Python 3 code works
    >>> type(mypy2module.d)
    builtins.dict
    

This is a standard Python 3 data type, so, when called from Python 3 code, `keys()` returns a view, not a list:
    
    
    >>> type(mypy2module.d.keys())
    builtins.dict_keys
    

* It currently requires a newline at the end of the module or it throws a `ParseError`.
* This only works with pure-Python modules. C extension modules and Cython code are not supported.
* The biggest hurdle to automatic translation is likely to be ambiguity about byte-strings and text (unicode strings) in the Python 2 code. If the `past.autotranslate` feature fails because of this, you could try running `futurize` over the code and adding a `b''` or `u''` prefix to the relevant string literals. To convert between byte-strings and text (unicode strings), add an `.encode` or `.decode` method call. If this succeeds, please push your patches upstream to the package maintainers.
* Otherwise, the source translation feature offered by the `past.translation` package has similar limitations to the `futurize` script (see [Known limitations][5]). Help developing and testing this feature further would be particularly welcome.

Please report any bugs you find on the `python-future` [bug tracker][6].

## Should I import unicode_literals?

The `future` package can be used with or without `unicode_literals` imports.

In general, it is more compelling to use `unicode_literals` when back-porting new or existing Python 3 code to Python 2/3 than when porting existing Python 2 code to 2/3. In the latter case, explicitly marking up all unicode string literals with `u''` prefixes would help to avoid unintentionally changing the existing Python 2 API. However, if changing the existing Python 2 API is not a concern, using `unicode_literals` may speed up the porting process.

This section summarizes the benefits and drawbacks of using `unicode_literals`. To avoid confusion, we recommend using `unicode_literals` everywhere across a code-base or not at all, instead of turning on for only some modules.

### Benefits

1. String literals are unicode on Python 3. Making them unicode on Python 2 leads to more consistency of your string types across the two runtimes. This can make it easier to understand and debug your code.
2. Code without `u''` prefixes is cleaner, one of the claimed advantages of Python 3. Even though some unicode strings would require a function call to invert them to native strings for some Python 2 APIs (see [Standard library incompatibilities][7]), the incidence of these function calls would usually be much lower than the incidence of `u''` prefixes for text strings in the absence of `unicode_literals`.
3. The diff when porting to a Python 2/3-compatible codebase may be smaller, less noisy, and easier to review with `unicode_literals` than if an explicit `u''` prefix is added to every unadorned string literal.
4. If support for Python 3.2 is required (e.g. for Ubuntu 12.04 LTS or Debian wheezy), `u''` prefixes are a `SyntaxError`, making `unicode_literals` the only option for a Python 2/3 compatible codebase. [However, note that `future` doesn't support Python 3.0-3.2.]

### Drawbacks

1. Adding `unicode_literals` to a module amounts to a "global flag day" for that module, changing the data types of all strings in the module at once. Cautious developers may prefer an incremental approach. (See [here][8] for an excellent article describing the superiority of an incremental patch-set in the the case of the Linux kernel.)
2. Changing to `unicode_literals` will likely introduce regressions on Python 2 that require an initial investment of time to find and fix. The APIs may be changed in subtle ways that are not immediately obvious.

An example on Python 2:
    
        ### Module: mypaths.py
    
    ...
    def unix_style_path(path):
        return path.replace('\', '/')
    ...
    
    ### User code:
    
    >>> path1 = '\Users\Ed'
    >>> unix_style_path(path1)
    '/Users/ed'
    

On Python 2, adding a `unicode_literals` import to `mypaths.py` would change the return type of the `unix_style_path` function from `str` to `unicode` in the user code, which is difficult to anticipate and probably unintended.

The counter-argument is that this code is broken, in a portability sense; we see this from Python 3 raising a `TypeError` upon passing the function a byte-string. The code needs to be changed to make explicit whether the `path` argument is to be a byte string or a unicode string.

3. With `unicode_literals` in effect, there is no way to specify a native string literal (`str` type on both platforms). This can be worked around as follows:
    
        >>> from __future__ import unicode_literals
    >>> ...
    >>> from future.utils import bytes_to_native_str as n
    
    >>> s = n(b'ABCD')
    >>> s
    'ABCD'  # on both Py2 and Py3
    

although this incurs a performance penalty (a function call and, on Py3, a `decode` method call.)

This is a little awkward because various Python library APIs (standard and non-standard) require a native string to be passed on both Py2 and Py3. (See [Standard library incompatibilities][7] for some examples. WSGI dictionaries are another.)

3. If a codebase already explicitly marks up all text with `u''` prefixes, and if support for Python versions 3.0-3.2 can be dropped, then removing the existing `u''` prefixes and replacing these with `unicode_literals` imports (the porting approach Django used) would introduce more noise into the patch and make it more difficult to review. However, note that the `futurize` script takes advantage of PEP 414 and does not remove explicit `u''` prefixes that already exist.

4. Turning on `unicode_literals` converts even docstrings to unicode, but Pydoc breaks with unicode docstrings containing non-ASCII characters for Python versions < 2.7.7. ([Fix committed][9] in Jan 2014.):
    
        >>> def f():
    ...     u"Author: Martin von Löwis"
    
    >>> help(f)
    
    /Users/schofield/Install/anaconda/python.app/Contents/lib/python2.7/pydoc.pyc in pipepager(text, cmd)
       1376     pipe = os.popen(cmd, 'w')
       1377     try:
    -> 1378         pipe.write(text)
       1379         pipe.close()
       1380     except IOError:
    
    UnicodeEncodeError: 'ascii' codec can't encode character u'xf6' in position 71: ordinal not in range(128)
    

See [this Stack Overflow thread][10] for other gotchas.

### Others' perspectives

Django recommends importing `unicode_literals` as its top [porting tip][11] for migrating Django extension modules to Python 3. The following [quote][12] is from Aymeric Augustin on 23 August 2012 regarding why he chose `unicode_literals` for the port of Django to a Python 2/3-compatible codebase.:

> "... I'd like to explain why this PEP [PEP 414, which allows explicit `u''` prefixes for unicode literals on Python 3.3+] is at odds with the porting philosophy I've applied to Django, and why I would have vetoed taking advantage of it.
> 
> "I believe that aiming for a Python 2 codebase with Python 3 compatibility hacks is a counter-productive way to port a project. You end up with all the drawbacks of Python 2 (including the legacy u prefixes) and none of the advantages Python 3 (especially the sane string handling).
> 
> "Working to write Python 3 code, with legacy compatibility for Python 2, is much more rewarding. Of course it takes more effort, but the results are much cleaner and much more maintainable. It's really about looking towards the future or towards the past.
> 
> "I understand the reasons why PEP 414 was proposed and why it was accepted. It makes sense for legacy software that is minimally maintained. I hope nobody puts Django in this category!"

> "There are so many subtle problems that `unicode_literals` causes. For instance lots of people accidentally introduce unicode into filenames and that seems to work, until they are using it on a system where there are unicode characters in the filesystem path."
> 
> —Armin Ronacher

> "+1 from me for avoiding the unicode_literals future, as it can have very strange side effects in Python 2.... This is one of the key reasons I backed Armin's PEP 414."
> 
> —Nick Coghlan

> "Yeah, one of the nuisances of the WSGI spec is that the header values IIRC are the str or StringType on both py2 and py3. With unicode_literals this causes hard-to-spot bugs, as some WSGI servers might be more tolerant than others, but usually using unicode in python 2 for WSGI headers will cause the response to fail."
> 
> —Antti Haapala

[1]: http://python-future.org/unicode_literals.html#unicode-literals
[2]: http://python-future.org/what_else.html#what-else
[3]: http://python-future.org/futurize.html#forwards-conversion-stage2
[4]: https://github.com/PythonCharmers/python-future
[5]: http://python-future.org/conversion_limitations.html#futurize-limitations
[6]: https://github.com/PythonCharmers/python-future/
[7]: http://python-future.org/stdlib_incompatibilities.html#stdlib-incompatibilities
[8]: http://lwn.net/Articles/165039/
[9]: http://bugs.python.org/issue1065986#msg207403
[10]: http://stackoverflow.com/questions/809796/any-gotchas-using-unicode-literals-in-python-2-6
[11]: https://docs.djangoproject.com/en/dev/topics/python3/#unicode-literals
[12]: https://groups.google.com/forum/#!topic/django-developers/2ddIWdicbNY
