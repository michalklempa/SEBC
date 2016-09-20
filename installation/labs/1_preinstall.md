* Add repo for cloudera manager
```
sudo vim /etc/yum.repos.d/cloudera-manager.repo
```
contains:
```
[cloudera-manager]
# Packages for Cloudera Manager, Version 5, on RedHat or CentOS 6 x86_64           	  
name=Cloudera Manager
baseurl=https://archive.cloudera.com/cm5/redhat/6/x86_64/cm/5/
gpgkey =https://archive.cloudera.com/cm5/redhat/6/x86_64/cm/RPM-GPG-KEY-cloudera    
gpgcheck = 1
```

java
```
sudo yum install oracle-j2sdk1.7
```

manager
```
sudo yum install cloudera-manager-daemons cloudera-manager-server
```

database for manager
```
/usr/share/cmf/schema/scm_prepare_database.sh
```

```
sudo mkdir /usr/share/java
sudo cp mysql-connector-java-5.1.39/mysql-connector-java-5.1.39-bin.jar /usr/share/java/mysql-connector-java.jar
```


```
 sudo /usr/share/cmf/schema/scm_prepare_database.sh mysql -u root -p cloudera_manager cloudera_manager u
```
* We have got cluster installed and users ready, change ulimit
```
echo hdfs - nofile 32768 >> /etc/security/limits.conf
echo mapred - nofile 32768 >> /etc/security/limits.conf
echo hbase - nofile 32768 >> /etc/security/limits.conf
echo hdfs - nproc 32768 >> /etc/security/limits.conf
echo mapred - nproc 32768 >> /etc/security/limits.conf
echo hbase - nproc 32768 >> /etc/security/limits.conf
```
* Recheck the limits
```
[root@klempa1 ec2-user]# echo hbase - nproc 32768 >> /etc/security/limits.conf
[root@klempa1 ec2-user]# su - hdfs
[hdfs@klempa1 ~]$ ulimit -Hn
32768
[hdfs@klempa1 ~]$ ulimit -a | grep processes
max user processes              (-u) 32768
```