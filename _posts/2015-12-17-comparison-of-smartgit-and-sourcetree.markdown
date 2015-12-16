---
layout: post
title: Comparison of SmartGit and SourceTree
date: 2015-12-17 00:17:18 +1100
categories: git gui smartgit sourcetree comparison 
---

This blog post handles the comparison of the git gui tools `SmartGit` 7.0.3 and `SourceTree` 1.6.23.0 on Windows.
For simple stuff I mostly use the command line, but I prefer gui tools for file merging and the faster separation of commits through `git add -p`. The comparison of both tools is divided into different categories to better highlight each's adavantages and disadvantages and represented in the following table.

||SmartGit|SourceTree|
|Text comparison|character by character|line by line, does not always work|
|Binary documents|no support|content and diffs of pdfs and office documents is displayed and buttons for fast file opening|
|License|commercial: fee-based|free of charge, registration required|
|Language|english|system language|
|Hunk selection|no selection of lines by cursor, maybe no fine-granular hunk selection|selection of lines by cursor, right click does not work, bad recognition of hunks|
|Merging|Visualization and comparison of different file states|Only whole file like in git console is displayed|
|Miscellaneous||wants to change git settings|
|||cannot consistently handle umlauts|

The code to demonstrate my findings is published in this [GitHub repository](https://github.com/philippneugebauer/git_gui_test).

Do you know other important factors I didn't consider? Do some points needed to be clarified?
