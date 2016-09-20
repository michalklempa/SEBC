### `vm.swapiness`

 * Check swapinnes:
```
[ec2-user@ip-172-31-9-86 ~]$ cat /proc/sys/vm/swappiness
60
```
 * set to 1
```
[ec2-user@ip-172-31-9-86 ~]$ sudo sysctl -w vm.swappiness=1
vm.swappiness = 1
```

### `noatime` for all volumes except root
 * first of all, add a volume `/dev/xvdf` to the host using AWS Console
 * Create partitions
```
[root@ip-172-31-9-86 ec2-user]# sudo gdisk /dev/xvdf 
GPT fdisk (gdisk) version 0.8.10

Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.

Command (? for help): ? 
b	back up GPT data to a file
c	change a partition's name
d	delete a partition
i	show detailed information on a partition
l	list known partition types
n	add a new partition
o	create a new empty GUID partition table (GPT)
p	print the partition table
q	quit without saving changes
r	recovery and transformation options (experts only)
s	sort partitions
t	change a partition's type code
v	verify disk
w	write table to disk and exit
x	extra functionality (experts only)
?	print this menu

Command (? for help): o
This option deletes all partitions and creates a new protective MBR.
Proceed? (Y/N): y

Command (? for help): n
Partition number (1-128, default 1): 
First sector (34-209715166, default = 2048) or {+-}size{KMGTP}: 
Last sector (2048-209715166, default = 209715166) or {+-}size{KMGTP}: 
Current type is 'Linux filesystem'
Hex code or GUID (L to show codes, Enter = 8300): 
Changed type of partition to 'Linux filesystem'

Command (? for help): p
Disk /dev/xvdf: 209715200 sectors, 100.0 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 4DDAB368-FCC3-466B-B40C-D4CFD5B9BA01
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 209715166
Partitions will be aligned on 2048-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048       209715166   100.0 GiB   8300  Linux filesystem

Command (? for help): w

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): y
OK; writing new GUID partition table (GPT) to /dev/xvdf.
The operation has completed successfully.
```
 * make filesystem on new partition with 0% reserved space
```
[root@ip-172-31-9-86 ec2-user]# sudo mkfs.ext4 /dev/xvdf1 -m 0
mke2fs 1.41.12 (17-May-2010)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
6553600 inodes, 26214139 blocks
0 blocks (0.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
800 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 25 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
```
 * setup fstab to mount new filesystem.
```
[root@ip-172-31-9-86 ec2-user]# blkid
/dev/xvda1: UUID="1b7ea291-67b4-48da-802a-be4b2bcb64d5" TYPE="ext4" 
    /dev/xvdf1: UUID="d0201af3-3231-43a2-bab5-5cd7e0ca12aa" TYPE="ext4" 
```
 * `vim /etc/fstab` add the line for the new disk (2nd line in this listing):
```
#
# /etc/fstab
# Created by anaconda on Tue Apr 12 19:19:11 2016
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=1b7ea291-67b4-48da-802a-be4b2bcb64d5 /                       ext4    defaults        1 1
UUID=d0201af3-3231-43a2-bab5-5cd7e0ca12aa /data/1                       ext4    defaults,noatime        0 2
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
```
 * create mount point
```
[root@ip-172-31-9-86 ec2-user]# mkdir -p /data/1
[root@ip-172-31-9-86 ec2-user]# mount -a
[root@ip-172-31-9-86 ec2-user]# mount
/dev/xvda1 on / type ext4 (rw)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw,rootcontext="system_u:object_r:tmpfs_t:s0")
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/xvdf1 on /data/1 type ext4 (rw,noatime)
```
* "Check the user limits for maximum file descriptors and processes" - well, there are no hadoop users, yet. skipping. According to http://www.cloudera.com/documentation/enterprise/latest/topics/cm_mc_max_fd.html , this can be done later using CM.
* DNS configured using Route 53. Set hostname:
```
hostname klempa1.cdh.seb
```
* Check reverse lookups:
```
[root@ip-172-31-9-86 ~]# host 172.31.9.86
86.9.31.172.in-addr.arpa domain name pointer klempa1.cdh.seb.
[root@ip-172-31-9-86 ~]# host 172.31.9.84
84.9.31.172.in-addr.arpa domain name pointer klempa2.cdh.seb.
[root@ip-172-31-9-86 ~]# host 172.31.9.85
85.9.31.172.in-addr.arpa domain name pointer klempa3.cdh.seb.
[root@ip-172-31-9-86 ~]# host 172.31.9.82
82.9.31.172.in-addr.arpa domain name pointer klempa4.cdh.seb.
[root@ip-172-31-9-86 ~]# host 172.31.9.83
83.9.31.172.in-addr.arpa domain name pointer klempa5.cdh.deb.
```
* Check forward lookups
```
[root@ip-172-31-9-86 ~]# host klempa1.cdh.seb
klempa1.cdh.seb has address 172.31.9.86
[root@ip-172-31-9-86 ~]# host klempa1.cdh.seb
klempa1.cdh.seb has address 172.31.9.86
[root@ip-172-31-9-86 ~]# host klempa2.cdh.seb
klempa2.cdh.seb has address 172.31.9.84
[root@ip-172-31-9-86 ~]# host klempa3.cdh.seb
klempa3.cdh.seb has address 172.31.9.85
[root@ip-172-31-9-86 ~]# host klempa4.cdh.seb
klempa4.cdh.seb has address 172.31.9.82
[root@ip-172-31-9-86 ~]# host klempa5.cdh.seb
klempa5.cdh.seb has address 172.31.9.83
```
* nscd:
```
[root@ip-172-31-9-86 ec2-user]# yum install nscd -y
...
[root@ip-172-31-9-86 ec2-user]# chkconfig --list nscd
nscd           	0:off	1:off	2:off	3:off	4:off	5:off	6:off
[root@ip-172-31-9-86 ec2-user]# chkconfig nscd on
[root@ip-172-31-9-86 ec2-user]# chkconfig --list nscd
nscd           	0:off	1:off	2:on	3:on	4:on	5:on	6:off
```
* ntpd, check and enable
```
[root@ip-172-31-9-86 ec2-user]# chkconfig --list ntpd
ntpd           	0:off	1:off	2:off	3:off	4:off	5:off	6:off
[root@ip-172-31-9-86 ec2-user]# chkconfig ntpd on
[root@ip-172-31-9-86 ec2-user]# chkconfig --list ntpd
ntpd           	0:off	1:off	2:on	3:on	4:on	5:on	6:off
```
