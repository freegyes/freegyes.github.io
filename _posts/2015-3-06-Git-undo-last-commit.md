---
layout: post
title: GIT: undo last commit, keep commit message
tags:
- git
---

````
$ git commit ...              (1)
$ git reset --soft HEAD~1     (2)
<< edit files as necessary >> (3)
$ git add ....                (4)
$ git commit -c ORIG_HEAD     (5)
````

thank you [stackoverflow](http://stackoverflow.com/questions/927358/how-to-undo-the-last-commit)