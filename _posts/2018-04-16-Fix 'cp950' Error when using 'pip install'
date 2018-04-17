---
title:  "Fix 'cp950' Error when using 'pip install'"
header:
  teaser: "Fix 'cp950' Error when using 'pip install'"
categories: 
  - pip, python, pip
tags:
  - pip
  - python
---

## Error info
```
UnicodeDecodeError: '???' codec can't decode byte 0xaa in position 999: illegal multibyte sequence
```
Got this kind of error msg when calling 'pip install jws' on Windows 10.

It's a bug from the package, it should consider the ecnoding problem in it's setup.py

## Solution

- use `pip download jws` instead of 'pip install'
- use `7z` open the `filename.tar.gz` archive
- edit the `setup.py` 
  ``` git
  - return open(os.path.join(os.path.dirname(__file__), fname).read()
  + return open(os.path.join(os.path.dirname(__file__), fname), encoding="UTF-8").read()
  ```
- Re-archive the tar file, run `pip install filename.tar`


### Reference
https://github.com/brianloveswords/python-jws/pull/35
