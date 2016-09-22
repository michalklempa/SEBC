* sentry test
```
[ec2-user@klempa5 ~]$ kinit george
Password for george@KLEMPA.CDH.SEB: 
[ec2-user@klempa5 ~]$ klist
Ticket cache: FILE:/tmp/krb5cc_500
Default principal: george@KLEMPA.CDH.SEB

Valid starting     Expires            Service principal
09/22/16 12:02:45  09/23/16 12:02:45  krbtgt/KLEMPA.CDH.SEB@KLEMPA.CDH.SEB
	renew until 09/29/16 12:02:45
[ec2-user@klempa5 ~]$ beeline
2016-09-22 12:02:56,376 WARN  [main] mapreduce.TableMapReduceUtil: The hbase-prefix-tree module jar containing PrefixTreeCodec is not present.  Continuing without it.
Beeline version 1.1.0-cdh5.8.0 by Apache Hive
beeline> !connect jdbc:hive2://klempa2.cdh.seb:10000/default;principal=hive/klempa2.cdh.seb@KLEMPA.CDH.SEB
scan complete in 2ms
Connecting to jdbc:hive2://klempa2.cdh.seb:10000/default;principal=hive/klempa2.cdh.seb@KLEMPA.CDH.SEB
Enter username for jdbc:hive2://klempa2.cdh.seb:10000/default;principal=hive/klempa2.cdh.seb@KLEMPA.CDH.SEB: george
Enter password for jdbc:hive2://klempa2.cdh.seb:10000/default;principal=hive/klempa2.cdh.seb@KLEMPA.CDH.SEB: ********
Connected to: Apache Hive (version 1.1.0-cdh5.8.0)
Driver: Hive JDBC (version 1.1.0-cdh5.8.0)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://klempa2.cdh.seb:10000/default> show tables;
INFO  : Compiling command(queryId=hive_20160922120303_11273209-4d50-4701-948d-2df261f915fa): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20160922120303_11273209-4d50-4701-948d-2df261f915fa); Time taken: 0.053 seconds
INFO  : Executing command(queryId=hive_20160922120303_11273209-4d50-4701-948d-2df261f915fa): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20160922120303_11273209-4d50-4701-948d-2df261f915fa); Time taken: 0.119 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0.282 seconds)
0: jdbc:hive2://klempa2.cdh.seb:10000/default> Closing: 0: jdbc:hive2://klempa2.cdh.seb:10000/default;principal=hive/klempa2.cdh.seb@KLEMPA.CDH.SEB
[ec2-user@klempa5 ~]$ kdestroy
[ec2-user@klempa5 ~]$ kinit ferdinand
Password for ferdinand@KLEMPA.CDH.SEB: 
[ec2-user@klempa5 ~]$ klist
Ticket cache: FILE:/tmp/krb5cc_500
Default principal: ferdinand@KLEMPA.CDH.SEB

Valid starting     Expires            Service principal
09/22/16 12:03:17  09/23/16 12:03:17  krbtgt/KLEMPA.CDH.SEB@KLEMPA.CDH.SEB
	renew until 09/29/16 12:03:17
[ec2-user@klempa5 ~]$ beeline
2016-09-22 12:03:28,122 WARN  [main] mapreduce.TableMapReduceUtil: The hbase-prefix-tree module jar containing PrefixTreeCodec is not present.  Continuing without it.
Beeline version 1.1.0-cdh5.8.0 by Apache Hive
beeline> !connect jdbc:hive2://klempa2.cdh.seb:10000/default;principal=hive/klempa2.cdh.seb@KLEMPA.CDH.SEB
scan complete in 2ms
Connecting to jdbc:hive2://klempa2.cdh.seb:10000/default;principal=hive/klempa2.cdh.seb@KLEMPA.CDH.SEB
Enter username for jdbc:hive2://klempa2.cdh.seb:10000/default;principal=hive/klempa2.cdh.seb@KLEMPA.CDH.SEB: ferdinand
Enter password for jdbc:hive2://klempa2.cdh.seb:10000/default;principal=hive/klempa2.cdh.seb@KLEMPA.CDH.SEB: ********
Connected to: Apache Hive (version 1.1.0-cdh5.8.0)
Driver: Hive JDBC (version 1.1.0-cdh5.8.0)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://klempa2.cdh.seb:10000/default> show tables;
INFO  : Compiling command(queryId=hive_20160922120303_9a122b67-54a4-4a4f-bfd0-829b438ee92d): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20160922120303_9a122b67-54a4-4a4f-bfd0-829b438ee92d); Time taken: 0.06 seconds
INFO  : Executing command(queryId=hive_20160922120303_9a122b67-54a4-4a4f-bfd0-829b438ee92d): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20160922120303_9a122b67-54a4-4a4f-bfd0-829b438ee92d); Time taken: 0.116 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| sample_07  |
+------------+--+
1 row selected (0.29 seconds)
0: jdbc:hive2://klempa2.cdh.seb:10000/default> Closing: 0: jdbc:hive2://klempa2.cdh.seb:10000/default;principal=hive/klempa2.cdh.seb@KLEMPA.CDH.SEB
[ec2-user@klempa5 ~]$ 
```
* sentry roles
```
0: jdbc:hive2://localhost:10000/default> SHOW ROLE GRANT GROUP inserters;
INFO  : Compiling command(queryId=hive_20160922115757_c345ff1f-e795-485f-abc0-c5dcc8413c08): SHOW ROLE GRANT GROUP inserters
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:role, type:string, comment:from deserializer), FieldSchema(name:grant_option, type:boolean, comment:from deserializer), FieldSchema(name:grant_time, type:bigint, comment:from deserializer), FieldSchema(name:grantor, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20160922115757_c345ff1f-e795-485f-abc0-c5dcc8413c08); Time taken: 0.056 seconds
INFO  : Executing command(queryId=hive_20160922115757_c345ff1f-e795-485f-abc0-c5dcc8413c08): SHOW ROLE GRANT GROUP inserters
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20160922115757_c345ff1f-e795-485f-abc0-c5dcc8413c08); Time taken: 0.024 seconds
INFO  : OK
+-------------+---------------+-------------+----------+--+
|    role     | grant_option  | grant_time  | grantor  |
+-------------+---------------+-------------+----------+--+
| write_auth  | false         | NULL        | --       |
+-------------+---------------+-------------+----------+--+
1 row selected (0.092 seconds)
0: jdbc:hive2://localhost:10000/default> SHOW ROLE GRANT GROUP selector;
INFO  : Compiling command(queryId=hive_20160922115757_7101b0c1-adec-4eb5-94bd-1eb49dab61e1): SHOW ROLE GRANT GROUP selector
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:role, type:string, comment:from deserializer), FieldSchema(name:grant_option, type:boolean, comment:from deserializer), FieldSchema(name:grant_time, type:bigint, comment:from deserializer), FieldSchema(name:grantor, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20160922115757_7101b0c1-adec-4eb5-94bd-1eb49dab61e1); Time taken: 0.058 seconds
INFO  : Executing command(queryId=hive_20160922115757_7101b0c1-adec-4eb5-94bd-1eb49dab61e1): SHOW ROLE GRANT GROUP selector
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20160922115757_7101b0c1-adec-4eb5-94bd-1eb49dab61e1); Time taken: 0.03 seconds
INFO  : OK
+------------+---------------+-------------+----------+--+
|    role    | grant_option  | grant_time  | grantor  |
+------------+---------------+-------------+----------+--+
| read_auth  | false         | NULL        | --       |
+------------+---------------+-------------+----------+--+
1 row selected (0.101 seconds)
0: jdbc:hive2://localhost:10000/default> SHOW GRANT ROLE write_auth
. . . . . . . . . . . . . . . . . . . .> ;
INFO  : Compiling command(queryId=hive_20160922115757_d98a8305-9728-4404-9081-fc44dad29292): SHOW GRANT ROLE write_auth
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:database, type:string, comment:from deserializer), FieldSchema(name:table, type:string, comment:from deserializer), FieldSchema(name:partition, type:string, comment:from deserializer), FieldSchema(name:column, type:string, comment:from deserializer), FieldSchema(name:principal_name, type:string, comment:from deserializer), FieldSchema(name:principal_type, type:string, comment:from deserializer), FieldSchema(name:privilege, type:string, comment:from deserializer), FieldSchema(name:grant_option, type:boolean, comment:from deserializer), FieldSchema(name:grant_time, type:bigint, comment:from deserializer), FieldSchema(name:grantor, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20160922115757_d98a8305-9728-4404-9081-fc44dad29292); Time taken: 0.059 seconds
INFO  : Executing command(queryId=hive_20160922115757_d98a8305-9728-4404-9081-fc44dad29292): SHOW GRANT ROLE write_auth
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20160922115757_d98a8305-9728-4404-9081-fc44dad29292); Time taken: 0.047 seconds
INFO  : OK
+-----------+------------+------------+---------+-----------------+-----------------+------------+---------------+-------------------+----------+--+
| database  |   table    | partition  | column  | principal_name  | principal_type  | privilege  | grant_option  |    grant_time     | grantor  |
+-----------+------------+------------+---------+-----------------+-----------------+------------+---------------+-------------------+----------+--+
| default   | sample_07  |            |         | write_auth      | ROLE            | select     | false         | 1474559034756000  | --       |
+-----------+------------+------------+---------+-----------------+-----------------+------------+---------------+-------------------+----------+--+
1 row selected (0.12 seconds)
0: jdbc:hive2://localhost:10000/default> SHOW GRANT ROLE read_auth;
INFO  : Compiling command(queryId=hive_20160922115858_10f3ffe0-4409-401a-b712-6271baafa16e): SHOW GRANT ROLE read_auth
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:database, type:string, comment:from deserializer), FieldSchema(name:table, type:string, comment:from deserializer), FieldSchema(name:partition, type:string, comment:from deserializer), FieldSchema(name:column, type:string, comment:from deserializer), FieldSchema(name:principal_name, type:string, comment:from deserializer), FieldSchema(name:principal_type, type:string, comment:from deserializer), FieldSchema(name:privilege, type:string, comment:from deserializer), FieldSchema(name:grant_option, type:boolean, comment:from deserializer), FieldSchema(name:grant_time, type:bigint, comment:from deserializer), FieldSchema(name:grantor, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20160922115858_10f3ffe0-4409-401a-b712-6271baafa16e); Time taken: 0.06 seconds
INFO  : Executing command(queryId=hive_20160922115858_10f3ffe0-4409-401a-b712-6271baafa16e): SHOW GRANT ROLE read_auth
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20160922115858_10f3ffe0-4409-401a-b712-6271baafa16e); Time taken: 0.023 seconds
INFO  : OK
+-----------+--------+------------+---------+-----------------+-----------------+------------+---------------+-------------------+----------+--+
| database  | table  | partition  | column  | principal_name  | principal_type  | privilege  | grant_option  |    grant_time     | grantor  |
+-----------+--------+------------+---------+-----------------+-----------------+------------+---------------+-------------------+----------+--+
| default   |        |            |         | read_auth       | ROLE            | select     | false         | 1474559017219000  | --       |
+-----------+--------+------------+---------+-----------------+-----------------+------------+---------------+-------------------+----------+--+
1 row selected (0.097 seconds)
```