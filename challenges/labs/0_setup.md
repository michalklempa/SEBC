* us-east-1
* ami-23abb849
* 54.209.111.254
```
[root@klempa1 ec2-user]# ls /usr/java
ls: cannot access /usr/java: No such file or directory
```
```
[root@klempa1 ec2-user]# cat /etc/passwd | grep christie
christie:x:2500:501::/home/christie:/bin/bash
[root@klempa1 ec2-user]# cat /etc/passwd | grep weiner
weiner:x:2501:502::/home/weiner:/bin/bash
[root@klempa1 ec2-user]# cat /etc/group | grep pictures
pictures:x:503:weiner
[root@klempa1 ec2-user]# cat /etc/group | grep bridges
bridges:x:504:christie
```
```
[root@klempa2 yum.repos.d]# cat /etc/passwd | grep christie
christie:x:2500:501::/home/christie:/bin/bash
[root@klempa2 yum.repos.d]# cat /etc/passwd | grep weiner
weiner:x:2501:502::/home/weiner:/bin/bash
[root@klempa2 yum.repos.d]# cat /etc/group | grep pictures
pictures:x:503:weiner
[root@klempa2 yum.repos.d]# cat /etc/group | grep bridges
bridges:x:504:christie
```
```
[root@klempa3 ec2-user]# cat /etc/passwd | grep christie
christie:x:2500:501::/home/christie:/bin/bash
[root@klempa3 ec2-user]# cat /etc/passwd | grep weiner
weiner:x:2501:502::/home/weiner:/bin/bash
[root@klempa3 ec2-user]# cat /etc/group | grep pictures
pictures:x:503:weiner
[root@klempa3 ec2-user]# cat /etc/group | grep bridges
bridges:x:504:christie
```

```
[root@klempa4 ec2-user]# cat /etc/passwd | grep christie
christie:x:2500:501::/home/christie:/bin/bash
[root@klempa4 ec2-user]# cat /etc/passwd | grep weiner
weiner:x:2501:502::/home/weiner:/bin/bash
[root@klempa4 ec2-user]# cat /etc/group | grep pictures
pictures:x:503:weiner
[root@klempa4 ec2-user]# cat /etc/group | grep bridges
bridges:x:504:christie

```

```
[root@klempa5 ec2-user]# cat /etc/passwd | grep christie
christie:x:2500:501::/home/christie:/bin/bash
[root@klempa5 ec2-user]# cat /etc/passwd | grep weiner
weiner:x:2501:502::/home/weiner:/bin/bash
[root@klempa5 ec2-user]# cat /etc/group | grep pictures
pictures:x:503:weiner
[root@klempa5 ec2-user]# cat /etc/group | grep bridges
bridges:x:504:christie
```
