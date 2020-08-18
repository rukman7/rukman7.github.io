---
layout: post
title: Linux file permissions
tags:
  - linux
  - file permissions
---
![file folder](../../../assets/images/omid-kashmari-s34f0Wxbens-unsplash.jpg)
<div style="text-align: right"> <cite><span>Photo by <a href="https://unsplash.com/@omidkashmari?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Omid Kashmari</a> on <a href="https://unsplash.com/s/photos/files?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Unsplash</a></span></cite></div>

### Permission groups
1. owner - owner of the file.
2. group - a group of users.
3. others - basically everyone. 

### Permission types
1. read
2. write
3. execute

### Changing permissions using numeric code

Code | Permission | Symbol
------- | -------
0	| No Permission	| - - -
1	| Execute	| - - x
2	| Write	| - w -
3	| Execute + Write	| - w x
4	| Read | r - -
5	| Read + Execute | r - x
6	| Read +Write	| r w -
7	| Read + Write +Execute | r w x

### Commands for changing file/directory permissions
Viewing permission of a directory or a file.
```
ls -l    #linux
ls -lthr #OSX
```
Changing file permission of a directory/file.
```
#sets full access for owner and read + execute permission for group and others.
chmod 755 /path/to/directory  
```
Changing file permissions for a directory and its contents recursively.
```
chmod -R 755 /path/to/directory
```
### Changing owner of a file or directory
```
chown rukman spring_security
#for recursively changing ownership -R can be used.
```
Where rukman should be one the user in the system.
### Changing group ownership of a file or directory
```
chgrp group1 path/to/file
```
Where group1 is one of the member of user groups in the system.
### Other usages
Setting permission and ownership upon creating a directory.
```
sudo install --owner=rabbitmq --group=rabbitmq --mode=755 \
--directory /var/lib/messageQ/rabbitmq/server

#the install command would also create missing parent directories.
```

#### useful links:
[pluralsight - linux file permissions](https://www.pluralsight.com/blog/it-ops/linux-file-permissions) \
[install command - man page](https://linux.die.net/man/1/install)


