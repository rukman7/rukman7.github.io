---
layout: post
title: Digging GIT history using 'git log'
tags:
  - GIT
---
### A good analogy
Sometimes while debugging/analysing a bug or issue in the code, It can be helping to review and analyse the history of changes that went into to file/directory. While most of the times simply looking at the code may give us what we need, Sometimes it can be time consuming. Looking at past history can render a better context and makes debugging a lot faster.

![house](../../../assets/images/Dr-House-13.jpg)
<div style="text-align: right"> <cite>image source: google</cite></div>

I like to compare this to Dr.house's approach. He sends his staffs to sneak into his patients house to look for clues relating to the patient's illness. While he is considered one of the best, He uses this sneaky way to cancel out and narrow down possibilities faster to diagnose the issue.

### Looking into git history using 'git log' command

Display previous changes in the current branch.

`git log`

Display history of changes with filenames for a specific directory or file.

`git log --name-status /path/to/file`

Display one line information with commit-id and commit message.

`git log --oneline /path/to/file`

Display changes along with file diff use `-c` flag.

`git log -c /path/to/file`

Search through the history for changes containing specific string.

`git log -S"string" /path/to/file`

The above command can be helpful when searching for changes that added or removed a specifc string.

Display log with number of insertions and deletions to each file in a commit.

`git log --stat /path/to/file`

Use `-n` flag to restrict search output to specific number of entries. Example,

`git log -10`

Do not diplay merge commits in the log.

`git log --no-merges`


Other advanced usages: \
[git log man page](http://web.mit.edu/git/www/git-log.html) \
[bitbucket git log](https://www.atlassian.com/git/tutorials/git-log)