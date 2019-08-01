+++
title = "Run Python 2 with the -3 Flag To Detect Compatibility Issues"
date = "2019-07-31"
author = "Alasdair Nicol"
cover = ""
tags = ["python"]
description = "TLDR: Use `python -3` to see warnings about compatibility issues with your Python 2 code."
showFullContent = false
+++

Python 2 has a [-3 flag][1] that warns about compatibility issues
encountered at runtime.

Consider the following example files `division.py` and `test_division.py`.

```python
# division.py
def classic_division(x, y):
    return x / y

If __name__ == "__main__":
    x = 10
    y = 3
    print(classic_division(x, y))
```

```python
# test_division.py
from division import classic_division

def test_classic_division():
    assert classic_division(10, 3) == 3
``` 

If you run python with the `-3` flag, then the classic division will
cause a deprecation warning.

```
python -3 division.py
division.py:2: DeprecationWarning: classic int division
  return x / y
  3
```

You can also use the flag when you run your tests using pytest:

```
$ python -3 -m pytest test_division.py
<snip>
  ====================== test session starts =======================
  platform linux2 -- Python 2.7.13, pytest-4.6.4, py-1.8.0, pluggy-0.12.0
  rootdir: /home/alasdair
  collected 1 item

test_division.py .                                         [100%]

======================== warnings summary ========================
test_division.py::test_classic_division
  /home/alasdair/division.py:2: DeprecationWarning: classic int division
      return x / y

-- Docs: https://docs.pytest.org/en/latest/warnings.html
============== 1 passed, 1 warnings in 0.01 seconds ==============
```

[1]: https://docs.python.org/2/howto/pyporting.html#prevent-compatibility-regressions