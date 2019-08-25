
[Source](http://python-future.org/compatible_idioms.html "Permalink to Writing Python 2-3 compatible code — Python-Future documentation")

# Writing Python 2-3 compatible code — Python-Future documentation

### Unicode (text) string literals

If you are upgrading an existing Python 2 codebase, it may be preferable to mark up all string literals as unicode explicitly with `u` prefixes:
    
    
    # Python 2 only
    s1 = 'The Zen of Python'
    s2 = u'きたないのよりきれいな方がいいn'
    
    # Python 2 and 3
    s1 = u'The Zen of Python'
    s2 = u'きたないのよりきれいな方がいいn'
    

The `futurize` and `python-modernize` tools do not currently offer an option to do this automatically.

If you are writing code for a new project or new codebase, you can use this idiom to make all string literals in a module unicode strings:
    
    
    # Python 2 and 3
    from __future__ import unicode_literals    # at top of module
    
    s1 = 'The Zen of Python'
    s2 = 'きたないのよりきれいな方がいいn'
    

See  for more discussion on which style to use.

### Byte-string literals
    
    
    # Python 2 only
    s = 'This must be a byte-string'
    
    # Python 2 and 3
    s = b'This must be a byte-string'
    

To loop over a byte-string with possible high-bit characters, obtaining each character as a byte-string of length 1:
    
    
    # Python 2 only:
    for bytechar in 'byte-string with high-bit chars like xf9':
        ...
    
    # Python 3 only:
    for myint in b'byte-string with high-bit chars like xf9':
        bytechar = bytes([myint])
    
    # Python 2 and 3:
    from builtins import bytes
    for myint in bytes(b'byte-string with high-bit chars like xf9'):
        bytechar = bytes([myint])
    

As an alternative, `chr()` and `.encode('latin-1')` can be used to convert an int into a 1-char byte string:
    
    
    # Python 3 only:
    for myint in b'byte-string with high-bit chars like xf9':
        char = chr(myint)    # returns a unicode string
        bytechar = char.encode('latin-1')
    
    # Python 2 and 3:
    from builtins import bytes, chr
    for myint in bytes(b'byte-string with high-bit chars like xf9'):
        char = chr(myint)    # returns a unicode string
        bytechar = char.encode('latin-1')    # forces returning a byte str
   
