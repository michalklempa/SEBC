
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