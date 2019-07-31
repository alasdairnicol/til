+++
title = "How to add an SSH Key to the Agent for a Limited Time"
date = "2019-07-01"
author = "Alasdair Nicol"
cover = ""
tags = ["ssh"]
description = "TLDR: Use the `-t` flag to limit the time the agent will keep the key, e.g. `ssh-add -t 1h`"
showFullContent = false
+++

The `ssh-add` command has a `-t` flag to limit the time the agent will
keep the key. For example, to set a limit of 1 hour, you would do:

```
ssh-add -t 1h
```

You can also add an alias to `.bash_aliases` file, so that a limit is
used all the time:

```
alias ssh-add='ssh-add -t 1h'
```