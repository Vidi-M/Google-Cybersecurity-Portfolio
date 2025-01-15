# Use Linux commands to manage file permissions

## Overview
In this activity, you will create a new portfolio document to demonstrate your experience using Linux commands to manage file permissions. This scenario is connected to the lab you have just completed about how to examine and manage file permissions. You will explain the commands you used in that lab.

## Scenario
You are a security professional at a large organization. You mainly work with their research team. Part of your job is to ensure users on this team are authorized with the appropriate permissions. This helps keep the system secure. 

Your task is to examine existing permissions on the file system. You’ll need to determine if the permissions match the authorization that should be given. If they do not match, you’ll need to modify the permissions to authorize the appropriate users and remove any unauthorized access.

## Permission Strings
Permissions are shown by 10-character strings.

| **Character** | **Example**   | **Meaning**                                           |
|---------------|---------------|-------------------------------------------------------|
| **1st**       | **d** rwxrwxrwx    | File type                                             |
|               | d             | for directory                                         |
|               | -             | for a regular file                                    |
| **2nd**       | d **r** wxrwxrwx    | Read permissions for the user                         |
|               | r             | if the user has read permissions                      |
|               | -             | if the user lacks read permissions                    |
| **3rd**       | dr **w** xrwxrwx    | Write permissions for the user                        |
|               | w             | if the user has write permissions                     |
|               | -             | if the user lacks write permissions                   |
| **4th**       | drw **x** rwxrwx    | Execute permissions for the user                      |
|               | x             | if the user has execute permissions                   |
|               | -             | if the user lacks execute permissions                 |
| **5th**       | drwx **r** wxrwx    | Read permissions for the group                        |
|               | r             | if the group has read permissions                     |
|               | -             | if the group lacks read permissions                   |
| **6th**       | drwxr **w** xrwx    | Write permissions for the group                       |
|               | w             | if the group has write permissions                    |
|               | -             | if the group lacks write permissions                  |
| **7th**       | drwxrw **x** rwx    | Execute permissions for the group                     |
|               | x             | if the group has execute permissions                  |
|               | -             | if the group lacks execute permissions                |
| **8th**       | drwxrwx **r** wx    | Read permissions for other                            |
|               | r             | if the other owner type has read permissions          |
|               | -             | if the other owner type lacks read permissions        |
| **9th**       | drwxrwxr **w** x    | Write permissions for other                           |
|               | w             | if the other owner type has write permissions         |
|               | -             | if the other owner type lacks write permissions       |
| **10th**      | drwxrwxrw **x**   | Execute permissions for other                         |
|               | x             | if the other owner type has execute permissions       |
|               | -             | if the other owner type lacks execute permissions     |

### Example

## File Permission Changes using Bash

## Project Description
## Check file and directory details
```
researcher2@3b8ec5424d48:~/projects$ ls -la
```
```
total 32
drwxr-xr-x 3 researcher2 research_team 4096 Jan 15 02:44 .
drwxr-xr-x 3 researcher2 research_team 4096 Jan 15 03:49 ..
-rw--w---- 1 researcher2 research_team   46 Jan 15 02:44 .project_x.txt
drwx--x--- 2 researcher2 research_team 4096 Jan 15 02:44 drafts
-rw-rw-rw- 1 researcher2 research_team   46 Jan 15 02:44 project_k.txt
-rw-r----- 1 researcher2 research_team   46 Jan 15 02:44 project_m.txt
-rw-rw-r-- 1 researcher2 research_team   46 Jan 15 02:44 project_r.txt
-rw-rw-r-- 1 researcher2 research_team   46 Jan 15 02:44 project_t.txt
```
## Describe a permission string
```
-rw-rw-r-- 1 researcher2 research_team   46 Jan 15 02:44 project_r.txt
```
- This is a file 

- reseacher2 = user >> has read and write permissions

- research_team = group >> has read and write permissions

- other >> has only read permissions
  
## Change file permissions
Taken away write permission from owner type other
```
-rw-rw-rw- 1 researcher2 research_team   46 Jan 15 02:44 project_k.txt
```
```
chmod o-w project_k.txt
```
```
-rw-rw-r-- 1 researcher2 research_team   46 Jan 15 02:44 project_k.txt
```
## Change file permissions on a hidden file
Both user and group permissions should be read only
```
-rw--w---- 1 researcher2 research_team   46 Jan 15 02:44 .project_x.txt
```
```
chmod u=r,g=r .project_x.txt
```
```
-r--r----- 1 researcher2 research_team   46 Jan 15 02:44 .project_x.txt
```
## Change directory permissions
```
drwx--x--- 2 researcher2 research_team 4096 Jan 15 02:44 drafts
```
```
chmod g-x drafts
```
```
drwx------ 2 researcher2 research_team 4096 Jan 15 02:44 drafts
```
## Summary
TODO

