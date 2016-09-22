* of course we've found out that teragen is not outputing 10GB data, then the script was not writing time results to any log file.
* This is output from nigthly run:
```
[hdfs@klempa2 ~]$ cat TG.log 
Mappers: 100 Reducers: 100 Container memory: 256

real	6m41.688s
user	0m15.279s
sys	0m0.671s
Mappers: 100 Reducers: 100 Container memory: 1024

real	7m53.482s
user	0m14.935s
sys	0m0.704s
Mappers: 100 Reducers: 100 Container memory: 2048

real	6m15.439s
user	0m15.460s
sys	0m0.734s
Mappers: 100 Reducers: 70 Container memory: 256

real	6m45.344s
user	0m15.832s
sys	0m0.734s
Mappers: 100 Reducers: 70 Container memory: 1024

real	7m33.544s
user	0m15.362s
sys	0m0.738s
Mappers: 100 Reducers: 70 Container memory: 2048

real	6m58.570s
user	0m15.234s
sys	0m0.688s
Mappers: 100 Reducers: 40 Container memory: 256

real	5m39.283s
user	0m15.463s
sys	0m0.653s
Mappers: 100 Reducers: 40 Container memory: 1024

real	7m4.006s
user	0m14.443s
sys	0m0.662s
Mappers: 100 Reducers: 40 Container memory: 2048

real	5m41.199s
user	0m15.397s
sys	0m0.674s
Mappers: 100 Reducers: 10 Container memory: 256

real	4m25.053s
user	0m14.680s
sys	0m0.631s
Mappers: 100 Reducers: 10 Container memory: 1024

real	1m39.303s
user	0m6.042s
sys	0m0.276s
Mappers: 100 Reducers: 10 Container memory: 2048

real	1m11.124s
user	0m6.262s
sys	0m0.301s
Mappers: 70 Reducers: 100 Container memory: 256

real	1m12.758s
user	0m6.447s
sys	0m0.279s
Mappers: 70 Reducers: 100 Container memory: 1024

real	0m2.930s
user	0m5.073s
sys	0m0.218s
Mappers: 70 Reducers: 100 Container memory: 2048

real	0m2.994s
user	0m4.433s
sys	0m0.218s
Mappers: 70 Reducers: 70 Container memory: 256

real	0m2.970s
user	0m5.213s
sys	0m0.206s
Mappers: 70 Reducers: 70 Container memory: 1024

real	0m3.028s
user	0m4.460s
sys	0m0.211s
Mappers: 70 Reducers: 70 Container memory: 2048

real	0m2.907s
user	0m4.738s
sys	0m0.220s
Mappers: 70 Reducers: 40 Container memory: 256

real	0m3.042s
user	0m4.558s
sys	0m0.197s
Mappers: 70 Reducers: 40 Container memory: 1024

real	0m3.152s
user	0m4.875s
sys	0m0.231s
Mappers: 70 Reducers: 40 Container memory: 2048

real	0m3.336s
user	0m5.409s
sys	0m0.238s
Mappers: 70 Reducers: 10 Container memory: 256

real	0m2.964s
user	0m5.235s
sys	0m0.206s
Mappers: 70 Reducers: 10 Container memory: 1024

real	0m3.001s
user	0m4.471s
sys	0m0.209s
Mappers: 70 Reducers: 10 Container memory: 2048

real	0m2.878s
user	0m4.759s
sys	0m0.209s
Mappers: 40 Reducers: 100 Container memory: 256

real	0m3.116s
user	0m4.758s
sys	0m0.228s
Mappers: 40 Reducers: 100 Container memory: 1024

real	0m2.943s
user	0m4.400s
sys	0m0.189s
Mappers: 40 Reducers: 100 Container memory: 2048

real	0m3.029s
user	0m4.615s
sys	0m0.199s
Mappers: 40 Reducers: 70 Container memory: 256

real	0m3.097s
user	0m4.686s
sys	0m0.209s
Mappers: 40 Reducers: 70 Container memory: 1024

real	0m3.075s
user	0m4.535s
sys	0m0.208s
Mappers: 40 Reducers: 70 Container memory: 2048

real	0m3.033s
user	0m4.587s
sys	0m0.217s
Mappers: 40 Reducers: 40 Container memory: 256

real	0m3.005s
user	0m4.707s
sys	0m0.216s
Mappers: 40 Reducers: 40 Container memory: 1024

real	0m3.018s
user	0m5.099s
sys	0m0.223s
Mappers: 40 Reducers: 40 Container memory: 2048

real	0m3.093s
user	0m5.314s
sys	0m0.250s
Mappers: 40 Reducers: 10 Container memory: 256

real	0m3.079s
user	0m4.637s
sys	0m0.217s
Mappers: 40 Reducers: 10 Container memory: 1024

real	0m3.198s
user	0m4.931s
sys	0m0.213s
Mappers: 40 Reducers: 10 Container memory: 2048

real	0m3.057s
user	0m4.469s
sys	0m0.203s
Mappers: 10 Reducers: 100 Container memory: 256

real	0m3.104s
user	0m4.569s
sys	0m0.211s
Mappers: 10 Reducers: 100 Container memory: 1024

real	0m2.930s
user	0m4.789s
sys	0m0.199s
Mappers: 10 Reducers: 100 Container memory: 2048

real	0m2.904s
user	0m4.481s
sys	0m0.193s
Mappers: 10 Reducers: 70 Container memory: 256

real	0m3.021s
user	0m4.607s
sys	0m0.194s
Mappers: 10 Reducers: 70 Container memory: 1024

real	0m2.923s
user	0m4.463s
sys	0m0.213s
Mappers: 10 Reducers: 70 Container memory: 2048

real	0m2.997s
user	0m4.438s
sys	0m0.174s
Mappers: 10 Reducers: 40 Container memory: 256

real	0m3.075s
user	0m4.524s
sys	0m0.218s
Mappers: 10 Reducers: 40 Container memory: 1024

real	0m2.972s
user	0m4.617s
sys	0m0.234s
Mappers: 10 Reducers: 40 Container memory: 2048

real	0m2.915s
user	0m4.454s
sys	0m0.228s
Mappers: 10 Reducers: 10 Container memory: 256

real	0m3.102s
user	0m4.753s
sys	0m0.225s
Mappers: 10 Reducers: 10 Container memory: 1024

real	0m3.046s
user	0m4.499s
sys	0m0.199s
Mappers: 10 Reducers: 10 Container memory: 2048

real	0m2.992s
user	0m4.596s
sys	0m0.236s
```
* at `Mappers: 100 Reducers: 10 Container memory: 1024` something happened, ses the of of this particular job:
```
[hdfs@klempa2 ~]$ cat tera_100_10_1024.err 
16/09/22 01:11:47 INFO client.RMProxy: Connecting to ResourceManager at klempa1.cdh.seb/172.31.9.86:8032
16/09/22 01:11:47 INFO hdfs.DFSClient: Created HDFS_DELEGATION_TOKEN token 21 for hdfs on ha-hdfs:nameservice1
16/09/22 01:11:47 INFO security.TokenCache: Got dt for hdfs://nameservice1; Kind: HDFS_DELEGATION_TOKEN, Service: ha-hdfs:nameservice1, Ident: (HDFS_DELEGATION_TOKEN token 21 for hdfs)
16/09/22 01:11:47 INFO terasort.TeraSort: Generating 100000000 using 100
16/09/22 01:11:47 INFO mapreduce.JobSubmitter: number of splits:100
16/09/22 01:11:48 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1474512955446_0021
16/09/22 01:11:48 INFO mapreduce.JobSubmitter: Kind: HDFS_DELEGATION_TOKEN, Service: ha-hdfs:nameservice1, Ident: (HDFS_DELEGATION_TOKEN token 21 for hdfs)
16/09/22 01:11:48 INFO impl.YarnClientImpl: Submitted application application_1474512955446_0021
16/09/22 01:11:48 INFO mapreduce.Job: The url to track the job: http://klempa1.cdh.seb:8088/proxy/application_1474512955446_0021/
16/09/22 01:11:48 INFO mapreduce.Job: Running job: job_1474512955446_0021
16/09/22 01:11:56 INFO mapreduce.Job: Job job_1474512955446_0021 running in uber mode : false
16/09/22 01:11:56 INFO mapreduce.Job:  map 0% reduce 0%
16/09/22 01:12:37 INFO mapreduce.Job:  map 1% reduce 0%
16/09/22 01:12:38 INFO mapreduce.Job:  map 3% reduce 0%
16/09/22 01:12:39 INFO mapreduce.Job:  map 5% reduce 0%
16/09/22 01:12:40 INFO mapreduce.Job:  map 6% reduce 0%
16/09/22 01:12:41 INFO mapreduce.Job:  map 9% reduce 0%
16/09/22 01:12:42 INFO mapreduce.Job:  map 13% reduce 0%
16/09/22 01:12:43 INFO mapreduce.Job:  map 15% reduce 0%
16/09/22 01:12:44 INFO mapreduce.Job:  map 19% reduce 0%
16/09/22 01:12:45 INFO mapreduce.Job:  map 22% reduce 0%
16/09/22 01:12:46 INFO mapreduce.Job:  map 23% reduce 0%
16/09/22 01:12:47 INFO mapreduce.Job:  map 25% reduce 0%
16/09/22 01:12:48 INFO mapreduce.Job:  map 28% reduce 0%
16/09/22 01:12:50 INFO mapreduce.Job:  map 29% reduce 0%
16/09/22 01:12:51 INFO mapreduce.Job:  map 30% reduce 0%
16/09/22 01:12:51 INFO mapreduce.Job: Task Id : attempt_1474512955446_0021_m_000052_0, Status : FAILED
Error: org.apache.hadoop.ipc.RemoteException(java.io.IOException): File /results/tg-10GB-100-10-1024/_temporary/1/_temporary/attempt_1474512955446_0021_m_000052_0/part-m-00052 could only be replicated to 0 nodes instead of minReplication (=1).  There are 5 datanode(s) running and no node(s) are excluded in this operation.
	at org.apache.hadoop.hdfs.server.blockmanagement.BlockManager.chooseTarget4NewBlock(BlockManager.java:1610)
	at org.apache.hadoop.hdfs.server.namenode.FSNamesystem.getAdditionalBlock(FSNamesystem.java:3315)
	at org.apache.hadoop.hdfs.server.namenode.NameNodeRpcServer.addBlock(NameNodeRpcServer.java:679)
	at org.apache.hadoop.hdfs.server.namenode.AuthorizationProviderProxyClientProtocol.addBlock(AuthorizationProviderProxyClientProtocol.java:214)
	at org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolServerSideTranslatorPB.addBlock(ClientNamenodeProtocolServerSideTranslatorPB.java:489)
	at org.apache.hadoop.hdfs.protocol.proto.ClientNamenodeProtocolProtos$ClientNamenodeProtocol$2.callBlockingMethod(ClientNamenodeProtocolProtos.java)
	at org.apache.hadoop.ipc.ProtobufRpcEngine$Server$ProtoBufRpcInvoker.call(ProtobufRpcEngine.java:617)
	at org.apache.hadoop.ipc.RPC$Server.call(RPC.java:1073)
	at org.apache.hadoop.ipc.Server$Handler$1.run(Server.java:2086)
	at org.apache.hadoop.ipc.Server$Handler$1.run(Server.java:2082)
	at java.security.AccessController.doPrivileged(Native Method)
	at javax.security.auth.Subject.doAs(Subject.java:415)
	at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1693)
	at org.apache.hadoop.ipc.Server$Handler.run(Server.java:2080)

	at org.apache.hadoop.ipc.Client.call(Client.java:1471)
	at org.apache.hadoop.ipc.Client.call(Client.java:1408)
	at org.apache.hadoop.ipc.ProtobufRpcEngine$Invoker.invoke(ProtobufRpcEngine.java:230)
	at com.sun.proxy.$Proxy15.addBlock(Unknown Source)
	at org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolTranslatorPB.addBlock(ClientNamenodeProtocolTranslatorPB.java:409)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:606)
	at org.apache.hadoop.io.retry.RetryInvocationHandler.invokeMethod(RetryInvocationHandler.java:256)
	at org.apache.hadoop.io.retry.RetryInvocationHandler.invoke(RetryInvocationHandler.java:104)
	at com.sun.proxy.$Proxy16.addBlock(Unknown Source)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.locateFollowingBlock(DFSOutputStream.java:1733)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.nextBlockOutputStream(DFSOutputStream.java:1529)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.run(DFSOutputStream.java:683)

16/09/22 01:12:52 INFO mapreduce.Job:  map 31% reduce 0%
16/09/22 01:12:54 INFO mapreduce.Job:  map 32% reduce 0%
16/09/22 01:12:55 INFO mapreduce.Job:  map 33% reduce 0%
16/09/22 01:12:57 INFO mapreduce.Job:  map 36% reduce 0%
16/09/22 01:12:59 INFO mapreduce.Job: Task Id : attempt_1474512955446_0021_m_000052_1, Status : FAILED
Error: org.apache.hadoop.ipc.RemoteException(java.io.IOException): File /results/tg-10GB-100-10-1024/_temporary/1/_temporary/attempt_1474512955446_0021_m_000052_1/part-m-00052 could only be replicated to 0 nodes instead of minReplication (=1).  There are 5 datanode(s) running and no node(s) are excluded in this operation.
	at org.apache.hadoop.hdfs.server.blockmanagement.BlockManager.chooseTarget4NewBlock(BlockManager.java:1610)
	at org.apache.hadoop.hdfs.server.namenode.FSNamesystem.getAdditionalBlock(FSNamesystem.java:3315)
	at org.apache.hadoop.hdfs.server.namenode.NameNodeRpcServer.addBlock(NameNodeRpcServer.java:679)
	at org.apache.hadoop.hdfs.server.namenode.AuthorizationProviderProxyClientProtocol.addBlock(AuthorizationProviderProxyClientProtocol.java:214)
	at org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolServerSideTranslatorPB.addBlock(ClientNamenodeProtocolServerSideTranslatorPB.java:489)
	at org.apache.hadoop.hdfs.protocol.proto.ClientNamenodeProtocolProtos$ClientNamenodeProtocol$2.callBlockingMethod(ClientNamenodeProtocolProtos.java)
	at org.apache.hadoop.ipc.ProtobufRpcEngine$Server$ProtoBufRpcInvoker.call(ProtobufRpcEngine.java:617)
	at org.apache.hadoop.ipc.RPC$Server.call(RPC.java:1073)
	at org.apache.hadoop.ipc.Server$Handler$1.run(Server.java:2086)
	at org.apache.hadoop.ipc.Server$Handler$1.run(Server.java:2082)
	at java.security.AccessController.doPrivileged(Native Method)
	at javax.security.auth.Subject.doAs(Subject.java:415)
	at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1693)
	at org.apache.hadoop.ipc.Server$Handler.run(Server.java:2080)

	at org.apache.hadoop.ipc.Client.call(Client.java:1471)
	at org.apache.hadoop.ipc.Client.call(Client.java:1408)
	at org.apache.hadoop.ipc.ProtobufRpcEngine$Invoker.invoke(ProtobufRpcEngine.java:230)
	at com.sun.proxy.$Proxy15.addBlock(Unknown Source)
	at org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolTranslatorPB.addBlock(ClientNamenodeProtocolTranslatorPB.java:409)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:606)
	at org.apache.hadoop.io.retry.RetryInvocationHandler.invokeMethod(RetryInvocationHandler.java:256)
	at org.apache.hadoop.io.retry.RetryInvocationHandler.invoke(RetryInvocationHandler.java:104)
	at com.sun.proxy.$Proxy16.addBlock(Unknown Source)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.locateFollowingBlock(DFSOutputStream.java:1733)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.nextBlockOutputStream(DFSOutputStream.java:1529)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.run(DFSOutputStream.java:683)

16/09/22 01:13:00 INFO mapreduce.Job:  map 38% reduce 0%
16/09/22 01:13:03 INFO mapreduce.Job:  map 40% reduce 0%
16/09/22 01:13:06 INFO mapreduce.Job:  map 41% reduce 0%
16/09/22 01:13:07 INFO mapreduce.Job:  map 42% reduce 0%
16/09/22 01:13:08 INFO mapreduce.Job:  map 43% reduce 0%
16/09/22 01:13:08 INFO mapreduce.Job: Task Id : attempt_1474512955446_0021_m_000052_2, Status : FAILED
Error: org.apache.hadoop.ipc.RemoteException(java.io.IOException): File /results/tg-10GB-100-10-1024/_temporary/1/_temporary/attempt_1474512955446_0021_m_000052_2/part-m-00052 could only be replicated to 0 nodes instead of minReplication (=1).  There are 5 datanode(s) running and no node(s) are excluded in this operation.
	at org.apache.hadoop.hdfs.server.blockmanagement.BlockManager.chooseTarget4NewBlock(BlockManager.java:1610)
	at org.apache.hadoop.hdfs.server.namenode.FSNamesystem.getAdditionalBlock(FSNamesystem.java:3315)
	at org.apache.hadoop.hdfs.server.namenode.NameNodeRpcServer.addBlock(NameNodeRpcServer.java:679)
	at org.apache.hadoop.hdfs.server.namenode.AuthorizationProviderProxyClientProtocol.addBlock(AuthorizationProviderProxyClientProtocol.java:214)
	at org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolServerSideTranslatorPB.addBlock(ClientNamenodeProtocolServerSideTranslatorPB.java:489)
	at org.apache.hadoop.hdfs.protocol.proto.ClientNamenodeProtocolProtos$ClientNamenodeProtocol$2.callBlockingMethod(ClientNamenodeProtocolProtos.java)
	at org.apache.hadoop.ipc.ProtobufRpcEngine$Server$ProtoBufRpcInvoker.call(ProtobufRpcEngine.java:617)
	at org.apache.hadoop.ipc.RPC$Server.call(RPC.java:1073)
	at org.apache.hadoop.ipc.Server$Handler$1.run(Server.java:2086)
	at org.apache.hadoop.ipc.Server$Handler$1.run(Server.java:2082)
	at java.security.AccessController.doPrivileged(Native Method)
	at javax.security.auth.Subject.doAs(Subject.java:415)
	at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1693)
	at org.apache.hadoop.ipc.Server$Handler.run(Server.java:2080)

	at org.apache.hadoop.ipc.Client.call(Client.java:1471)
	at org.apache.hadoop.ipc.Client.call(Client.java:1408)
	at org.apache.hadoop.ipc.ProtobufRpcEngine$Invoker.invoke(ProtobufRpcEngine.java:230)
	at com.sun.proxy.$Proxy15.addBlock(Unknown Source)
	at org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolTranslatorPB.addBlock(ClientNamenodeProtocolTranslatorPB.java:409)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:606)
	at org.apache.hadoop.io.retry.RetryInvocationHandler.invokeMethod(RetryInvocationHandler.java:256)
	at org.apache.hadoop.io.retry.RetryInvocationHandler.invoke(RetryInvocationHandler.java:104)
	at com.sun.proxy.$Proxy16.addBlock(Unknown Source)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.locateFollowingBlock(DFSOutputStream.java:1733)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.nextBlockOutputStream(DFSOutputStream.java:1529)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.run(DFSOutputStream.java:683)

16/09/22 01:13:08 INFO mapreduce.Job: Task Id : attempt_1474512955446_0021_m_000059_0, Status : FAILED
Error: org.apache.hadoop.ipc.RemoteException(java.io.IOException): File /results/tg-10GB-100-10-1024/_temporary/1/_temporary/attempt_1474512955446_0021_m_000059_0/part-m-00059 could only be replicated to 0 nodes instead of minReplication (=1).  There are 5 datanode(s) running and no node(s) are excluded in this operation.
	at org.apache.hadoop.hdfs.server.blockmanagement.BlockManager.chooseTarget4NewBlock(BlockManager.java:1610)
	at org.apache.hadoop.hdfs.server.namenode.FSNamesystem.getAdditionalBlock(FSNamesystem.java:3315)
	at org.apache.hadoop.hdfs.server.namenode.NameNodeRpcServer.addBlock(NameNodeRpcServer.java:679)
	at org.apache.hadoop.hdfs.server.namenode.AuthorizationProviderProxyClientProtocol.addBlock(AuthorizationProviderProxyClientProtocol.java:214)
	at org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolServerSideTranslatorPB.addBlock(ClientNamenodeProtocolServerSideTranslatorPB.java:489)
	at org.apache.hadoop.hdfs.protocol.proto.ClientNamenodeProtocolProtos$ClientNamenodeProtocol$2.callBlockingMethod(ClientNamenodeProtocolProtos.java)
	at org.apache.hadoop.ipc.ProtobufRpcEngine$Server$ProtoBufRpcInvoker.call(ProtobufRpcEngine.java:617)
	at org.apache.hadoop.ipc.RPC$Server.call(RPC.java:1073)
	at org.apache.hadoop.ipc.Server$Handler$1.run(Server.java:2086)
	at org.apache.hadoop.ipc.Server$Handler$1.run(Server.java:2082)
	at java.security.AccessController.doPrivileged(Native Method)
	at javax.security.auth.Subject.doAs(Subject.java:415)
	at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1693)
	at org.apache.hadoop.ipc.Server$Handler.run(Server.java:2080)

	at org.apache.hadoop.ipc.Client.call(Client.java:1471)
	at org.apache.hadoop.ipc.Client.call(Client.java:1408)
	at org.apache.hadoop.ipc.ProtobufRpcEngine$Invoker.invoke(ProtobufRpcEngine.java:230)
	at com.sun.proxy.$Proxy15.addBlock(Unknown Source)
	at org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolTranslatorPB.addBlock(ClientNamenodeProtocolTranslatorPB.java:409)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:606)
	at org.apache.hadoop.io.retry.RetryInvocationHandler.invokeMethod(RetryInvocationHandler.java:256)
	at org.apache.hadoop.io.retry.RetryInvocationHandler.invoke(RetryInvocationHandler.java:104)
	at com.sun.proxy.$Proxy16.addBlock(Unknown Source)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.locateFollowingBlock(DFSOutputStream.java:1733)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.nextBlockOutputStream(DFSOutputStream.java:1529)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.run(DFSOutputStream.java:683)

16/09/22 01:13:09 INFO mapreduce.Job:  map 44% reduce 0%
16/09/22 01:13:11 INFO mapreduce.Job:  map 45% reduce 0%
16/09/22 01:13:12 INFO mapreduce.Job:  map 46% reduce 0%
16/09/22 01:13:13 INFO mapreduce.Job:  map 47% reduce 0%
16/09/22 01:13:13 INFO mapreduce.Job: Task Id : attempt_1474512955446_0021_m_000064_0, Status : FAILED
Error: org.apache.hadoop.ipc.RemoteException(java.io.IOException): File /results/tg-10GB-100-10-1024/_temporary/1/_temporary/attempt_1474512955446_0021_m_000064_0/part-m-00064 could only be replicated to 0 nodes instead of minReplication (=1).  There are 5 datanode(s) running and no node(s) are excluded in this operation.
	at org.apache.hadoop.hdfs.server.blockmanagement.BlockManager.chooseTarget4NewBlock(BlockManager.java:1610)
	at org.apache.hadoop.hdfs.server.namenode.FSNamesystem.getAdditionalBlock(FSNamesystem.java:3315)
	at org.apache.hadoop.hdfs.server.namenode.NameNodeRpcServer.addBlock(NameNodeRpcServer.java:679)
	at org.apache.hadoop.hdfs.server.namenode.AuthorizationProviderProxyClientProtocol.addBlock(AuthorizationProviderProxyClientProtocol.java:214)
	at org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolServerSideTranslatorPB.addBlock(ClientNamenodeProtocolServerSideTranslatorPB.java:489)
	at org.apache.hadoop.hdfs.protocol.proto.ClientNamenodeProtocolProtos$ClientNamenodeProtocol$2.callBlockingMethod(ClientNamenodeProtocolProtos.java)
	at org.apache.hadoop.ipc.ProtobufRpcEngine$Server$ProtoBufRpcInvoker.call(ProtobufRpcEngine.java:617)
	at org.apache.hadoop.ipc.RPC$Server.call(RPC.java:1073)
	at org.apache.hadoop.ipc.Server$Handler$1.run(Server.java:2086)
	at org.apache.hadoop.ipc.Server$Handler$1.run(Server.java:2082)
	at java.security.AccessController.doPrivileged(Native Method)
	at javax.security.auth.Subject.doAs(Subject.java:415)
	at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1693)
	at org.apache.hadoop.ipc.Server$Handler.run(Server.java:2080)

	at org.apache.hadoop.ipc.Client.call(Client.java:1471)
	at org.apache.hadoop.ipc.Client.call(Client.java:1408)
	at org.apache.hadoop.ipc.ProtobufRpcEngine$Invoker.invoke(ProtobufRpcEngine.java:230)
	at com.sun.proxy.$Proxy15.addBlock(Unknown Source)
	at org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolTranslatorPB.addBlock(ClientNamenodeProtocolTranslatorPB.java:409)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:606)
	at org.apache.hadoop.io.retry.RetryInvocationHandler.invokeMethod(RetryInvocationHandler.java:256)
	at org.apache.hadoop.io.retry.RetryInvocationHandler.invoke(RetryInvocationHandler.java:104)
	at com.sun.proxy.$Proxy16.addBlock(Unknown Source)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.locateFollowingBlock(DFSOutputStream.java:1733)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.nextBlockOutputStream(DFSOutputStream.java:1529)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.run(DFSOutputStream.java:683)

16/09/22 01:13:13 INFO mapreduce.Job: Task Id : attempt_1474512955446_0021_m_000061_0, Status : FAILED
Error: org.apache.hadoop.ipc.RemoteException(java.io.IOException): File /results/tg-10GB-100-10-1024/_temporary/1/_temporary/attempt_1474512955446_0021_m_000061_0/part-m-00061 could only be replicated to 0 nodes instead of minReplication (=1).  There are 5 datanode(s) running and no node(s) are excluded in this operation.
	at org.apache.hadoop.hdfs.server.blockmanagement.BlockManager.chooseTarget4NewBlock(BlockManager.java:1610)
	at org.apache.hadoop.hdfs.server.namenode.FSNamesystem.getAdditionalBlock(FSNamesystem.java:3315)
	at org.apache.hadoop.hdfs.server.namenode.NameNodeRpcServer.addBlock(NameNodeRpcServer.java:679)
	at org.apache.hadoop.hdfs.server.namenode.AuthorizationProviderProxyClientProtocol.addBlock(AuthorizationProviderProxyClientProtocol.java:214)
	at org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolServerSideTranslatorPB.addBlock(ClientNamenodeProtocolServerSideTranslatorPB.java:489)
	at org.apache.hadoop.hdfs.protocol.proto.ClientNamenodeProtocolProtos$ClientNamenodeProtocol$2.callBlockingMethod(ClientNamenodeProtocolProtos.java)
	at org.apache.hadoop.ipc.ProtobufRpcEngine$Server$ProtoBufRpcInvoker.call(ProtobufRpcEngine.java:617)
	at org.apache.hadoop.ipc.RPC$Server.call(RPC.java:1073)
	at org.apache.hadoop.ipc.Server$Handler$1.run(Server.java:2086)
	at org.apache.hadoop.ipc.Server$Handler$1.run(Server.java:2082)
	at java.security.AccessController.doPrivileged(Native Method)
	at javax.security.auth.Subject.doAs(Subject.java:415)
	at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1693)
	at org.apache.hadoop.ipc.Server$Handler.run(Server.java:2080)

	at org.apache.hadoop.ipc.Client.call(Client.java:1471)
	at org.apache.hadoop.ipc.Client.call(Client.java:1408)
	at org.apache.hadoop.ipc.ProtobufRpcEngine$Invoker.invoke(ProtobufRpcEngine.java:230)
	at com.sun.proxy.$Proxy15.addBlock(Unknown Source)
	at org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolTranslatorPB.addBlock(ClientNamenodeProtocolTranslatorPB.java:409)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:606)
	at org.apache.hadoop.io.retry.RetryInvocationHandler.invokeMethod(RetryInvocationHandler.java:256)
	at org.apache.hadoop.io.retry.RetryInvocationHandler.invoke(RetryInvocationHandler.java:104)
	at com.sun.proxy.$Proxy16.addBlock(Unknown Source)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.locateFollowingBlock(DFSOutputStream.java:1733)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.nextBlockOutputStream(DFSOutputStream.java:1529)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.run(DFSOutputStream.java:683)

16/09/22 01:13:14 INFO mapreduce.Job:  map 48% reduce 0%
16/09/22 01:13:14 INFO mapreduce.Job: Task Id : attempt_1474512955446_0021_m_000060_0, Status : FAILED
Error: org.apache.hadoop.ipc.RemoteException(java.io.IOException): File /results/tg-10GB-100-10-1024/_temporary/1/_temporary/attempt_1474512955446_0021_m_000060_0/part-m-00060 could only be replicated to 0 nodes instead of minReplication (=1).  There are 5 datanode(s) running and no node(s) are excluded in this operation.
	at org.apache.hadoop.hdfs.server.blockmanagement.BlockManager.chooseTarget4NewBlock(BlockManager.java:1610)
	at org.apache.hadoop.hdfs.server.namenode.FSNamesystem.getAdditionalBlock(FSNamesystem.java:3315)
	at org.apache.hadoop.hdfs.server.namenode.NameNodeRpcServer.addBlock(NameNodeRpcServer.java:679)
	at org.apache.hadoop.hdfs.server.namenode.AuthorizationProviderProxyClientProtocol.addBlock(AuthorizationProviderProxyClientProtocol.java:214)
	at org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolServerSideTranslatorPB.addBlock(ClientNamenodeProtocolServerSideTranslatorPB.java:489)
	at org.apache.hadoop.hdfs.protocol.proto.ClientNamenodeProtocolProtos$ClientNamenodeProtocol$2.callBlockingMethod(ClientNamenodeProtocolProtos.java)
	at org.apache.hadoop.ipc.ProtobufRpcEngine$Server$ProtoBufRpcInvoker.call(ProtobufRpcEngine.java:617)
	at org.apache.hadoop.ipc.RPC$Server.call(RPC.java:1073)
	at org.apache.hadoop.ipc.Server$Handler$1.run(Server.java:2086)
	at org.apache.hadoop.ipc.Server$Handler$1.run(Server.java:2082)
	at java.security.AccessController.doPrivileged(Native Method)
	at javax.security.auth.Subject.doAs(Subject.java:415)
	at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1693)
	at org.apache.hadoop.ipc.Server$Handler.run(Server.java:2080)

	at org.apache.hadoop.ipc.Client.call(Client.java:1471)
	at org.apache.hadoop.ipc.Client.call(Client.java:1408)
	at org.apache.hadoop.ipc.ProtobufRpcEngine$Invoker.invoke(ProtobufRpcEngine.java:230)
	at com.sun.proxy.$Proxy15.addBlock(Unknown Source)
	at org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolTranslatorPB.addBlock(ClientNamenodeProtocolTranslatorPB.java:409)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:606)
	at org.apache.hadoop.io.retry.RetryInvocationHandler.invokeMethod(RetryInvocationHandler.java:256)
	at org.apache.hadoop.io.retry.RetryInvocationHandler.invoke(RetryInvocationHandler.java:104)
	at com.sun.proxy.$Proxy16.addBlock(Unknown Source)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.locateFollowingBlock(DFSOutputStream.java:1733)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.nextBlockOutputStream(DFSOutputStream.java:1529)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.run(DFSOutputStream.java:683)

16/09/22 01:13:14 INFO mapreduce.Job: Task Id : attempt_1474512955446_0021_m_000063_0, Status : FAILED
Error: org.apache.hadoop.ipc.RemoteException(java.io.IOException): File /results/tg-10GB-100-10-1024/_temporary/1/_temporary/attempt_1474512955446_0021_m_000063_0/part-m-00063 could only be replicated to 0 nodes instead of minReplication (=1).  There are 5 datanode(s) running and no node(s) are excluded in this operation.
	at org.apache.hadoop.hdfs.server.blockmanagement.BlockManager.chooseTarget4NewBlock(BlockManager.java:1610)
	at org.apache.hadoop.hdfs.server.namenode.FSNamesystem.getAdditionalBlock(FSNamesystem.java:3315)
	at org.apache.hadoop.hdfs.server.namenode.NameNodeRpcServer.addBlock(NameNodeRpcServer.java:679)
	at org.apache.hadoop.hdfs.server.namenode.AuthorizationProviderProxyClientProtocol.addBlock(AuthorizationProviderProxyClientProtocol.java:214)
	at org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolServerSideTranslatorPB.addBlock(ClientNamenodeProtocolServerSideTranslatorPB.java:489)
	at org.apache.hadoop.hdfs.protocol.proto.ClientNamenodeProtocolProtos$ClientNamenodeProtocol$2.callBlockingMethod(ClientNamenodeProtocolProtos.java)
	at org.apache.hadoop.ipc.ProtobufRpcEngine$Server$ProtoBufRpcInvoker.call(ProtobufRpcEngine.java:617)
	at org.apache.hadoop.ipc.RPC$Server.call(RPC.java:1073)
	at org.apache.hadoop.ipc.Server$Handler$1.run(Server.java:2086)
	at org.apache.hadoop.ipc.Server$Handler$1.run(Server.java:2082)
	at java.security.AccessController.doPrivileged(Native Method)
	at javax.security.auth.Subject.doAs(Subject.java:415)
	at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1693)
	at org.apache.hadoop.ipc.Server$Handler.run(Server.java:2080)

	at org.apache.hadoop.ipc.Client.call(Client.java:1471)
	at org.apache.hadoop.ipc.Client.call(Client.java:1408)
	at org.apache.hadoop.ipc.ProtobufRpcEngine$Invoker.invoke(ProtobufRpcEngine.java:230)
	at com.sun.proxy.$Proxy15.addBlock(Unknown Source)
	at org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolTranslatorPB.addBlock(ClientNamenodeProtocolTranslatorPB.java:409)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:606)
	at org.apache.hadoop.io.retry.RetryInvocationHandler.invokeMethod(RetryInvocationHandler.java:256)
	at org.apache.hadoop.io.retry.RetryInvocationHandler.invoke(RetryInvocationHandler.java:104)
	at com.sun.proxy.$Proxy16.addBlock(Unknown Source)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.locateFollowingBlock(DFSOutputStream.java:1733)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.nextBlockOutputStream(DFSOutputStream.java:1529)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.run(DFSOutputStream.java:683)

16/09/22 01:13:14 INFO mapreduce.Job: Task Id : attempt_1474512955446_0021_m_000059_1, Status : FAILED
Error: org.apache.hadoop.ipc.RemoteException(java.io.IOException): File /results/tg-10GB-100-10-1024/_temporary/1/_temporary/attempt_1474512955446_0021_m_000059_1/part-m-00059 could only be replicated to 0 nodes instead of minReplication (=1).  There are 5 datanode(s) running and no node(s) are excluded in this operation.
	at org.apache.hadoop.hdfs.server.blockmanagement.BlockManager.chooseTarget4NewBlock(BlockManager.java:1610)
	at org.apache.hadoop.hdfs.server.namenode.FSNamesystem.getAdditionalBlock(FSNamesystem.java:3315)
	at org.apache.hadoop.hdfs.server.namenode.NameNodeRpcServer.addBlock(NameNodeRpcServer.java:679)
	at org.apache.hadoop.hdfs.server.namenode.AuthorizationProviderProxyClientProtocol.addBlock(AuthorizationProviderProxyClientProtocol.java:214)
	at org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolServerSideTranslatorPB.addBlock(ClientNamenodeProtocolServerSideTranslatorPB.java:489)
	at org.apache.hadoop.hdfs.protocol.proto.ClientNamenodeProtocolProtos$ClientNamenodeProtocol$2.callBlockingMethod(ClientNamenodeProtocolProtos.java)
	at org.apache.hadoop.ipc.ProtobufRpcEngine$Server$ProtoBufRpcInvoker.call(ProtobufRpcEngine.java:617)
	at org.apache.hadoop.ipc.RPC$Server.call(RPC.java:1073)
	at org.apache.hadoop.ipc.Server$Handler$1.run(Server.java:2086)
	at org.apache.hadoop.ipc.Server$Handler$1.run(Server.java:2082)
	at java.security.AccessController.doPrivileged(Native Method)
	at javax.security.auth.Subject.doAs(Subject.java:415)
	at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1693)
	at org.apache.hadoop.ipc.Server$Handler.run(Server.java:2080)

	at org.apache.hadoop.ipc.Client.call(Client.java:1471)
	at org.apache.hadoop.ipc.Client.call(Client.java:1408)
	at org.apache.hadoop.ipc.ProtobufRpcEngine$Invoker.invoke(ProtobufRpcEngine.java:230)
	at com.sun.proxy.$Proxy15.addBlock(Unknown Source)
	at org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolTranslatorPB.addBlock(ClientNamenodeProtocolTranslatorPB.java:409)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:606)
	at org.apache.hadoop.io.retry.RetryInvocationHandler.invokeMethod(RetryInvocationHandler.java:256)
	at org.apache.hadoop.io.retry.RetryInvocationHandler.invoke(RetryInvocationHandler.java:104)
	at com.sun.proxy.$Proxy16.addBlock(Unknown Source)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.locateFollowingBlock(DFSOutputStream.java:1733)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.nextBlockOutputStream(DFSOutputStream.java:1529)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.run(DFSOutputStream.java:683)

16/09/22 01:13:15 INFO mapreduce.Job: Task Id : attempt_1474512955446_0021_m_000069_0, Status : FAILED
Error: org.apache.hadoop.ipc.RemoteException(java.io.IOException): File /results/tg-10GB-100-10-1024/_temporary/1/_temporary/attempt_1474512955446_0021_m_000069_0/part-m-00069 could only be replicated to 0 nodes instead of minReplication (=1).  There are 5 datanode(s) running and no node(s) are excluded in this operation.
	at org.apache.hadoop.hdfs.server.blockmanagement.BlockManager.chooseTarget4NewBlock(BlockManager.java:1610)
	at org.apache.hadoop.hdfs.server.namenode.FSNamesystem.getAdditionalBlock(FSNamesystem.java:3315)
	at org.apache.hadoop.hdfs.server.namenode.NameNodeRpcServer.addBlock(NameNodeRpcServer.java:679)
	at org.apache.hadoop.hdfs.server.namenode.AuthorizationProviderProxyClientProtocol.addBlock(AuthorizationProviderProxyClientProtocol.java:214)
	at org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolServerSideTranslatorPB.addBlock(ClientNamenodeProtocolServerSideTranslatorPB.java:489)
	at org.apache.hadoop.hdfs.protocol.proto.ClientNamenodeProtocolProtos$ClientNamenodeProtocol$2.callBlockingMethod(ClientNamenodeProtocolProtos.java)
	at org.apache.hadoop.ipc.ProtobufRpcEngine$Server$ProtoBufRpcInvoker.call(ProtobufRpcEngine.java:617)
	at org.apache.hadoop.ipc.RPC$Server.call(RPC.java:1073)
	at org.apache.hadoop.ipc.Server$Handler$1.run(Server.java:2086)
	at org.apache.hadoop.ipc.Server$Handler$1.run(Server.java:2082)
	at java.security.AccessController.doPrivileged(Native Method)
	at javax.security.auth.Subject.doAs(Subject.java:415)
	at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1693)
	at org.apache.hadoop.ipc.Server$Handler.run(Server.java:2080)

	at org.apache.hadoop.ipc.Client.call(Client.java:1471)
	at org.apache.hadoop.ipc.Client.call(Client.java:1408)
	at org.apache.hadoop.ipc.ProtobufRpcEngine$Invoker.invoke(ProtobufRpcEngine.java:230)
	at com.sun.proxy.$Proxy15.addBlock(Unknown Source)
	at org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolTranslatorPB.addBlock(ClientNamenodeProtocolTranslatorPB.java:409)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:606)
	at org.apache.hadoop.io.retry.RetryInvocationHandler.invokeMethod(RetryInvocationHandler.java:256)
	at org.apache.hadoop.io.retry.RetryInvocationHandler.invoke(RetryInvocationHandler.java:104)
	at com.sun.proxy.$Proxy16.addBlock(Unknown Source)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.locateFollowingBlock(DFSOutputStream.java:1733)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.nextBlockOutputStream(DFSOutputStream.java:1529)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.run(DFSOutputStream.java:683)

16/09/22 01:13:16 INFO mapreduce.Job:  map 49% reduce 0%
16/09/22 01:13:16 INFO mapreduce.Job: Task Id : attempt_1474512955446_0021_m_000072_0, Status : FAILED
Error: org.apache.hadoop.ipc.RemoteException(java.io.IOException): File /results/tg-10GB-100-10-1024/_temporary/1/_temporary/attempt_1474512955446_0021_m_000072_0/part-m-00072 could only be replicated to 0 nodes instead of minReplication (=1).  There are 5 datanode(s) running and no node(s) are excluded in this operation.
	at org.apache.hadoop.hdfs.server.blockmanagement.BlockManager.chooseTarget4NewBlock(BlockManager.java:1610)
	at org.apache.hadoop.hdfs.server.namenode.FSNamesystem.getAdditionalBlock(FSNamesystem.java:3315)
	at org.apache.hadoop.hdfs.server.namenode.NameNodeRpcServer.addBlock(NameNodeRpcServer.java:679)
	at org.apache.hadoop.hdfs.server.namenode.AuthorizationProviderProxyClientProtocol.addBlock(AuthorizationProviderProxyClientProtocol.java:214)
	at org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolServerSideTranslatorPB.addBlock(ClientNamenodeProtocolServerSideTranslatorPB.java:489)
	at org.apache.hadoop.hdfs.protocol.proto.ClientNamenodeProtocolProtos$ClientNamenodeProtocol$2.callBlockingMethod(ClientNamenodeProtocolProtos.java)
	at org.apache.hadoop.ipc.ProtobufRpcEngine$Server$ProtoBufRpcInvoker.call(ProtobufRpcEngine.java:617)
	at org.apache.hadoop.ipc.RPC$Server.call(RPC.java:1073)
	at org.apache.hadoop.ipc.Server$Handler$1.run(Server.java:2086)
	at org.apache.hadoop.ipc.Server$Handler$1.run(Server.java:2082)
	at java.security.AccessController.doPrivileged(Native Method)
	at javax.security.auth.Subject.doAs(Subject.java:415)
	at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1693)
	at org.apache.hadoop.ipc.Server$Handler.run(Server.java:2080)

	at org.apache.hadoop.ipc.Client.call(Client.java:1471)
	at org.apache.hadoop.ipc.Client.call(Client.java:1408)
	at org.apache.hadoop.ipc.ProtobufRpcEngine$Invoker.invoke(ProtobufRpcEngine.java:230)
	at com.sun.proxy.$Proxy15.addBlock(Unknown Source)
	at org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolTranslatorPB.addBlock(ClientNamenodeProtocolTranslatorPB.java:409)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:606)
	at org.apache.hadoop.io.retry.RetryInvocationHandler.invokeMethod(RetryInvocationHandler.java:256)
	at org.apache.hadoop.io.retry.RetryInvocationHandler.invoke(RetryInvocationHandler.java:104)
	at com.sun.proxy.$Proxy16.addBlock(Unknown Source)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.locateFollowingBlock(DFSOutputStream.java:1733)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.nextBlockOutputStream(DFSOutputStream.java:1529)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.run(DFSOutputStream.java:683)

16/09/22 01:13:17 INFO mapreduce.Job:  map 50% reduce 0%
16/09/22 01:13:17 INFO mapreduce.Job: Task Id : attempt_1474512955446_0021_m_000068_0, Status : FAILED
Error: org.apache.hadoop.ipc.RemoteException(java.io.IOException): File /results/tg-10GB-100-10-1024/_temporary/1/_temporary/attempt_1474512955446_0021_m_000068_0/part-m-00068 could only be replicated to 0 nodes instead of minReplication (=1).  There are 5 datanode(s) running and no node(s) are excluded in this operation.
	at org.apache.hadoop.hdfs.server.blockmanagement.BlockManager.chooseTarget4NewBlock(BlockManager.java:1610)
	at org.apache.hadoop.hdfs.server.namenode.FSNamesystem.getAdditionalBlock(FSNamesystem.java:3315)
	at org.apache.hadoop.hdfs.server.namenode.NameNodeRpcServer.addBlock(NameNodeRpcServer.java:679)
	at org.apache.hadoop.hdfs.server.namenode.AuthorizationProviderProxyClientProtocol.addBlock(AuthorizationProviderProxyClientProtocol.java:214)
	at org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolServerSideTranslatorPB.addBlock(ClientNamenodeProtocolServerSideTranslatorPB.java:489)
	at org.apache.hadoop.hdfs.protocol.proto.ClientNamenodeProtocolProtos$ClientNamenodeProtocol$2.callBlockingMethod(ClientNamenodeProtocolProtos.java)
	at org.apache.hadoop.ipc.ProtobufRpcEngine$Server$ProtoBufRpcInvoker.call(ProtobufRpcEngine.java:617)
	at org.apache.hadoop.ipc.RPC$Server.call(RPC.java:1073)
	at org.apache.hadoop.ipc.Server$Handler$1.run(Server.java:2086)
	at org.apache.hadoop.ipc.Server$Handler$1.run(Server.java:2082)
	at java.security.AccessController.doPrivileged(Native Method)
	at javax.security.auth.Subject.doAs(Subject.java:415)
	at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1693)
	at org.apache.hadoop.ipc.Server$Handler.run(Server.java:2080)

	at org.apache.hadoop.ipc.Client.call(Client.java:1471)
	at org.apache.hadoop.ipc.Client.call(Client.java:1408)
	at org.apache.hadoop.ipc.ProtobufRpcEngine$Invoker.invoke(ProtobufRpcEngine.java:230)
	at com.sun.proxy.$Proxy15.addBlock(Unknown Source)
	at org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolTranslatorPB.addBlock(ClientNamenodeProtocolTranslatorPB.java:409)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:606)
	at org.apache.hadoop.io.retry.RetryInvocationHandler.invokeMethod(RetryInvocationHandler.java:256)
	at org.apache.hadoop.io.retry.RetryInvocationHandler.invoke(RetryInvocationHandler.java:104)
	at com.sun.proxy.$Proxy16.addBlock(Unknown Source)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.locateFollowingBlock(DFSOutputStream.java:1733)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.nextBlockOutputStream(DFSOutputStream.java:1529)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.run(DFSOutputStream.java:683)

16/09/22 01:13:19 INFO mapreduce.Job:  map 56% reduce 0%
16/09/22 01:13:20 INFO mapreduce.Job:  map 67% reduce 0%
16/09/22 01:13:21 INFO mapreduce.Job:  map 100% reduce 0%
16/09/22 01:13:23 INFO mapreduce.Job: Job job_1474512955446_0021 failed with state FAILED due to: Task failed task_1474512955446_0021_m_000052
Job failed as tasks failed. failedMaps:1 failedReduces:0

16/09/22 01:13:23 INFO mapreduce.Job: Counters: 33
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=3552290
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=2480
		HDFS: Number of bytes written=2900000000
		HDFS: Number of read operations=116
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=58
	Job Counters 
		Failed map tasks=13
		Killed map tasks=70
		Launched map tasks=86
		Other local map tasks=88
		Total time spent by all maps in occupied slots (ms)=3956959
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=3956959
		Total vcore-seconds taken by all map tasks=3956959
		Total megabyte-seconds taken by all map tasks=4051926016
	Map-Reduce Framework
		Map input records=29000000
		Map output records=29000000
		Input split bytes=2480
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=13080
		CPU time spent (ms)=154180
		Physical memory (bytes) snapshot=8049385472
		Virtual memory (bytes) snapshot=45245964288
		Total committed heap usage (bytes)=11468800000
	org.apache.hadoop.examples.terasort.TeraGen$Counters
		CHECKSUM=62286991949275379
	File Input Format Counters 
		Bytes Read=0
	File Output Format Counters 
		Bytes Written=2900000000
```
* i have ended up in filled HDFS (each node has /data/1/ with 100GB disk attached).
