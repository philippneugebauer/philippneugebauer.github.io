---
layout: post
title: Comparison of SmartGit and SourceTree
date: 2015-12-17 09:49:18 +1100
categories: git gui smartgit sourcetree comparison 
---

This blog post approaches the comparison of the git gui tools `SmartGit` 7.0.3 and `SourceTree` 1.6.23.0 on Windows.
I mostly use the command line for simple stuff, but I prefer gui tools for file merging and the faster separation of commits through `git add -p`. The comparison of both tools is divided into different categories to better highlight each's adavantages and disadvantages and represented in the following table.

||SmartGit|SourceTree|
|-------|------|
|**Text Comparison**|character by character|line by line, does not always work|
|**Binary Documents**|no support|content and diffs of pdfs and office documents are displayed
|||buttons for fast file opening|
|**License**|commercial: fee-based|free of charge, registration required|
|**Language**|english|system language|
|**Hunk Selection**|no selection of lines by cursor|selection of lines by cursor|
||sometimes no fine-granular hunk selection|bad recognition of hunks and no intuitive right-clicks|
|**Merging**|visualization and comparison|only whole file is displayed like in git|
||of different file states|console|
|**Miscellaneous**||wants to change git settings|
|||cannot consistently handle umlauts|

<br>

The code to demonstrate my findings is published in this [GitHub repository](https://github.com/philippneugebauer/git_gui_test).

Do you know other important factors I didn't consider? Do some points need to be clarified?
