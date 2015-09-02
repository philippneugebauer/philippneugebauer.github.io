---
layout: post
title: Crazy mysql2 gem Error
date: 2015-09-02 00:30:43 +0200
categories: ruby mysql2-gem windows
---

I run at least the second time into the same crazy mysql2 gem error with Ruby on Windows
but I couldn't find any solution with Google.
So I came up with a revolutionary solution presented in the following.

The error message was `You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use (Mysql2::Error)`
although I was able to successfully query my database with this query.
After spending hours to identify the problem and to find a solution,
I just restarted my system. That fixed everything ...

Update: Another thing you should looking for are reserved keywords like `order` in MySQL which must be escaped by ```.

