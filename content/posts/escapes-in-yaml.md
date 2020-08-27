+++
title = "How to put \n in YAML"
date = "2020-08-27"
author = "Alasdair Nicol"
cover = ""
tags = ["yaml"]
description = "TLDR: - Use double quotes if you want to use `\n` to be treated as a newline e.g. `message: "hello\nworld"
showFullContent = false
+++

When loading a YAML file into Python, I found I was getting `\\n` instead of a newline `\n` as expected.

The solution was to switch from single quotes to double quotes.

```
>>> import yaml
>>> d = yaml.safe_load(r'''
... single: 'hello\nworld'
... double: "hello\nworld"
... ''')
>>> print(repr(d['single']))
'hello\\nworld'
>>> print(d['single'])
hello\nworld
>>> print(repr(d['double']))
'hello\nworld'
>>> print(d['double'])
hello
world
```
Hat tip to the excellent http://yaml-multiline.info, which has more examples.
