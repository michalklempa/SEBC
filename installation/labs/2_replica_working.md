## Output of show slave status
```
*************************** 1. row ***************************
               Slave_IO_State: Waiting for master to send event
                  Master_Host: klempa1.cdh.seb
                  Master_User: replica
                  Master_Port: 3306
                Connect_Retry: 60
              Master_Log_File: mysql-bin.000003
          Read_Master_Log_Pos: 1378
               Relay_Log_File: mysqld-relay-bin.000002
                Relay_Log_Pos: 253
        Relay_Master_Log_File: mysql-bin.000003
             Slave_IO_Running: Yes
            Slave_SQL_Running: Yes
              Replicate_Do_DB: 
          Replicate_Ignore_DB: 
           Replicate_Do_Table: 
       Replicate_Ignore_Table: 
      Replicate_Wild_Do_Table: 
  Replicate_Wild_Ignore_Table: 
                   Last_Errno: 0
                   Last_Error: 
                 Skip_Counter: 0
          Exec_Master_Log_Pos: 1378
              Relay_Log_Space: 410
              Until_Condition: None
               Until_Log_File: 
                Until_Log_Pos: 0
           Master_SSL_Allowed: No
           Master_SSL_CA_File: 
           Master_SSL_CA_Path: 
              Master_SSL_Cert: 
            Master_SSL_Cipher: 
               Master_SSL_Key: 
        Seconds_Behind_Master: 0
Master_SSL_Verify_Server_Cert: No
                Last_IO_Errno: 0
                Last_IO_Error: 
               Last_SQL_Errno: 0
               Last_SQL_Error: 
  Replicate_Ignore_Server_Ids: 
             Master_Server_Id: 1
1 row in set (0.00 sec)

```
## Installation steps

### Install mysql
* Download mysql yum repository .rpm 
```
[ec2-user@klempa2 ~]$ wget http://dev.mysql.com/get/mysql57-community-release-el6-9.noarch.rpm
--2016-09-19 20:26:47--  http://dev.mysql.com/get/mysql57-community-release-el6-9.noarch.rpm
Resolving dev.mysql.com... 137.254.60.11
Connecting to dev.mysql.com|137.254.60.11|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://repo.mysql.com//mysql57-community-release-el6-9.noarch.rpm [following]
--2016-09-19 20:26:47--  http://repo.mysql.com//mysql57-community-release-el6-9.noarch.rpm
Resolving repo.mysql.com... 104.118.184.45
Connecting to repo.mysql.com|104.118.184.45|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 9216 (9,0K) [application/x-redhat-package-manager]
Saving to: “mysql57-community-release-el6-9.noarch.rpm”

100%[==================================================================================================================================================================>] 9 216       --.-K/s   in 0s      

2016-09-19 20:26:47 (634 MB/s) - “mysql57-community-release-el6-9.noarch.rpm” saved [9216/9216]

```
* install it
```
[ec2-user@klempa2 ~]$ sudo rpm -Uvh mysql57-community-release-el6-9.noarch.rpm 
warning: mysql57-community-release-el6-9.noarch.rpm: Header V3 DSA/SHA1 Signature, key ID 5072e1f5: NOKEY
Preparing...                ########################################### [100%]
   1:mysql57-community-relea########################################### [100%]
```
* enable 5.5 repository and disable 5.7 in repo descriptior
```
sudo vim /etc/yum.repos.d/mysql-community.repo
```
to look like
```
[mysql-connectors-community]
name=MySQL Connectors Community
baseurl=http://repo.mysql.com/yum/mysql-connectors-community/el/6/$basearch/
enabled=1
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-mysql

[mysql-tools-community]
name=MySQL Tools Community
baseurl=http://repo.mysql.com/yum/mysql-tools-community/el/6/$basearch/
enabled=1
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-mysql

# Enable to use MySQL 5.5
[mysql55-community]
name=MySQL 5.5 Community Server
baseurl=http://repo.mysql.com/yum/mysql-5.5-community/el/6/$basearch/
enabled=1
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-mysql

# Enable to use MySQL 5.6
[mysql56-community]
name=MySQL 5.6 Community Server
baseurl=http://repo.mysql.com/yum/mysql-5.6-community/el/6/$basearch/
enabled=0
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-mysql

[mysql57-community]
name=MySQL 5.7 Community Server
baseurl=http://repo.mysql.com/yum/mysql-5.7-community/el/6/$basearch/
enabled=0
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-mysql

[mysql80-community]
name=MySQL 8.0 Community Server
baseurl=http://repo.mysql.com/yum/mysql-8.0-community/el/6/$basearch/
enabled=0
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-mysql

[mysql-tools-preview]
name=MySQL Tools Preview
baseurl=http://repo.mysql.com/yum/mysql-tools-preview/el/6/$basearch/
enabled=0
gpgcheck=1
gpgkey=file:/etc/pki/rpm-gpg/RPM-GPG-KEY-mysql
```
* install mysql server
```
[root@klempa2 yum.repos.d]# sudo yum install mysql-community-server
Loaded plugins: amazon-id, rhui-lb, security
Setting up Install Process
Resolving Dependencies
--> Running transaction check
---> Package mysql-community-server.x86_64 0:5.5.52-2.el6 will be installed
--> Processing Dependency: mysql-community-common(x86-64) = 5.5.52-2.el6 for package: mysql-community-server-5.5.52-2.el6.x86_64
--> Processing Dependency: mysql-community-client(x86-64) >= 5.5.8 for package: mysql-community-server-5.5.52-2.el6.x86_64
--> Running transaction check
---> Package mysql-community-client.x86_64 0:5.5.52-2.el6 will be installed
--> Processing Dependency: mysql-community-libs(x86-64) >= 5.5.8 for package: mysql-community-client-5.5.52-2.el6.x86_64
---> Package mysql-community-common.x86_64 0:5.5.52-2.el6 will be installed
--> Running transaction check
---> Package mysql-community-libs.x86_64 0:5.5.52-2.el6 will be obsoleting
---> Package mysql-libs.x86_64 0:5.1.73-5.el6_7.1 will be obsoleted
--> Processing Dependency: libmysqlclient.so.16()(64bit) for package: 2:postfix-2.6.6-6.el6_7.1.x86_64
--> Processing Dependency: libmysqlclient.so.16(libmysqlclient_16)(64bit) for package: 2:postfix-2.6.6-6.el6_7.1.x86_64
--> Running transaction check
---> Package mysql-community-libs-compat.x86_64 0:5.5.52-2.el6 will be obsoleting
--> Finished Dependency Resolution

Dependencies Resolved

============================================================================================================================================================================================================
 Package                                                     Arch                                   Version                                         Repository                                         Size
============================================================================================================================================================================================================
Installing:
 mysql-community-libs                                        x86_64                                 5.5.52-2.el6                                    mysql55-community                                 1.7 M
     replacing  mysql-libs.x86_64 5.1.73-5.el6_7.1
 mysql-community-libs-compat                                 x86_64                                 5.5.52-2.el6                                    mysql55-community                                 1.6 M
     replacing  mysql-libs.x86_64 5.1.73-5.el6_7.1
 mysql-community-server                                      x86_64                                 5.5.52-2.el6                                    mysql55-community                                  38 M
Installing for dependencies:
 mysql-community-client                                      x86_64                                 5.5.52-2.el6                                    mysql55-community                                  15 M
 mysql-community-common                                      x86_64                                 5.5.52-2.el6                                    mysql55-community                                 277 k

Transaction Summary
============================================================================================================================================================================================================
Install       5 Package(s)

Total download size: 56 M
Is this ok [y/N]: y
Downloading Packages:
(1/5): mysql-community-client-5.5.52-2.el6.x86_64.rpm                                                                                                                                |  15 MB     00:00     
(2/5): mysql-community-common-5.5.52-2.el6.x86_64.rpm                                                                                                                                | 277 kB     00:00     
(3/5): mysql-community-libs-5.5.52-2.el6.x86_64.rpm                                                                                                                                  | 1.7 MB     00:00     
(4/5): mysql-community-libs-compat-5.5.52-2.el6.x86_64.rpm                                                                                                                           | 1.6 MB     00:00     
(5/5): mysql-community-server-5.5.52-2.el6.x86_64.rpm                                                                                                                                |  38 MB     00:00     
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                                                                                        31 MB/s |  56 MB     00:01     
Running rpm_check_debug
Running Transaction Test
Transaction Test Succeeded
Running Transaction
  Installing : mysql-community-common-5.5.52-2.el6.x86_64                                                                                                                                               1/6 
  Installing : mysql-community-libs-5.5.52-2.el6.x86_64                                                                                                                                                 2/6 
  Installing : mysql-community-client-5.5.52-2.el6.x86_64                                                                                                                                               3/6 
  Installing : mysql-community-server-5.5.52-2.el6.x86_64                                                                                                                                               4/6 
  Installing : mysql-community-libs-compat-5.5.52-2.el6.x86_64                                                                                                                                          5/6 
  Erasing    : mysql-libs-5.1.73-5.el6_7.1.x86_64                                                                                                                                                       6/6 
  Verifying  : mysql-community-common-5.5.52-2.el6.x86_64                                                                                                                                               1/6 
  Verifying  : mysql-community-libs-5.5.52-2.el6.x86_64                                                                                                                                                 2/6 
  Verifying  : mysql-community-server-5.5.52-2.el6.x86_64                                                                                                                                               3/6 
  Verifying  : mysql-community-libs-compat-5.5.52-2.el6.x86_64                                                                                                                                          4/6 
  Verifying  : mysql-community-client-5.5.52-2.el6.x86_64                                                                                                                                               5/6 
  Verifying  : mysql-libs-5.1.73-5.el6_7.1.x86_64                                                                                                                                                       6/6 

Installed:
  mysql-community-libs.x86_64 0:5.5.52-2.el6                      mysql-community-libs-compat.x86_64 0:5.5.52-2.el6                      mysql-community-server.x86_64 0:5.5.52-2.el6                     

Dependency Installed:
  mysql-community-client.x86_64 0:5.5.52-2.el6                                                         mysql-community-common.x86_64 0:5.5.52-2.el6                                                        

Replaced:
  mysql-libs.x86_64 0:5.1.73-5.el6_7.1                                                                                                                                                                      

Complete!

```
* on other nodes, install only client:
```
[ec2-user@klempa3 ~]$ sudo rpm -Uvh mysql57-community-release-el6-9.noarch.rpm 
warning: mysql57-community-release-el6-9.noarch.rpm: Header V3 DSA/SHA1 Signature, key ID 5072e1f5: NOKEY
Preparing...                ########################################### [100%]
   1:mysql57-community-relea########################################### [100%]
[ec2-user@klempa3 ~]$ sudo vim /etc/yum.repos.d/mysql-community.repo
[ec2-user@klempa3 ~]$ sudo yum install mysql-community-client
Loaded plugins: amazon-id, rhui-lb, security
Setting up Install Process
mysql-connectors-community                                                                                                                                                           | 2.5 kB     00:00     
mysql-connectors-community/primary_db                                                                                                                                                | 9.9 kB     00:00     
mysql-tools-community                                                                                                                                                                | 2.5 kB     00:00     
mysql-tools-community/primary_db                                                                                                                                                     |  31 kB     00:00     
mysql55-community                                                                                                                                                                    | 2.5 kB     00:00     
mysql55-community/primary_db                                                                                                                                                         | 147 kB     00:00     
Resolving Dependencies
--> Running transaction check
---> Package mysql-community-client.x86_64 0:5.5.52-2.el6 will be installed
--> Processing Dependency: mysql-community-libs(x86-64) >= 5.5.8 for package: mysql-community-client-5.5.52-2.el6.x86_64
--> Running transaction check
---> Package mysql-community-libs.x86_64 0:5.5.52-2.el6 will be obsoleting
--> Processing Dependency: mysql-community-common(x86-64) >= 5.5.8 for package: mysql-community-libs-5.5.52-2.el6.x86_64
---> Package mysql-libs.x86_64 0:5.1.73-5.el6_7.1 will be obsoleted
--> Processing Dependency: libmysqlclient.so.16()(64bit) for package: 2:postfix-2.6.6-6.el6_7.1.x86_64
--> Processing Dependency: libmysqlclient.so.16(libmysqlclient_16)(64bit) for package: 2:postfix-2.6.6-6.el6_7.1.x86_64
--> Running transaction check
---> Package mysql-community-common.x86_64 0:5.5.52-2.el6 will be installed
---> Package mysql-community-libs-compat.x86_64 0:5.5.52-2.el6 will be obsoleting
--> Finished Dependency Resolution

Dependencies Resolved

============================================================================================================================================================================================================
 Package                                                     Arch                                   Version                                         Repository                                         Size
============================================================================================================================================================================================================
Installing:
 mysql-community-client                                      x86_64                                 5.5.52-2.el6                                    mysql55-community                                  15 M
 mysql-community-libs                                        x86_64                                 5.5.52-2.el6                                    mysql55-community                                 1.7 M
     replacing  mysql-libs.x86_64 5.1.73-5.el6_7.1
 mysql-community-libs-compat                                 x86_64                                 5.5.52-2.el6                                    mysql55-community                                 1.6 M
     replacing  mysql-libs.x86_64 5.1.73-5.el6_7.1
Installing for dependencies:
 mysql-community-common                                      x86_64                                 5.5.52-2.el6                                    mysql55-community                                 277 k

Transaction Summary
============================================================================================================================================================================================================
Install       4 Package(s)

Total download size: 18 M
Is this ok [y/N]: y
Downloading Packages:
(1/4): mysql-community-client-5.5.52-2.el6.x86_64.rpm                                                                                                                                |  15 MB     00:00     
(2/4): mysql-community-common-5.5.52-2.el6.x86_64.rpm                                                                                                                                | 277 kB     00:00     
(3/4): mysql-community-libs-5.5.52-2.el6.x86_64.rpm                                                                                                                                  | 1.7 MB     00:00     
(4/4): mysql-community-libs-compat-5.5.52-2.el6.x86_64.rpm                                                                                                                           | 1.6 MB     00:00     
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                                                                                        38 MB/s |  18 MB     00:00     
warning: rpmts_HdrFromFdno: Header V3 DSA/SHA1 Signature, key ID 5072e1f5: NOKEY
Retrieving key from file:///etc/pki/rpm-gpg/RPM-GPG-KEY-mysql
Importing GPG key 0x5072E1F5:
 Userid : MySQL Release Engineering <mysql-build@oss.oracle.com>
 Package: mysql57-community-release-el6-9.noarch (installed)
 From   : /etc/pki/rpm-gpg/RPM-GPG-KEY-mysql
Is this ok [y/N]: y
Running rpm_check_debug
Running Transaction Test
Transaction Test Succeeded
Running Transaction
Warning: RPMDB altered outside of yum.
  Installing : mysql-community-common-5.5.52-2.el6.x86_64                                                                                                                                               1/5 
  Installing : mysql-community-libs-5.5.52-2.el6.x86_64                                                                                                                                                 2/5 
  Installing : mysql-community-client-5.5.52-2.el6.x86_64                                                                                                                                               3/5 
  Installing : mysql-community-libs-compat-5.5.52-2.el6.x86_64                                                                                                                                          4/5 
  Erasing    : mysql-libs-5.1.73-5.el6_7.1.x86_64                                                                                                                                                       5/5 
  Verifying  : mysql-community-client-5.5.52-2.el6.x86_64                                                                                                                                               1/5 
  Verifying  : mysql-community-libs-compat-5.5.52-2.el6.x86_64                                                                                                                                          2/5 
  Verifying  : mysql-community-common-5.5.52-2.el6.x86_64                                                                                                                                               3/5 
  Verifying  : mysql-community-libs-5.5.52-2.el6.x86_64                                                                                                                                                 4/5 
  Verifying  : mysql-libs-5.1.73-5.el6_7.1.x86_64                                                                                                                                                       5/5 

Installed:
  mysql-community-client.x86_64 0:5.5.52-2.el6                      mysql-community-libs.x86_64 0:5.5.52-2.el6                      mysql-community-libs-compat.x86_64 0:5.5.52-2.el6                     

Dependency Installed:
  mysql-community-common.x86_64 0:5.5.52-2.el6                                                                                                                                                              

Replaced:
  mysql-libs.x86_64 0:5.1.73-5.el6_7.1                                                                                                                                                                      

Complete!
```
* Download and copy the JDBC connector to all nodes, in my opinion, there is no application that would use the connector right now. Lets wait until we need to start app which needs this. CM/Agent

### Enabling replication
* Edit `/etc/my.cnf` on master (klempa1)
```
[mysqld]
#
# Remove leading # and set to the amount of RAM for the most important data
# cache in MySQL. Start at 70% of total RAM for dedicated server, else 10%.
# innodb_buffer_pool_size = 128M
#
# Remove leading # to turn on a very important data integrity option: logging
# changes to the binary log between backups.
log-bin=mysql-bin
server-id=1
innodb_flush_log_at_trx_commit=1
sync_binlog=1
```
* edit `/etc/my.cnf` on replica: (klempa2)
```
[mysqld]
#
# Remove leading # and set to the amount of RAM for the most important data
# cache in MySQL. Start at 70% of total RAM for dedicated server, else 10%.
# innodb_buffer_pool_size = 128M
#
# Remove leading # to turn on a very important data integrity option: logging
# changes to the binary log between backups.
server-id=2
```
* on master (klempa1) start mysql server:
```
sudo service mysqld start
```
* check the server log if it started ok:
```
sudo less /var/log/mysqld.log
```
* secure the installation (shown output from klempa2, same steps are done for master and slave)
```
[ec2-user@klempa2 ~]$ sudo /usr/bin/mysql_secure_installation 




NOTE: RUNNING ALL PARTS OF THIS SCRIPT IS RECOMMENDED FOR ALL MySQL
      SERVERS IN PRODUCTION USE!  PLEASE READ EACH STEP CAREFULLY!


In order to log into MySQL to secure it, we'll need the current
password for the root user.  If you've just installed MySQL, and
you haven't set the root password yet, the password will be blank,
so you should just press enter here.

Enter current password for root (enter for none): 
OK, successfully used password, moving on...

Setting the root password ensures that nobody can log into the MySQL
root user without the proper authorisation.

Set root password? [Y/n] y
New password: 
Re-enter new password: 
Password updated successfully!
Reloading privilege tables..
 ... Success!


By default, a MySQL installation has an anonymous user, allowing anyone
to log into MySQL without having to have a user account created for
them.  This is intended only for testing, and to make the installation
go a bit smoother.  You should remove them before moving into a
production environment.

Remove anonymous users? [Y/n] y
 ... Success!

Normally, root should only be allowed to connect from 'localhost'.  This
ensures that someone cannot guess at the root password from the network.

Disallow root login remotely? [Y/n] n
 ... skipping.

By default, MySQL comes with a database named 'test' that anyone can
access.  This is also intended only for testing, and should be removed
before moving into a production environment.

Remove test database and access to it? [Y/n] y
 - Dropping test database...
 ... Success!
 - Removing privileges on test database...
 ... Success!

Reloading the privilege tables will ensure that all changes made so far
will take effect immediately.

Reload privilege tables now? [Y/n] y
 ... Success!

Cleaning up...



All done!  If you've completed all of the above steps, your MySQL
installation should now be secure.

Thanks for using MySQL!

```
* on master (klempa1) create user for replication and grant him replication privilege:
```
[ec2-user@klempa1 ~]$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 9
Server version: 5.5.52-log MySQL Community Server (GPL)

Copyright (c) 2000, 2016, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> GRANT REPLICATION SLAVE ON *.* TO 'replica'@'klempa2.cdh.seb' IDENTIFIED BY 'BLkeLF2MD7zm';
Query OK, 0 rows affected (0.00 sec)

mysql> SET GLOBAL binlog_format = 'ROW';
Query OK, 0 rows affected (0.00 sec)

mysql>  FLUSH TABLES WITH READ LOCK;
Query OK, 0 rows affected (0.00 sec)

mysql> FLUSH PRIVILEGES;
Query OK, 0 rows affected (0.01 sec)
```
* on master (klempa1) take the note of position
```
[ec2-user@klempa1 ~]$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 10
Server version: 5.5.52-log MySQL Community Server (GPL)

Copyright (c) 2000, 2016, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> SHOW MASTER STATUS;
+------------------+----------+--------------+------------------+
| File             | Position | Binlog_Do_DB | Binlog_Ignore_DB |
+------------------+----------+--------------+------------------+
| mysql-bin.000003 |     1378 |              |                  |
+------------------+----------+--------------+------------------+
1 row in set (0.00 sec)
```
* on slave (klempa2) enable replication
```
[ec2-user@klempa2 ~]$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 9
Server version: 5.5.52 MySQL Community Server (GPL)

Copyright (c) 2000, 2016, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> CHANGE MASTER TO MASTER_HOST='klempa1.cdh.seb', MASTER_USER='replica', MASTER_PASSWORD='BLkeLF2MD7zm', MASTER_LOG_FILE='mysql-bin.000003', MASTER_LOG_POS=1378;
Query OK, 0 rows affected (0.01 sec)

mysql> START SLAVE;
Query OK, 0 rows affected (0.00 sec)

mysql> SHOW SLAVE STATUS \G
*************************** 1. row ***************************
               Slave_IO_State: Waiting for master to send event
                  Master_Host: klempa1.cdh.seb
                  Master_User: replica
                  Master_Port: 3306
                Connect_Retry: 60
              Master_Log_File: mysql-bin.000003
          Read_Master_Log_Pos: 1378
               Relay_Log_File: mysqld-relay-bin.000002
                Relay_Log_Pos: 253
        Relay_Master_Log_File: mysql-bin.000003
             Slave_IO_Running: Yes
            Slave_SQL_Running: Yes
              Replicate_Do_DB: 
          Replicate_Ignore_DB: 
           Replicate_Do_Table: 
       Replicate_Ignore_Table: 
      Replicate_Wild_Do_Table: 
  Replicate_Wild_Ignore_Table: 
                   Last_Errno: 0
                   Last_Error: 
                 Skip_Counter: 0
          Exec_Master_Log_Pos: 1378
              Relay_Log_Space: 410
              Until_Condition: None
               Until_Log_File: 
                Until_Log_Pos: 0
           Master_SSL_Allowed: No
           Master_SSL_CA_File: 
           Master_SSL_CA_Path: 
              Master_SSL_Cert: 
            Master_SSL_Cipher: 
               Master_SSL_Key: 
        Seconds_Behind_Master: 0
Master_SSL_Verify_Server_Cert: No
                Last_IO_Errno: 0
                Last_IO_Error: 
               Last_SQL_Errno: 0
               Last_SQL_Error: 
  Replicate_Ignore_Server_Ids: 
             Master_Server_Id: 1
1 row in set (0.00 sec)

```

* startup
```
sudo /sbin/chkconfig mysqld on
```