---
layout: post
title: Git Windows Path Problem
date: 2015-04-09 00:45:14 +0200
categories: git windows path
---

Not the first time I ran in the problem that the `.ssh` folder in Windows changed from the `.ssh` of the specific 
`user folder` to the `folder of the Git installation`. Now I tried to investigate what actually causes the problem.

I was able to verify that the presence of the binaries of the Git installation in the `Windows PATH` was 
responsible for the problem, e.g. `C:\Program Files (x86)\Git\bin`. Unfortunately, I wasn't able to solve
or understand it, but I suggest a better way to get around the problem. Furthermore, the problem also affects
only the Windows command line but not Git tools like `SourceTree`.

Although the simplest solution is just to copy the `.ssh folder` so that consequently 2 ssh key locations exist,
I suggest to create a symbolic link on Windows by executing 
`mklink /D your_git_installation_path/.ssh your_user_folder\.ssh`
which allows you to avoid the redundancy of two same folders.
