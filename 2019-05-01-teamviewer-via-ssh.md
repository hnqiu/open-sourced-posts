---
title:  "Lanuch Teamviewer Through SSH"
date: 2019-05-01
last_modified_at: 2019-05-01
author: hnqiu
tags:
  - ssh
  - teamviewer
---

> :unlock: This post is [open-sourced](https://github.com/hnqiu/open-sourced-posts/blob/master/2019-05-01-teamviewer-via-ssh.md).

Even if we can [login to the server computer remotely via `ssh`](https://hnqiu.github.io/2019/04/30/using-ssh.html), sometimes it would be best to have graphical control of that machine. In this case, [Teamviewer](https://www.teamviewer.com/) is an ideal tool. 

One thing to be noted is, unlike terminal access, we can only have one screen to control. Therefore, only one user should be allowed to have graphical control at a time, otherwise everyone will be trying to take it over.

Before doing the following, we should have installed Teamviewer on both ends.  

1. `ssh` to the host
    ```
    ssh <user>@<ip_addr>
    ```

2. Check if teamviewer is available by `teamviewer help`. If no such command, find out where it is using `whereis teamviewer` and navigate to the location.

3. Get teamviewer id
    ```
    teamviewer info
    ```

4. Reset password (if necessary)
    ```
    sudo teamviewer passwd NewPassword
    ```

5. Enable and start teamviewer
    ```
    sudo teamviewer daemon enable
    sudo teamviewer daemon start
    ```

6. Log out `ssh` and use teamviewer to connect to the remote machine


#### Acknowledgement
This note is based on [TONI SOTO's blog](http://www.tonisoto.com/2013/07/launching-teamviewer-remotely-throught-ssh/).

