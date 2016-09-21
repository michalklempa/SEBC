* install httpd
```
sudo yum install httpd
```
* enable and start
```
chkonfig httpd on
service httpd start
```
* add blank page to avoid default
```
echo > /var/www/html/index.html
```
* download packages, see the listing of created files
```
[root@klempa1 html]# ls -R
.:
accumulo  accumulo-c5  cdh5  impala  index.html  kafka  navigator-keytrustee5  search  spark  sqoop-connectors

./accumulo:
parcels

./accumulo/parcels:
1.4

./accumulo/parcels/1.4:
ACCUMULO-1.4.4-1.cdh4.5.0.p0.65-el6.parcel  ACCUMULO-1.4.4-1.cdh4.5.0.p0.65-el6.parcel.sha1  manifest.json

./accumulo-c5:
parcels

./accumulo-c5/parcels:
1.6.0.116  latest

./accumulo-c5/parcels/1.6.0.116:
ACCUMULO-1.6.0-1.cdh5.1.4.p0.116-el6.parcel  manifest.json

./cdh5:
parcels

./cdh5/parcels:
5.8.0.42  latest

./cdh5/parcels/5.8.0.42:
CDH-5.8.0-1.cdh5.8.0.p0.42-el5.parcel.sha1  CDH-5.8.0-1.cdh5.8.0.p0.42-el6.parcel  manifest.json

./impala:
parcels

./impala/parcels:
2.1.0.1995  latest

./impala/parcels/2.1.0.1995:
IMPALA-2.1.0-1.impala2.0.0.p0.1995-el6.parcel  manifest.json

./kafka:
parcels

./kafka/parcels:
2.0.2.5  latest

./kafka/parcels/2.0.2.5:
KAFKA-2.0.2-1.2.0.2.p0.5-el6.parcel  KAFKA-2.0.2-1.2.0.2.p0.5-el6.parcel.sha1  manifest.json

./navigator-keytrustee5:
parcels

./navigator-keytrustee5/parcels:
5.8.0.21  latest

./navigator-keytrustee5/parcels/5.8.0.21:
KEYTRUSTEE-5.8.0-5.KEYTRUSTEE5.8.0.p0.21-el6.parcel  KEYTRUSTEE-5.8.0-5.KEYTRUSTEE5.8.0.p0.21-el6.parcel.sha1  manifest.json

./search:
parcels

./search/parcels:
1.3.0.9  latest

./search/parcels/1.3.0.9:
manifest.json  SOLR-1.3.0-1.cdh4.5.0.p0.9-el6.parcel  SOLR-1.3.0-1.cdh4.5.0.p0.9-el6.parcel.sha1

./spark:
parcels

./spark/parcels:
0.9.0.98  latest

./spark/parcels/0.9.0.98:
manifest.json  SPARK-0.9.0-1.cdh4.6.0.p0.98-el6.parcel  SPARK-0.9.0-1.cdh4.6.0.p0.98-el6.parcel.sha1

./sqoop-connectors:
parcels

./sqoop-connectors/parcels:
1.5.9  latest

./sqoop-connectors/parcels/1.5.9:
manifest.json  SQOOP_NETEZZA_CONNECTOR-1.3c5-el6.parcel  SQOOP_NETEZZA_CONNECTOR-1.3c5-el6.parcel.sha1  SQOOP_TERADATA_CONNECTOR-1.5c5-el6.parcel  SQOOP_TERADATA_CONNECTOR-1.5c5-el6.parcel.sha1
```
* set the CM, see the screen shot
* test by downloading, see downloaded2.png and also one can oversee output of
```
tcpdump -i lo -vv port 80
```
to be sure downloading happens from localhost.