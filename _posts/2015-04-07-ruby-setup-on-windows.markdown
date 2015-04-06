---
layout: post
title:  Ruby Setup On Windows
date:   2015-04-07 1:15:00
categories: ruby setup windwos
---

First, download the `ruby installer` and the appropriate `development kit` from [http://rubyinstaller.org/]().
Afterwards, follow the [instructions](https://github.com/oneclick/rubyinstaller/wiki/Development-Kit).

`HINT: The installation path must NOT contain whitespaces, therefore e.g. C:\Program Files\ is a bad folder!`

Finally, execute the following commands and then start developing:

```ruby
gem update --system
gem install bundler
bundle
```