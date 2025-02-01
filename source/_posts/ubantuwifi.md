title: 乌班图重启网络服务命令
date: 2025-2-1 10:49:32
tags:
-----

在终端下输入：

```
sudo service NetworkManager stop 
 
sudo rm /var/lib/NetworkManager/NetworkManager.state 
 
sudo service NetworkManager start

```
