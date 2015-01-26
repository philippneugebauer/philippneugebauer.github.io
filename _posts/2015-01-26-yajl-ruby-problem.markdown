---
layout: post
title:  "Solve Yajl Liquid Exception"
date:   2015-01-26 20:00:00
categories: yajl windows liquid_execption
---

Had to solve `Liquid Exception: cannot load such file — yajl/2.1/yajl` to start blogging on GitHub.

[On Windows, you just need to change the highlighter if you don't want to install python](http://stackoverflow.com/questions/16498287/jekyll-liquid-exception-cannot-load-such-file-yajl-2-0-yajl).

Unfortunately, it mustn't be pushed to GitHub, because that would let to a `Page build failed.` which is also described [here](http://loyc.net/2014/blogging-on-github.html).

Jekyll 3.0 should resolve this issue when rouge hopefully becomes the [standard highlighter](https://github.com/jekyll/jekyll/issues/3157).
