---
layout: post
title: Resetting local branch with remote branch
tags:
  - git
---
### Commands
From the branch that needs to be resetted, issue the following commands:
```
git fetch origin
git reset --hard origin/<branch>
```

Warning!
This will delete all the uncommitted files in that local branch. Hence is its good to commit or stash the required changes before doing hard reset. 
