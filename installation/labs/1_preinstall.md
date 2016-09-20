* Add repo for cloudera manager
```
sudo vim /etc/yum.repos.d/cloudera-manager.repo
```
should contain:
```
[cloudera-manager]
# Packages for Cloudera Manager, Version 5, on RedHat or CentOS 6 x86_64           	  
name=Cloudera Manager
baseurl=https://archive.cloudera.com/cm5/redhat/6/x86_64/cm/5/
gpgkey =https://archive.cloudera.com/cm5/redhat/6/x86_64/cm/RPM-GPG-KEY-cloudera    
gpgcheck = 1
```
* install java on CM host
java
```
sudo yum install oracle-j2sdk1.7
```
* install cloudera manager
```
sudo yum install cloudera-manager-daemons cloudera-manager-server
```
* create database in mysql for manager
database for manager
```
 sudo /usr/share/cmf/schema/scm_prepare_database.sh mysql -u root -p cloudera_manager cloudera_manager u
```
* distribute connector/j
```
sudo mkdir /usr/share/java
sudo cp mysql-connector-java-5.1.39/mysql-connector-java-5.1.39-bin.jar /usr/share/java/mysql-connector-java.jar
```
* connect to klempa1:7180, run install wizard using parcels
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