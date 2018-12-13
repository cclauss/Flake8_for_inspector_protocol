# Flake8 testing of inspector protocol
### print() is a function in Python 3
### xrange() was removed in Python 3 in favor of a reworked version of range()

* $ `git clone https://chromium.googlesource.com/deps/inspector_protocol
* $ `flake8 . --count --select=E901,E999,F821,F822,F823 --show-source --statistics

Current Travis CI results: https://travis-ci.com/cclauss/Flake8_for_inspector_protocol

[flake8](http://flake8.pycqa.org) testing of https://chromium.googlesource.com/deps/inspector_protocol on Python 3.7.1

```
./check_protocol_compatibility.py:478:46: E999 SyntaxError: invalid syntax
            print "  Public changes since %s:" % version
                                             ^
./code_generator.py:43:18: F821 undefined name 'xrange'
        for i in xrange(len(keys)):
                 ^
./pdl.py:162:51: E999 SyntaxError: invalid syntax
        print 'Error in %s:%s, illegal token: \t%s' % (file_name, i, line)
                                                  ^
2     E999 SyntaxError: invalid syntax
1     F821 undefined name 'xrange'
3
```

__E901,E999,F821,F822,F823__ are the "_showstopper_" [flake8](http://flake8.pycqa.org) issues that can halt the runtime with a SyntaxError, NameError, etc. Most other flake8 issues are merely "style violations" -- useful for readability but they do not effect runtime safety.
* F821: undefined name `name`
* F822: undefined name `name` in `__all__`
* F823: local variable name referenced before assignment
* E901: SyntaxError or IndentationError
* E999: SyntaxError -- failed to compile a file into an Abstract Syntax Tree
