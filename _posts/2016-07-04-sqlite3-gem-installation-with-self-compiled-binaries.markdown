---
layout: post
title: Sqlite3 Gem Installation with self Compiled Binaries
date: 2016-07-04 21:53:33 +0200
categories: windows ruby rails gem sqlite3
---

The hardest problem to solve by using a new version of Ruby for Rails on Windows had always been the absence of precompiled binaries for the sqlite3 gem.
Since there exist many solutions which did not work out on my environments, I present the working solution which I successfully applied.

First, you need to download `sqlite-autoconf-xxx.tar.gz` and `sqlite-dll-winyy-xyy-xxx.zip` from [sqlite.org](www.sqlite.org).
In the second step, you extract both files to the same directory on your system but you also need to copy the `dll files` to a folder contained by your `system $path`.
Next, you open a linux terminal in your sqlite folder, e.g. the `msys.bat` in your `DevKit` folder.
Then, you execute the three following commands which compile the sqlite3 code:

```
./configure
make
make install
```

After the successful compilation, you can install your sqlite3 gem whereby `path` represents the binary folder:

```
gem install sqlite3 --platform=ruby -- --with-sqlite3-include=path --with-sqlite3-lib=path --with-sqlite3-dir=path
```

### Errors

If you get a `checking for sqlite3_libversion_number() in -lsqlite3... no` error, you need to add `--with-sqlite3-dir=path` to gem installation command.

If you receive a `checking for sqlite3.h... no` error, then your pointed path does not include the binaries of sqlite.

Sources:
[GitHub](https://github.com/sparklemotion/sqlite3-ruby/issues/82)
[StackOverflow](http://stackoverflow.com/questions/15480381/how-do-i-install-sqlite3-for-ruby-on-windows)

