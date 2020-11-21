<div style="text-align:center"><img src="./fleur.png" alt="flower" style="zoom:35%;" /></div>



---

# CheatSheet : Linux Users

---

## Sommaire

[TOC]





## Groups

### Add an user to a group

``` shell
usermod -aG <group> <user>
```







## Users changes

### Change username

``` shell
usermod -l <new username> <old username>
```



### Change home directory name

``` shell
usermod -d <new directory> <username>
```



### Change user informations

``` shell
usermod -c <new informations> <username>
```