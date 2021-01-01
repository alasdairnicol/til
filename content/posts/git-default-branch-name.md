+++
title = "How to change the default initial branch for new Git repos"
date = "2021-01-01"
author = "Alasdair Nicol"
cover = ""
tags = ["git"]
description = "TLDR: - Use `git config --global init.defaultBranch main` to change the default initial branch to main"
showFullContent = false
+++

In Git [2.28][1], the `init.defaultBranch` option allows you to
specify the name of the initial branch for new repos.

To use `main`, which matches the default behaviour of GitHub
(configurable [here][2]), you can run:

```
git config --global init.defaultBranch main
```

If you prefer, you can edit your `.gitconfig` file directly and add
the following:

```
[init]
	defaultBranch = main
```

[1]: https://github.blog/2020-07-27-highlights-from-git-2-28/
[2]: https://github.com/settings/repositories
