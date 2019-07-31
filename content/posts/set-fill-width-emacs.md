+++
title = "How to Set the Fill Width In Emacs"
date = "2018-03-27"
author = "Alasdair Nicol"
cover = ""
tags = ["emacs"]
description = ""
showFullContent = false
+++

The [Django documentation guidelines][1] say to wrap documentation at
80 characters wide, but by default, Emacs wraps at 70 characters.

To change the value for the current session, you can do:

```
C-u 80 C-x f
```

Or to make the change permanently, you can add the following to your `.emacs`
file:

```
(setq-default fill-column 80)
```

For further info, see the Emacs docs for [fill-commands][2]. Thanks to @prosseek
for their [Stack Overflow Question][3].

[1]: https://docs.djangoproject.com/en/dev/internals/contributing/writing-documentation/#guidelines-for-restructuredtext-files
[2]: https://www.gnu.org/software/emacs/manual/html_node/emacs/Fill-Commands.html
[3]: https://stackoverflow.com/questions/3566727/how-to-set-the-default-width-of-fill-mode-to-80-with-emacs
