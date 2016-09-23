```
[root@klempa2 ~]# ls /etc/yum/repos.d
ls: cannot access /etc/yum/repos.d: No such file or directory
[root@klempa2 ~]# ls /etc/yum.repos.d
cloudera-manager.repo  mysql-community.repo  mysql-community-source.repo  redhat.repo  redhat-rhui-client-config.repo  redhat-rhui.repo  rhel-source.repo  rhui-load-balancers.conf
```

* According to my grants, CM database creation script already does the job of creating user `scm` to be able to access DB only from CM host (`klempa2.cha.seb`)/. See the listing below:
```
mysql> select * from information_schema.user_privileges;
+--------------------------+---------------+-------------------------+--------------+
| GRANTEE                  | TABLE_CATALOG | PRIVILEGE_TYPE          | IS_GRANTABLE |
+--------------------------+---------------+-------------------------+--------------+
| 'root'@'localhost'       | def           | SELECT                  | YES          |
| 'root'@'localhost'       | def           | INSERT                  | YES          |
| 'root'@'localhost'       | def           | UPDATE                  | YES          |
| 'root'@'localhost'       | def           | DELETE                  | YES          |
| 'root'@'localhost'       | def           | CREATE                  | YES          |
| 'root'@'localhost'       | def           | DROP                    | YES          |
| 'root'@'localhost'       | def           | RELOAD                  | YES          |
| 'root'@'localhost'       | def           | SHUTDOWN                | YES          |
| 'root'@'localhost'       | def           | PROCESS                 | YES          |
| 'root'@'localhost'       | def           | FILE                    | YES          |
| 'root'@'localhost'       | def           | REFERENCES              | YES          |
| 'root'@'localhost'       | def           | INDEX                   | YES          |
| 'root'@'localhost'       | def           | ALTER                   | YES          |
| 'root'@'localhost'       | def           | SHOW DATABASES          | YES          |
| 'root'@'localhost'       | def           | SUPER                   | YES          |
| 'root'@'localhost'       | def           | CREATE TEMPORARY TABLES | YES          |
| 'root'@'localhost'       | def           | LOCK TABLES             | YES          |
| 'root'@'localhost'       | def           | EXECUTE                 | YES          |
| 'root'@'localhost'       | def           | REPLICATION SLAVE       | YES          |
| 'root'@'localhost'       | def           | REPLICATION CLIENT      | YES          |
| 'root'@'localhost'       | def           | CREATE VIEW             | YES          |
| 'root'@'localhost'       | def           | SHOW VIEW               | YES          |
| 'root'@'localhost'       | def           | CREATE ROUTINE          | YES          |
| 'root'@'localhost'       | def           | ALTER ROUTINE           | YES          |
| 'root'@'localhost'       | def           | CREATE USER             | YES          |
| 'root'@'localhost'       | def           | EVENT                   | YES          |
| 'root'@'localhost'       | def           | TRIGGER                 | YES          |
| 'root'@'localhost'       | def           | CREATE TABLESPACE       | YES          |
| 'root'@'klempa1.cha.seb' | def           | SELECT                  | YES          |
| 'root'@'klempa1.cha.seb' | def           | INSERT                  | YES          |
| 'root'@'klempa1.cha.seb' | def           | UPDATE                  | YES          |
| 'root'@'klempa1.cha.seb' | def           | DELETE                  | YES          |
| 'root'@'klempa1.cha.seb' | def           | CREATE                  | YES          |
| 'root'@'klempa1.cha.seb' | def           | DROP                    | YES          |
| 'root'@'klempa1.cha.seb' | def           | RELOAD                  | YES          |
| 'root'@'klempa1.cha.seb' | def           | SHUTDOWN                | YES          |
| 'root'@'klempa1.cha.seb' | def           | PROCESS                 | YES          |
| 'root'@'klempa1.cha.seb' | def           | FILE                    | YES          |
| 'root'@'klempa1.cha.seb' | def           | REFERENCES              | YES          |
| 'root'@'klempa1.cha.seb' | def           | INDEX                   | YES          |
| 'root'@'klempa1.cha.seb' | def           | ALTER                   | YES          |
| 'root'@'klempa1.cha.seb' | def           | SHOW DATABASES          | YES          |
| 'root'@'klempa1.cha.seb' | def           | SUPER                   | YES          |
| 'root'@'klempa1.cha.seb' | def           | CREATE TEMPORARY TABLES | YES          |
| 'root'@'klempa1.cha.seb' | def           | LOCK TABLES             | YES          |
| 'root'@'klempa1.cha.seb' | def           | EXECUTE                 | YES          |
| 'root'@'klempa1.cha.seb' | def           | REPLICATION SLAVE       | YES          |
| 'root'@'klempa1.cha.seb' | def           | REPLICATION CLIENT      | YES          |
| 'root'@'klempa1.cha.seb' | def           | CREATE VIEW             | YES          |
| 'root'@'klempa1.cha.seb' | def           | SHOW VIEW               | YES          |
| 'root'@'klempa1.cha.seb' | def           | CREATE ROUTINE          | YES          |
| 'root'@'klempa1.cha.seb' | def           | ALTER ROUTINE           | YES          |
| 'root'@'klempa1.cha.seb' | def           | CREATE USER             | YES          |
| 'root'@'klempa1.cha.seb' | def           | EVENT                   | YES          |
| 'root'@'klempa1.cha.seb' | def           | TRIGGER                 | YES          |
| 'root'@'klempa1.cha.seb' | def           | CREATE TABLESPACE       | YES          |
| 'root'@'127.0.0.1'       | def           | SELECT                  | YES          |
| 'root'@'127.0.0.1'       | def           | INSERT                  | YES          |
| 'root'@'127.0.0.1'       | def           | UPDATE                  | YES          |
| 'root'@'127.0.0.1'       | def           | DELETE                  | YES          |
| 'root'@'127.0.0.1'       | def           | CREATE                  | YES          |
| 'root'@'127.0.0.1'       | def           | DROP                    | YES          |
| 'root'@'127.0.0.1'       | def           | RELOAD                  | YES          |
| 'root'@'127.0.0.1'       | def           | SHUTDOWN                | YES          |
| 'root'@'127.0.0.1'       | def           | PROCESS                 | YES          |
| 'root'@'127.0.0.1'       | def           | FILE                    | YES          |
| 'root'@'127.0.0.1'       | def           | REFERENCES              | YES          |
| 'root'@'127.0.0.1'       | def           | INDEX                   | YES          |
| 'root'@'127.0.0.1'       | def           | ALTER                   | YES          |
| 'root'@'127.0.0.1'       | def           | SHOW DATABASES          | YES          |
| 'root'@'127.0.0.1'       | def           | SUPER                   | YES          |
| 'root'@'127.0.0.1'       | def           | CREATE TEMPORARY TABLES | YES          |
| 'root'@'127.0.0.1'       | def           | LOCK TABLES             | YES          |
| 'root'@'127.0.0.1'       | def           | EXECUTE                 | YES          |
| 'root'@'127.0.0.1'       | def           | REPLICATION SLAVE       | YES          |
| 'root'@'127.0.0.1'       | def           | REPLICATION CLIENT      | YES          |
| 'root'@'127.0.0.1'       | def           | CREATE VIEW             | YES          |
| 'root'@'127.0.0.1'       | def           | SHOW VIEW               | YES          |
| 'root'@'127.0.0.1'       | def           | CREATE ROUTINE          | YES          |
| 'root'@'127.0.0.1'       | def           | ALTER ROUTINE           | YES          |
| 'root'@'127.0.0.1'       | def           | CREATE USER             | YES          |
| 'root'@'127.0.0.1'       | def           | EVENT                   | YES          |
| 'root'@'127.0.0.1'       | def           | TRIGGER                 | YES          |
| 'root'@'127.0.0.1'       | def           | CREATE TABLESPACE       | YES          |
| 'root'@'::1'             | def           | SELECT                  | YES          |
| 'root'@'::1'             | def           | INSERT                  | YES          |
| 'root'@'::1'             | def           | UPDATE                  | YES          |
| 'root'@'::1'             | def           | DELETE                  | YES          |
| 'root'@'::1'             | def           | CREATE                  | YES          |
| 'root'@'::1'             | def           | DROP                    | YES          |
| 'root'@'::1'             | def           | RELOAD                  | YES          |
| 'root'@'::1'             | def           | SHUTDOWN                | YES          |
| 'root'@'::1'             | def           | PROCESS                 | YES          |
| 'root'@'::1'             | def           | FILE                    | YES          |
| 'root'@'::1'             | def           | REFERENCES              | YES          |
| 'root'@'::1'             | def           | INDEX                   | YES          |
| 'root'@'::1'             | def           | ALTER                   | YES          |
| 'root'@'::1'             | def           | SHOW DATABASES          | YES          |
| 'root'@'::1'             | def           | SUPER                   | YES          |
| 'root'@'::1'             | def           | CREATE TEMPORARY TABLES | YES          |
| 'root'@'::1'             | def           | LOCK TABLES             | YES          |
| 'root'@'::1'             | def           | EXECUTE                 | YES          |
| 'root'@'::1'             | def           | REPLICATION SLAVE       | YES          |
| 'root'@'::1'             | def           | REPLICATION CLIENT      | YES          |
| 'root'@'::1'             | def           | CREATE VIEW             | YES          |
| 'root'@'::1'             | def           | SHOW VIEW               | YES          |
| 'root'@'::1'             | def           | CREATE ROUTINE          | YES          |
| 'root'@'::1'             | def           | ALTER ROUTINE           | YES          |
| 'root'@'::1'             | def           | CREATE USER             | YES          |
| 'root'@'::1'             | def           | EVENT                   | YES          |
| 'root'@'::1'             | def           | TRIGGER                 | YES          |
| 'root'@'::1'             | def           | CREATE TABLESPACE       | YES          |
| 'scm'@'klempa2.cha.seb'  | def           | USAGE                   | NO           |
| ''@'localhost'           | def           | USAGE                   | NO           |
| ''@'klempa1.cha.seb'     | def           | USAGE                   | NO           |
| 'root'@'%'               | def           | SELECT                  | NO           |
| 'root'@'%'               | def           | INSERT                  | NO           |
| 'root'@'%'               | def           | UPDATE                  | NO           |
| 'root'@'%'               | def           | DELETE                  | NO           |
| 'root'@'%'               | def           | CREATE                  | NO           |
| 'root'@'%'               | def           | DROP                    | NO           |
| 'root'@'%'               | def           | RELOAD                  | NO           |
| 'root'@'%'               | def           | SHUTDOWN                | NO           |
| 'root'@'%'               | def           | PROCESS                 | NO           |
| 'root'@'%'               | def           | FILE                    | NO           |
| 'root'@'%'               | def           | REFERENCES              | NO           |
| 'root'@'%'               | def           | INDEX                   | NO           |
| 'root'@'%'               | def           | ALTER                   | NO           |
| 'root'@'%'               | def           | SHOW DATABASES          | NO           |
| 'root'@'%'               | def           | SUPER                   | NO           |
| 'root'@'%'               | def           | CREATE TEMPORARY TABLES | NO           |
| 'root'@'%'               | def           | LOCK TABLES             | NO           |
| 'root'@'%'               | def           | EXECUTE                 | NO           |
| 'root'@'%'               | def           | REPLICATION SLAVE       | NO           |
| 'root'@'%'               | def           | REPLICATION CLIENT      | NO           |
| 'root'@'%'               | def           | CREATE VIEW             | NO           |
| 'root'@'%'               | def           | SHOW VIEW               | NO           |
| 'root'@'%'               | def           | CREATE ROUTINE          | NO           |
| 'root'@'%'               | def           | ALTER ROUTINE           | NO           |
| 'root'@'%'               | def           | CREATE USER             | NO           |
| 'root'@'%'               | def           | EVENT                   | NO           |
| 'root'@'%'               | def           | TRIGGER                 | NO           |
| 'root'@'%'               | def           | CREATE TABLESPACE       | NO           |
| 'michalklempa'@'%'       | def           | SELECT                  | YES          |
| 'michalklempa'@'%'       | def           | INSERT                  | YES          |
| 'michalklempa'@'%'       | def           | UPDATE                  | YES          |
| 'michalklempa'@'%'       | def           | DELETE                  | YES          |
| 'michalklempa'@'%'       | def           | CREATE                  | YES          |
| 'michalklempa'@'%'       | def           | DROP                    | YES          |
| 'michalklempa'@'%'       | def           | RELOAD                  | YES          |
| 'michalklempa'@'%'       | def           | SHUTDOWN                | YES          |
| 'michalklempa'@'%'       | def           | PROCESS                 | YES          |
| 'michalklempa'@'%'       | def           | FILE                    | YES          |
| 'michalklempa'@'%'       | def           | REFERENCES              | YES          |
| 'michalklempa'@'%'       | def           | INDEX                   | YES          |
| 'michalklempa'@'%'       | def           | ALTER                   | YES          |
| 'michalklempa'@'%'       | def           | SHOW DATABASES          | YES          |
| 'michalklempa'@'%'       | def           | SUPER                   | YES          |
| 'michalklempa'@'%'       | def           | CREATE TEMPORARY TABLES | YES          |
| 'michalklempa'@'%'       | def           | LOCK TABLES             | YES          |
| 'michalklempa'@'%'       | def           | EXECUTE                 | YES          |
| 'michalklempa'@'%'       | def           | REPLICATION SLAVE       | YES          |
| 'michalklempa'@'%'       | def           | REPLICATION CLIENT      | YES          |
| 'michalklempa'@'%'       | def           | CREATE VIEW             | YES          |
| 'michalklempa'@'%'       | def           | SHOW VIEW               | YES          |
| 'michalklempa'@'%'       | def           | CREATE ROUTINE          | YES          |
| 'michalklempa'@'%'       | def           | ALTER ROUTINE           | YES          |
| 'michalklempa'@'%'       | def           | CREATE USER             | YES          |
| 'michalklempa'@'%'       | def           | EVENT                   | YES          |
| 'michalklempa'@'%'       | def           | TRIGGER                 | YES          |
| 'michalklempa'@'%'       | def           | CREATE TABLESPACE       | YES          |
+--------------------------+---------------+-------------------------+--------------+
171 rows in set (0.00 sec)

```

* started CM, the head and output:
```
[root@klempa2 ~]# head -1 /var/log/cloudera-scm-server/cloudera-scm-server.log
2016-09-23 09:55:53,019 INFO main:com.cloudera.server.cmf.Main: Starting SCM Server. JVM Args: [-Dlog4j.configuration=file:/etc/cloudera-scm-server/log4j.properties, -Dfile.encoding=UTF-8, -Dcmf.root.logger=INFO,LOGFILE, -Dcmf.log.dir=/var/log/cloudera-scm-server, -Dcmf.log.file=cloudera-scm-server.log, -Dcmf.jetty.threshhold=WARN, -Dcmf.schema.dir=/usr/share/cmf/schema, -Djava.awt.headless=true, -Djava.net.preferIPv4Stack=true, -Dpython.home=/usr/share/cmf/python, -XX:+UseConcMarkSweepGC, -XX:+UseParNewGC, -XX:+HeapDumpOnOutOfMemoryError, -Xmx2G, -XX:MaxPermSize=256m, -XX:+HeapDumpOnOutOfMemoryError, -XX:HeapDumpPath=/tmp, -XX:OnOutOfMemoryError=kill -9 %p], Args: [], Version: 5.8.0 (#42 built by jenkins on 20160714-1246 git: d08ac14ff050a108864fab00205c12e0d4043132)
```
* grep jetty
```
[root@klempa2 ~]# grep "Started Jetty server" /var/log/cloudera-scm-server/cloudera-scm-server.log
2016-09-23 09:57:06,188 INFO WebServerImpl:com.cloudera.server.cmf.WebServerImpl: Started Jetty server.
```
