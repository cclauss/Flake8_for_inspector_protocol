@thefourtheye Do you understand how to contribute a fix to
* https://bugs.chromium.org/p/chromium/issues/detail?id=914950

The four changes required are quite trivial but I really struggle with the chromium.org workflow which is quite different from GitHUb's workflow.

1. https://chromium.googlesource.com/deps/inspector_protocol/+/master/pdl.py#162 add __()__
2. https://chromium.googlesource.com/deps/inspector_protocol/+/master/check_protocol_compatibility.py#478 add __()__
3. https://chromium.googlesource.com/deps/inspector_protocol/+/master/check_protocol_compatibility.py#480 add __()__
4. https://chromium.googlesource.com/deps/inspector_protocol/+/master/code_generator.py#19 add the lines:
```python
try:
    xrange          # Python 2
except NameError:
    xrange = range  # Python 3
```
