* i have been logging into hue using michalklempa account before (the admin account - first time login). The real sync happened on users george and ferdinand
```
sqlite> select * from auth_user;
1|pbkdf2_sha256$12000$zbIAa3p7pj08$bzlkBMUYB1okGjcHfG1anciAwK1Q4uiYN61H57oeSZU=|2016-09-21 19:15:50.198140|1|michalklempa||||0|1|2016-09-21 19:15:50.132134
1100713|!|2016-09-21 19:16:42.571829|0|hue||||0|0|2016-09-21 19:16:42.571910
1100714|!RWDFvh9p9ENBtBXG4a3ic8hYxfLvW9HH8VGylWMQ|2016-09-22 09:52:12.093976|0|hdfs||||0|1|2016-09-22 09:52:12.094059
1100715|!EAINGYNhNivt1YkTpqvKu7baef0c17nEIindlhbh|2016-09-22 09:52:12.139686|0|ec2-user||||0|1|2016-09-22 09:52:12.139751
1100716|!bovmKbK4YOwIDUog6XfK83RVYDLqccf5z965Y2xu|2016-09-22 09:52:12.153419|0|mapred||||0|1|2016-09-22 09:52:12.153482
1100717|!UMoiFalO9NI7xWfTk4nGaBzw11Q7wYapXiErnQkv|2016-09-22 09:52:12.179270|0|yarn||||0|1|2016-09-22 09:52:12.179332
1100718|!VM2SRudoJcRhbGU2M9Oc5mWfF2g73dXPpQTDlvQs|2016-09-22 09:52:12.198108|0|ferdinand||||0|1|2016-09-22 09:52:12.198172
1100719|!od6aa02VelT2S7IBHj6uTemx3xollHQaCJOFrhjk|2016-09-22 09:52:12.212324|0|george||||0|1|2016-09-22 09:52:12.212390
```
* ok, password must be set in hue, crazy. if we would not mind HUE doing double hashing, import could take shadowed password from /etc/shadow, and reshash it using PBKDF2, but ok, I gave ferdinand password using HUE admin (michaklempa):
```
sqlite> select * from auth_user;
1|pbkdf2_sha256$12000$zbIAa3p7pj08$bzlkBMUYB1okGjcHfG1anciAwK1Q4uiYN61H57oeSZU=|2016-09-22 10:05:43.622844|1|michalklempa||||0|1|2016-09-21 19:15:50.132134
1100713|!|2016-09-21 19:16:42.571829|0|hue||||0|0|2016-09-21 19:16:42.571910
1100714|!RWDFvh9p9ENBtBXG4a3ic8hYxfLvW9HH8VGylWMQ|2016-09-22 09:52:12.093976|0|hdfs||||0|1|2016-09-22 09:52:12.094059
1100715|!EAINGYNhNivt1YkTpqvKu7baef0c17nEIindlhbh|2016-09-22 09:52:12.139686|0|ec2-user||||0|1|2016-09-22 09:52:12.139751
1100716|!bovmKbK4YOwIDUog6XfK83RVYDLqccf5z965Y2xu|2016-09-22 09:52:12.153419|0|mapred||||0|1|2016-09-22 09:52:12.153482
1100717|!UMoiFalO9NI7xWfTk4nGaBzw11Q7wYapXiErnQkv|2016-09-22 09:52:12.179270|0|yarn||||0|1|2016-09-22 09:52:12.179332
1100718|pbkdf2_sha256$12000$TrbhVaopWt4w$ZSZZSJLEBHaNoUaoRrZmZkFk3g+VHJpSvhxhcRrlZhM=|2016-09-22 10:06:18.323100|0|ferdinand||||0|1|2016-09-22 09:52:12.198172
1100719|!od6aa02VelT2S7IBHj6uTemx3xollHQaCJOFrhjk|2016-09-22 09:52:12.212324|0|george||||0|1|2016-09-22 09:52:12.212390
```
