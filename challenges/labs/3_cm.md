* grants
```
mysql> SHOW GRANTS FOR rman;
+-----------------------------------------------------------------------------------------------------+
| Grants for rman@%                                                                                   |
+-----------------------------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'rman'@'%' IDENTIFIED BY PASSWORD '*819397F8B454D58DA4E9F42A88A4873756B8C96D' |
| GRANT ALL PRIVILEGES ON `rman`.* TO 'rman'@'%'                                                      |
+-----------------------------------------------------------------------------------------------------+
2 rows in set (0.00 sec)

mysql> SHOW GRANTS FOR hive;
+-----------------------------------------------------------------------------------------------------+
| Grants for hive@%                                                                                   |
+-----------------------------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'hive'@'%' IDENTIFIED BY PASSWORD '*4DF1D66463C18D44E3B001A8FB1BBFBEA13E27FC' |
| GRANT ALL PRIVILEGES ON `hive`.* TO 'hive'@'%'                                                      |
+-----------------------------------------------------------------------------------------------------+
2 rows in set (0.00 sec)

mysql> SHOW GRANTS FOR oozie;
+------------------------------------------------------------------------------------------------------+
| Grants for oozie@%                                                                                   |
+------------------------------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'oozie'@'%' IDENTIFIED BY PASSWORD '*2B03FE0359FAD3B80620490CE614F8622E0828CD' |
| GRANT ALL PRIVILEGES ON `oozie`.* TO 'oozie'@'%'                                                     |
+------------------------------------------------------------------------------------------------------+
2 rows in set (0.00 sec)
```
* hdfs
```
[hdfs@klempa8 ~]$ hdfs dfs -ls /user
Found 6 items
drwxr-xr-x   - hdfs   supergroup          0 2016-09-23 11:55 /user/christie
drwxrwxrwx   - mapred hadoop              0 2016-09-23 11:52 /user/history
drwxrwxr-t   - hive   hive                0 2016-09-23 11:53 /user/hive
drwxrwxr-x   - hue    hue                 0 2016-09-23 11:53 /user/hue
drwxrwxr-x   - oozie  oozie               0 2016-09-23 11:53 /user/oozie
drwxr-xr-x   - hdfs   supergroup          0 2016-09-23 11:55 /user/weiner
```
* classpath
```
[root@klempa8 ec2-user]# hadoop classpath
/etc/hadoop/conf:/opt/cloudera/parcels/CDH-5.7.3-1.cdh5.7.3.p0.5/lib/hadoop/libexec/../../hadoop/lib/*:/opt/cloudera/parcels/CDH-5.7.3-1.cdh5.7.3.p0.5/lib/hadoop/libexec/../../hadoop/.//*:/opt/cloudera/parcels/CDH-5.7.3-1.cdh5.7.3.p0.5/lib/hadoop/libexec/../../hadoop-hdfs/./:/opt/cloudera/parcels/CDH-5.7.3-1.cdh5.7.3.p0.5/lib/hadoop/libexec/../../hadoop-hdfs/lib/*:/opt/cloudera/parcels/CDH-5.7.3-1.cdh5.7.3.p0.5/lib/hadoop/libexec/../../hadoop-hdfs/.//*:/opt/cloudera/parcels/CDH-5.7.3-1.cdh5.7.3.p0.5/lib/hadoop/libexec/../../hadoop-yarn/lib/*:/opt/cloudera/parcels/CDH-5.7.3-1.cdh5.7.3.p0.5/lib/hadoop/libexec/../../hadoop-yarn/.//*:/opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/lib/*:/opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/.//*
```
* api only first item from json array as requested
```
{
    "hostId" : "i-6180cf99",
    "ipAddress" : "172.31.5.1",
    "hostname" : "klempa1.cha.seb",
    "rackId" : "/default",
    "hostUrl" : "http://klempa2.cha.seb:7180/cmf/hostRedirect/i-6180cf99",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15664750592
  }
```
