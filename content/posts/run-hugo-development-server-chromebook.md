+++
title = "How to Run the Hugo Development Server on a Chromebook"
date = "2019-07-30"
author = "Alasdair Nicol"
cover = ""
tags = ["hugo", "chromebook"]
description = "TLDR: - Use `hugo server -D -p 8080` to listen on port 8080, then open http://localhost:8080."
showFullContent = false
+++

If you run `hugo server -D` on a Chromebook, and navigate to
http://localhost:1313, then you'll get the error message *This site
can't be reached. localhost refused to connect*.

The problem is that the hugo server isn't running directly on your
Chromebook, it's running on a Linux container. The default container
has a hostname `penguin.linux.test` which you can use to access the
site with a couple of extra flags:

 * use `--bind 0.0.0.0` binds to all IP addresses instead of the
   default `127.0.0.1`

 * use `--baseURL http://penguin.linux.test/` to specify the root,
   otherwise the server will rewrite all links to
   http://localhost:1313, which will break links to other pages and
   CSS.

Putting these together, you should run:

```
hugo server -D --bind 0.0.0.0 --baseURL http://penguin.linux.test/
```

Then access your site at http://penguin.linux.test:1313.

In the above commands, the `-D` flag (or `--buildDrafts`) tells the
server to include content marked as draft.


## A simpler alternative

Well known ports like 8000 and 8080 [are forwarded to the linux
container][1]. By default, the Hugo server runs on port 1313 which is
not forwarded, so use the -p flag to listen on a different
port, for example 8080:

```
hugo server -D -p 8080
```

Then access the server at http://localhost:8080.

[1]: https://www.reddit.com/r/Crostini/comments/99s3t9/wellknown_ports_are_now_autoforwarded_to_the/
