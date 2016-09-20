* http://www.cloudera.com/documentation/enterprise/latest/topics/cm_ig_testing_the_install.html
* run the Pi example:
```
[root@klempa1 ec2-user]# sudo -u hdfs hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar pi 10 100
Number of Maps  = 10
Samples per Map = 100
Wrote input for Map #0
Wrote input for Map #1
Wrote input for Map #2
Wrote input for Map #3
Wrote input for Map #4
Wrote input for Map #5
Wrote input for Map #6
Wrote input for Map #7
Wrote input for Map #8
Wrote input for Map #9
Starting Job
16/09/20 13:27:36 INFO client.RMProxy: Connecting to ResourceManager at klempa1.cdh.seb/172.31.9.86:8032
16/09/20 13:27:36 INFO input.FileInputFormat: Total input paths to process : 10
16/09/20 13:27:36 INFO mapreduce.JobSubmitter: number of splits:10
16/09/20 13:27:36 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1474372773568_0002
16/09/20 13:27:37 INFO impl.YarnClientImpl: Submitted application application_1474372773568_0002
16/09/20 13:27:37 INFO mapreduce.Job: The url to track the job: http://klempa1.cdh.seb:8088/proxy/application_1474372773568_0002/
16/09/20 13:27:37 INFO mapreduce.Job: Running job: job_1474372773568_0002
16/09/20 13:27:42 INFO mapreduce.Job: Job job_1474372773568_0002 running in uber mode : false
16/09/20 13:27:42 INFO mapreduce.Job:  map 0% reduce 0%
16/09/20 13:27:47 INFO mapreduce.Job:  map 10% reduce 0%
16/09/20 13:27:48 INFO mapreduce.Job:  map 30% reduce 0%
16/09/20 13:27:49 INFO mapreduce.Job:  map 50% reduce 0%
16/09/20 13:27:50 INFO mapreduce.Job:  map 60% reduce 0%
16/09/20 13:27:51 INFO mapreduce.Job:  map 100% reduce 0%
16/09/20 13:27:57 INFO mapreduce.Job:  map 100% reduce 100%
16/09/20 13:27:57 INFO mapreduce.Job: Job job_1474372773568_0002 completed successfully
16/09/20 13:27:57 INFO mapreduce.Job: Counters: 50
	File System Counters
		FILE: Number of bytes read=99
		FILE: Number of bytes written=1324729
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=2700
		HDFS: Number of bytes written=215
		HDFS: Number of read operations=43
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=3
	Job Counters 
		Launched map tasks=10
		Launched reduce tasks=1
		Data-local map tasks=9
		Rack-local map tasks=1
		Total time spent by all maps in occupied slots (ms)=44940
		Total time spent by all reduces in occupied slots (ms)=3386
		Total time spent by all map tasks (ms)=44940
		Total time spent by all reduce tasks (ms)=3386
		Total vcore-seconds taken by all map tasks=44940
		Total vcore-seconds taken by all reduce tasks=3386
		Total megabyte-seconds taken by all map tasks=46018560
		Total megabyte-seconds taken by all reduce tasks=3467264
	Map-Reduce Framework
		Map input records=10
		Map output records=20
		Map output bytes=180
		Map output materialized bytes=340
		Input split bytes=1520
		Combine input records=0
		Combine output records=0
		Reduce input groups=2
		Reduce shuffle bytes=340
		Reduce input records=20
		Reduce output records=0
		Spilled Records=40
		Shuffled Maps =10
		Failed Shuffles=0
		Merged Map outputs=10
		GC time elapsed (ms)=284
		CPU time spent (ms)=6220
		Physical memory (bytes) snapshot=4813639680
		Virtual memory (bytes) snapshot=16954798080
		Total committed heap usage (bytes)=5457313792
	Shuffle Errors
		BAD_ID=0
		CONNECTION=0
		IO_ERROR=0
		WRONG_LENGTH=0
		WRONG_MAP=0
		WRONG_REDUCE=0
	File Input Format Counters 
		Bytes Read=1180
	File Output Format Counters 
		Bytes Written=97
Job Finished in 21.42 seconds
Estimated value of Pi is 3.14800000000000000000
```
* locate the hadoop examples
```
[root@klempa1 ec2-user]# locate examples | grep jar | grep hadoop
/opt/cloudera/parcels/CDH-5.8.0-1.cdh5.8.0.p0.42/jars/hadoop-examples-2.6.0-mr1-cdh5.8.0.jar
/opt/cloudera/parcels/CDH-5.8.0-1.cdh5.8.0.p0.42/jars/hadoop-examples.jar
/opt/cloudera/parcels/CDH-5.8.0-1.cdh5.8.0.p0.42/jars/hadoop-mapreduce-examples-2.6.0-cdh5.8.0.jar
```
* run the teragen
```
[root@klempa1 ec2-user]# su - hdfs 
[hdfs@klempa1 ~]$ yarn jar /opt/cloudera/parcels/CDH-5.8.0-1.cdh5.8.0.p0.42/jars/hadoop-mapreduce-examples-*.jar teragen -Dmapreduce.job.maps=50 5000000 /tmp/klempa-teragenout-500MB
16/09/20 14:07:47 INFO client.RMProxy: Connecting to ResourceManager at klempa1.cdh.seb/172.31.9.86:8032
16/09/20 14:07:47 INFO terasort.TeraSort: Generating 5000000 using 50
16/09/20 14:07:47 INFO mapreduce.JobSubmitter: number of splits:50
16/09/20 14:07:48 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1474372773568_0003
16/09/20 14:07:48 INFO impl.YarnClientImpl: Submitted application application_1474372773568_0003
16/09/20 14:07:48 INFO mapreduce.Job: The url to track the job: http://klempa1.cdh.seb:8088/proxy/application_1474372773568_0003/
16/09/20 14:07:48 INFO mapreduce.Job: Running job: job_1474372773568_0003
16/09/20 14:07:53 INFO mapreduce.Job: Job job_1474372773568_0003 running in uber mode : false
16/09/20 14:07:53 INFO mapreduce.Job:  map 0% reduce 0%
16/09/20 14:07:59 INFO mapreduce.Job:  map 4% reduce 0%
16/09/20 14:08:00 INFO mapreduce.Job:  map 6% reduce 0%
16/09/20 14:08:01 INFO mapreduce.Job:  map 10% reduce 0%
16/09/20 14:08:03 INFO mapreduce.Job:  map 16% reduce 0%
16/09/20 14:08:04 INFO mapreduce.Job:  map 20% reduce 0%
16/09/20 14:08:05 INFO mapreduce.Job:  map 22% reduce 0%
16/09/20 14:08:08 INFO mapreduce.Job:  map 28% reduce 0%
16/09/20 14:08:09 INFO mapreduce.Job:  map 30% reduce 0%
16/09/20 14:08:10 INFO mapreduce.Job:  map 32% reduce 0%
16/09/20 14:08:11 INFO mapreduce.Job:  map 34% reduce 0%
16/09/20 14:08:12 INFO mapreduce.Job:  map 38% reduce 0%
16/09/20 14:08:13 INFO mapreduce.Job:  map 40% reduce 0%
16/09/20 14:08:14 INFO mapreduce.Job:  map 42% reduce 0%
16/09/20 14:08:15 INFO mapreduce.Job:  map 48% reduce 0%
16/09/20 14:08:18 INFO mapreduce.Job:  map 50% reduce 0%
16/09/20 14:08:19 INFO mapreduce.Job:  map 58% reduce 0%
16/09/20 14:08:20 INFO mapreduce.Job:  map 60% reduce 0%
16/09/20 14:08:21 INFO mapreduce.Job:  map 64% reduce 0%
16/09/20 14:08:23 INFO mapreduce.Job:  map 66% reduce 0%
16/09/20 14:08:24 INFO mapreduce.Job:  map 70% reduce 0%
16/09/20 14:08:26 INFO mapreduce.Job:  map 72% reduce 0%
16/09/20 14:08:27 INFO mapreduce.Job:  map 78% reduce 0%
16/09/20 14:08:28 INFO mapreduce.Job:  map 84% reduce 0%
16/09/20 14:08:29 INFO mapreduce.Job:  map 86% reduce 0%
16/09/20 14:08:33 INFO mapreduce.Job:  map 94% reduce 0%
16/09/20 14:08:36 INFO mapreduce.Job:  map 100% reduce 0%
16/09/20 14:08:38 INFO mapreduce.Job: Job job_1474372773568_0003 completed successfully
16/09/20 14:08:38 INFO mapreduce.Job: Counters: 31
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=5987090
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=4247
		HDFS: Number of bytes written=500000000
		HDFS: Number of read operations=200
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=100
	Job Counters 
		Launched map tasks=50
		Other local map tasks=50
		Total time spent by all maps in occupied slots (ms)=260920
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=260920
		Total vcore-seconds taken by all map tasks=260920
		Total megabyte-seconds taken by all map tasks=267182080
	Map-Reduce Framework
		Map input records=5000000
		Map output records=5000000
		Input split bytes=4247
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=2670
		CPU time spent (ms)=105740
		Physical memory (bytes) snapshot=10253381632
		Virtual memory (bytes) snapshot=76824985600
		Total committed heap usage (bytes)=14769192960
	org.apache.hadoop.examples.terasort.TeraGen$Counters
		CHECKSUM=10735710707299981
	File Input Format Counters 
		Bytes Read=0
	File Output Format Counters 
		Bytes Written=500000000
```
* lets try the list files on colleague's cluster
```
[hdfs@klempa1 ~]$ hdfs dfs -ls hdfs://172.31.13.166:8020/
Found 2 items
drwxrwxrwt   - hdfs supergroup          0 2016-09-20 13:28 hdfs://172.31.13.166:8020/tmp
drwxr-xr-x   - hdfs supergroup          0 2016-09-20 09:53 hdfs://172.31.13.166:8020/user
```
* use distcp http://hadoop.apache.org/docs/stable/hadoop-distcp/DistCp.html
```
[hdfs@klempa1 ~]$ hadoop distcp hdfs://172.31.13.166:8020/tmp/cuper-teragenout-500MB /tmp/
16/09/20 14:15:38 INFO tools.DistCp: Input Options: DistCpOptions{atomicCommit=false, syncFolder=false, deleteMissing=false, ignoreFailures=false, overwrite=false, skipCRC=false, blocking=true, numListstatusThreads=0, maxMaps=20, mapBandwidth=100, sslConfigurationFile='null', copyStrategy='uniformsize', preserveStatus=[], preserveRawXattrs=false, atomicWorkPath=null, logPath=null, sourceFileListing=null, sourcePaths=[hdfs://172.31.13.166:8020/tmp/cuper-teragenout-500MB], targetPath=/tmp, targetPathExists=true, filtersFile='null'}
16/09/20 14:15:38 INFO client.RMProxy: Connecting to ResourceManager at klempa1.cdh.seb/172.31.9.86:8032
16/09/20 14:15:39 INFO tools.SimpleCopyListing: Paths (files+dirs) cnt = 50; dirCnt = 1
16/09/20 14:15:39 INFO tools.SimpleCopyListing: Build file listing completed.
16/09/20 14:15:39 INFO Configuration.deprecation: io.sort.mb is deprecated. Instead, use mapreduce.task.io.sort.mb
16/09/20 14:15:39 INFO Configuration.deprecation: io.sort.factor is deprecated. Instead, use mapreduce.task.io.sort.factor
16/09/20 14:15:39 INFO tools.DistCp: Number of paths in the copy list: 50
16/09/20 14:15:39 INFO tools.DistCp: Number of paths in the copy list: 50
16/09/20 14:15:39 INFO client.RMProxy: Connecting to ResourceManager at klempa1.cdh.seb/172.31.9.86:8032
16/09/20 14:15:39 INFO mapreduce.JobSubmitter: number of splits:24
16/09/20 14:15:39 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1474372773568_0004
16/09/20 14:15:40 INFO impl.YarnClientImpl: Submitted application application_1474372773568_0004
16/09/20 14:15:40 INFO mapreduce.Job: The url to track the job: http://klempa1.cdh.seb:8088/proxy/application_1474372773568_0004/
16/09/20 14:15:40 INFO tools.DistCp: DistCp job-id: job_1474372773568_0004
16/09/20 14:15:40 INFO mapreduce.Job: Running job: job_1474372773568_0004
16/09/20 14:15:46 INFO mapreduce.Job: Job job_1474372773568_0004 running in uber mode : false
16/09/20 14:15:46 INFO mapreduce.Job:  map 0% reduce 0%
16/09/20 14:15:52 INFO mapreduce.Job:  map 8% reduce 0%
16/09/20 14:15:53 INFO mapreduce.Job:  map 13% reduce 0%
16/09/20 14:15:54 INFO mapreduce.Job:  map 21% reduce 0%
16/09/20 14:15:55 INFO mapreduce.Job:  map 33% reduce 0%
16/09/20 14:15:57 INFO mapreduce.Job:  map 46% reduce 0%
16/09/20 14:16:00 INFO mapreduce.Job:  map 54% reduce 0%
16/09/20 14:16:01 INFO mapreduce.Job:  map 63% reduce 0%
16/09/20 14:16:02 INFO mapreduce.Job:  map 67% reduce 0%
16/09/20 14:16:03 INFO mapreduce.Job:  map 75% reduce 0%
16/09/20 14:16:04 INFO mapreduce.Job:  map 79% reduce 0%
16/09/20 14:16:06 INFO mapreduce.Job:  map 92% reduce 0%
16/09/20 14:16:07 INFO mapreduce.Job:  map 100% reduce 0%
16/09/20 14:16:08 INFO mapreduce.Job: Job job_1474372773568_0004 completed successfully
16/09/20 14:16:08 INFO mapreduce.Job: Counters: 33
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=2941094
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=500019316
		HDFS: Number of bytes written=500000000
		HDFS: Number of read operations=731
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=148
	Job Counters 
		Launched map tasks=24
		Other local map tasks=24
		Total time spent by all maps in occupied slots (ms)=125515
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=125515
		Total vcore-seconds taken by all map tasks=125515
		Total megabyte-seconds taken by all map tasks=128527360
	Map-Reduce Framework
		Map input records=50
		Map output records=0
		Input split bytes=2760
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=1278
		CPU time spent (ms)=51990
		Physical memory (bytes) snapshot=4872667136
		Virtual memory (bytes) snapshot=36858863616
		Total committed heap usage (bytes)=7117209600
	File Input Format Counters 
		Bytes Read=16556
	File Output Format Counters 
		Bytes Written=0
	org.apache.hadoop.tools.mapred.CopyMapper$Counter
		BYTESCOPIED=500000000
		BYTESEXPECTED=500000000
		COPY=50
```
* check the result
```
[hdfs@klempa1 ~]$ hdfs dfs -ls /tmp/cuper-teragenout-500MB
Found 49 items
-rw-r--r--   3 hdfs supergroup          0 2016-09-20 14:15 /tmp/cuper-teragenout-500MB/_SUCCESS
-rw-r--r--   3 hdfs supergroup   10416700 2016-09-20 14:15 /tmp/cuper-teragenout-500MB/part-m-00000
-rw-r--r--   3 hdfs supergroup   10416700 2016-09-20 14:15 /tmp/cuper-teragenout-500MB/part-m-00001
-rw-r--r--   3 hdfs supergroup   10416600 2016-09-20 14:15 /tmp/cuper-teragenout-500MB/part-m-00002
-rw-r--r--   3 hdfs supergroup   10416700 2016-09-20 14:15 /tmp/cuper-teragenout-500MB/part-m-00003
-rw-r--r--   3 hdfs supergroup   10416700 2016-09-20 14:15 /tmp/cuper-teragenout-500MB/part-m-00004
-rw-r--r--   3 hdfs supergroup   10416600 2016-09-20 14:15 /tmp/cuper-teragenout-500MB/part-m-00005
-rw-r--r--   3 hdfs supergroup   10416700 2016-09-20 14:15 /tmp/cuper-teragenout-500MB/part-m-00006
-rw-r--r--   3 hdfs supergroup   10416700 2016-09-20 14:15 /tmp/cuper-teragenout-500MB/part-m-00007
-rw-r--r--   3 hdfs supergroup   10416600 2016-09-20 14:15 /tmp/cuper-teragenout-500MB/part-m-00008
-rw-r--r--   3 hdfs supergroup   10416700 2016-09-20 14:15 /tmp/cuper-teragenout-500MB/part-m-00009
-rw-r--r--   3 hdfs supergroup   10416700 2016-09-20 14:15 /tmp/cuper-teragenout-500MB/part-m-00010
-rw-r--r--   3 hdfs supergroup   10416600 2016-09-20 14:15 /tmp/cuper-teragenout-500MB/part-m-00011
-rw-r--r--   3 hdfs supergroup   10416700 2016-09-20 14:15 /tmp/cuper-teragenout-500MB/part-m-00012
-rw-r--r--   3 hdfs supergroup   10416700 2016-09-20 14:15 /tmp/cuper-teragenout-500MB/part-m-00013
-rw-r--r--   3 hdfs supergroup   10416600 2016-09-20 14:15 /tmp/cuper-teragenout-500MB/part-m-00014
-rw-r--r--   3 hdfs supergroup   10416700 2016-09-20 14:15 /tmp/cuper-teragenout-500MB/part-m-00015
-rw-r--r--   3 hdfs supergroup   10416700 2016-09-20 14:15 /tmp/cuper-teragenout-500MB/part-m-00016
-rw-r--r--   3 hdfs supergroup   10416600 2016-09-20 14:15 /tmp/cuper-teragenout-500MB/part-m-00017
-rw-r--r--   3 hdfs supergroup   10416700 2016-09-20 14:15 /tmp/cuper-teragenout-500MB/part-m-00018
-rw-r--r--   3 hdfs supergroup   10416700 2016-09-20 14:15 /tmp/cuper-teragenout-500MB/part-m-00019
-rw-r--r--   3 hdfs supergroup   10416600 2016-09-20 14:15 /tmp/cuper-teragenout-500MB/part-m-00020
-rw-r--r--   3 hdfs supergroup   10416700 2016-09-20 14:15 /tmp/cuper-teragenout-500MB/part-m-00021
-rw-r--r--   3 hdfs supergroup   10416700 2016-09-20 14:15 /tmp/cuper-teragenout-500MB/part-m-00022
-rw-r--r--   3 hdfs supergroup   10416600 2016-09-20 14:15 /tmp/cuper-teragenout-500MB/part-m-00023
-rw-r--r--   3 hdfs supergroup   10416700 2016-09-20 14:15 /tmp/cuper-teragenout-500MB/part-m-00024
-rw-r--r--   3 hdfs supergroup   10416700 2016-09-20 14:15 /tmp/cuper-teragenout-500MB/part-m-00025
-rw-r--r--   3 hdfs supergroup   10416600 2016-09-20 14:16 /tmp/cuper-teragenout-500MB/part-m-00026
-rw-r--r--   3 hdfs supergroup   10416700 2016-09-20 14:16 /tmp/cuper-teragenout-500MB/part-m-00027
-rw-r--r--   3 hdfs supergroup   10416700 2016-09-20 14:16 /tmp/cuper-teragenout-500MB/part-m-00028
-rw-r--r--   3 hdfs supergroup   10416600 2016-09-20 14:16 /tmp/cuper-teragenout-500MB/part-m-00029
-rw-r--r--   3 hdfs supergroup   10416700 2016-09-20 14:16 /tmp/cuper-teragenout-500MB/part-m-00030
-rw-r--r--   3 hdfs supergroup   10416700 2016-09-20 14:16 /tmp/cuper-teragenout-500MB/part-m-00031
-rw-r--r--   3 hdfs supergroup   10416600 2016-09-20 14:15 /tmp/cuper-teragenout-500MB/part-m-00032
-rw-r--r--   3 hdfs supergroup   10416700 2016-09-20 14:16 /tmp/cuper-teragenout-500MB/part-m-00033
-rw-r--r--   3 hdfs supergroup   10416700 2016-09-20 14:15 /tmp/cuper-teragenout-500MB/part-m-00034
-rw-r--r--   3 hdfs supergroup   10416600 2016-09-20 14:16 /tmp/cuper-teragenout-500MB/part-m-00035
-rw-r--r--   3 hdfs supergroup   10416700 2016-09-20 14:16 /tmp/cuper-teragenout-500MB/part-m-00036
-rw-r--r--   3 hdfs supergroup   10416700 2016-09-20 14:16 /tmp/cuper-teragenout-500MB/part-m-00037
-rw-r--r--   3 hdfs supergroup   10416600 2016-09-20 14:16 /tmp/cuper-teragenout-500MB/part-m-00038
-rw-r--r--   3 hdfs supergroup   10416700 2016-09-20 14:16 /tmp/cuper-teragenout-500MB/part-m-00039
-rw-r--r--   3 hdfs supergroup   10416700 2016-09-20 14:16 /tmp/cuper-teragenout-500MB/part-m-00040
-rw-r--r--   3 hdfs supergroup   10416600 2016-09-20 14:16 /tmp/cuper-teragenout-500MB/part-m-00041
-rw-r--r--   3 hdfs supergroup   10416700 2016-09-20 14:16 /tmp/cuper-teragenout-500MB/part-m-00042
-rw-r--r--   3 hdfs supergroup   10416700 2016-09-20 14:16 /tmp/cuper-teragenout-500MB/part-m-00043
-rw-r--r--   3 hdfs supergroup   10416600 2016-09-20 14:16 /tmp/cuper-teragenout-500MB/part-m-00044
-rw-r--r--   3 hdfs supergroup   10416700 2016-09-20 14:16 /tmp/cuper-teragenout-500MB/part-m-00045
-rw-r--r--   3 hdfs supergroup   10416700 2016-09-20 14:16 /tmp/cuper-teragenout-500MB/part-m-00046
-rw-r--r--   3 hdfs supergroup   10416600 2016-09-20 14:16 /tmp/cuper-teragenout-500MB/part-m-00047
```
* generate 10GB with <128MB files
```
[hdfs@klempa1 ~]$ yarn jar /opt/cloudera/parcels/CDH-5.8.0-1.cdh5.8.0.p0.42/jars/hadoop-mapreduce-examples-*.jar teragen -Dmapreduce.job.maps=90 100000000 /tmp/klempa-teragenout-10GB
16/09/20 14:25:29 INFO client.RMProxy: Connecting to ResourceManager at klempa1.cdh.seb/172.31.9.86:8032
16/09/20 14:25:30 INFO terasort.TeraSort: Generating 100000000 using 90
16/09/20 14:25:30 INFO mapreduce.JobSubmitter: number of splits:90
16/09/20 14:25:30 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1474372773568_0005
16/09/20 14:25:30 INFO impl.YarnClientImpl: Submitted application application_1474372773568_0005
16/09/20 14:25:30 INFO mapreduce.Job: The url to track the job: http://klempa1.cdh.seb:8088/proxy/application_1474372773568_0005/
16/09/20 14:25:30 INFO mapreduce.Job: Running job: job_1474372773568_0005
16/09/20 14:25:36 INFO mapreduce.Job: Job job_1474372773568_0005 running in uber mode : false
16/09/20 14:25:36 INFO mapreduce.Job:  map 0% reduce 0%
16/09/20 14:25:43 INFO mapreduce.Job:  map 2% reduce 0%
16/09/20 14:25:44 INFO mapreduce.Job:  map 3% reduce 0%
16/09/20 14:25:46 INFO mapreduce.Job:  map 6% reduce 0%
16/09/20 14:25:48 INFO mapreduce.Job:  map 9% reduce 0%
16/09/20 14:25:49 INFO mapreduce.Job:  map 10% reduce 0%
16/09/20 14:25:50 INFO mapreduce.Job:  map 12% reduce 0%
16/09/20 14:25:54 INFO mapreduce.Job:  map 14% reduce 0%
16/09/20 14:25:55 INFO mapreduce.Job:  map 16% reduce 0%
16/09/20 14:25:56 INFO mapreduce.Job:  map 17% reduce 0%
16/09/20 14:25:57 INFO mapreduce.Job:  map 18% reduce 0%
16/09/20 14:26:00 INFO mapreduce.Job:  map 20% reduce 0%
16/09/20 14:26:01 INFO mapreduce.Job:  map 21% reduce 0%
16/09/20 14:26:05 INFO mapreduce.Job:  map 23% reduce 0%
16/09/20 14:26:15 INFO mapreduce.Job:  map 24% reduce 0%
16/09/20 14:26:17 INFO mapreduce.Job:  map 25% reduce 0%
16/09/20 14:26:18 INFO mapreduce.Job:  map 26% reduce 0%
16/09/20 14:26:26 INFO mapreduce.Job:  map 29% reduce 0%
16/09/20 14:26:27 INFO mapreduce.Job:  map 30% reduce 0%
16/09/20 14:26:28 INFO mapreduce.Job:  map 31% reduce 0%
16/09/20 14:26:29 INFO mapreduce.Job:  map 33% reduce 0%
16/09/20 14:26:37 INFO mapreduce.Job:  map 38% reduce 0%
16/09/20 14:26:39 INFO mapreduce.Job:  map 40% reduce 0%
16/09/20 14:26:44 INFO mapreduce.Job:  map 41% reduce 0%
16/09/20 14:26:45 INFO mapreduce.Job:  map 42% reduce 0%
16/09/20 14:26:50 INFO mapreduce.Job:  map 43% reduce 0%
16/09/20 14:26:57 INFO mapreduce.Job:  map 44% reduce 0%
16/09/20 14:27:01 INFO mapreduce.Job:  map 46% reduce 0%
16/09/20 14:27:02 INFO mapreduce.Job:  map 49% reduce 0%
16/09/20 14:27:04 INFO mapreduce.Job:  map 50% reduce 0%
16/09/20 14:27:11 INFO mapreduce.Job:  map 51% reduce 0%
16/09/20 14:27:12 INFO mapreduce.Job:  map 54% reduce 0%
16/09/20 14:27:18 INFO mapreduce.Job:  map 55% reduce 0%
16/09/20 14:27:23 INFO mapreduce.Job:  map 56% reduce 0%
16/09/20 14:27:24 INFO mapreduce.Job:  map 58% reduce 0%
16/09/20 14:27:26 INFO mapreduce.Job:  map 59% reduce 0%
16/09/20 14:27:29 INFO mapreduce.Job:  map 60% reduce 0%
16/09/20 14:27:36 INFO mapreduce.Job:  map 61% reduce 0%
16/09/20 14:27:37 INFO mapreduce.Job:  map 63% reduce 0%
16/09/20 14:27:42 INFO mapreduce.Job:  map 65% reduce 0%
16/09/20 14:27:43 INFO mapreduce.Job:  map 66% reduce 0%
16/09/20 14:27:49 INFO mapreduce.Job:  map 69% reduce 0%
16/09/20 14:27:56 INFO mapreduce.Job:  map 71% reduce 0%
16/09/20 14:28:01 INFO mapreduce.Job:  map 72% reduce 0%
16/09/20 14:28:05 INFO mapreduce.Job:  map 73% reduce 0%
16/09/20 14:28:06 INFO mapreduce.Job:  map 74% reduce 0%
16/09/20 14:28:08 INFO mapreduce.Job:  map 75% reduce 0%
16/09/20 14:28:10 INFO mapreduce.Job:  map 76% reduce 0%
16/09/20 14:28:15 INFO mapreduce.Job:  map 77% reduce 0%
16/09/20 14:28:16 INFO mapreduce.Job:  map 78% reduce 0%
16/09/20 14:28:22 INFO mapreduce.Job:  map 79% reduce 0%
16/09/20 14:28:26 INFO mapreduce.Job:  map 80% reduce 0%
16/09/20 14:28:31 INFO mapreduce.Job:  map 81% reduce 0%
16/09/20 14:28:33 INFO mapreduce.Job:  map 82% reduce 0%
16/09/20 14:28:34 INFO mapreduce.Job:  map 83% reduce 0%
16/09/20 14:28:37 INFO mapreduce.Job:  map 84% reduce 0%
16/09/20 14:28:40 INFO mapreduce.Job:  map 85% reduce 0%
16/09/20 14:28:43 INFO mapreduce.Job:  map 86% reduce 0%
16/09/20 14:28:48 INFO mapreduce.Job:  map 87% reduce 0%
16/09/20 14:28:50 INFO mapreduce.Job:  map 88% reduce 0%
16/09/20 14:28:55 INFO mapreduce.Job:  map 89% reduce 0%
16/09/20 14:28:57 INFO mapreduce.Job:  map 90% reduce 0%
16/09/20 14:29:09 INFO mapreduce.Job:  map 91% reduce 0%
16/09/20 14:29:13 INFO mapreduce.Job:  map 92% reduce 0%
16/09/20 14:29:14 INFO mapreduce.Job:  map 93% reduce 0%
16/09/20 14:29:19 INFO mapreduce.Job:  map 95% reduce 0%
16/09/20 14:29:21 INFO mapreduce.Job:  map 96% reduce 0%
16/09/20 14:29:24 INFO mapreduce.Job:  map 97% reduce 0%
16/09/20 14:29:28 INFO mapreduce.Job:  map 98% reduce 0%
16/09/20 14:29:47 INFO mapreduce.Job:  map 99% reduce 0%
16/09/20 14:29:51 INFO mapreduce.Job:  map 100% reduce 0%
16/09/20 14:29:52 INFO mapreduce.Job: Job job_1474372773568_0005 completed successfully
16/09/20 14:29:52 INFO mapreduce.Job: Counters: 31
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=10776860
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=7721
		HDFS: Number of bytes written=10000000000
		HDFS: Number of read operations=360
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=180
	Job Counters 
		Launched map tasks=90
		Other local map tasks=90
		Total time spent by all maps in occupied slots (ms)=1777665
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=1777665
		Total vcore-seconds taken by all map tasks=1777665
		Total megabyte-seconds taken by all map tasks=1820328960
	Map-Reduce Framework
		Map input records=100000000
		Map output records=100000000
		Input split bytes=7721
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=7291
		CPU time spent (ms)=368610
		Physical memory (bytes) snapshot=25965510656
		Virtual memory (bytes) snapshot=137807056896
		Total committed heap usage (bytes)=36903583744
	org.apache.hadoop.examples.terasort.TeraGen$Counters
		CHECKSUM=214760662691937609
	File Input Format Counters 
		Bytes Read=0
	File Output Format Counters 
		Bytes Written=10000000000
```
* check the result
```
[hdfs@klempa1 ~]$ hdfs dfs -ls -h /tmp/klempa-teragenout-10GB
Found 91 items
-rw-r--r--   3 hdfs supergroup          0 2016-09-20 14:29 /tmp/klempa-teragenout-10GB/_SUCCESS
-rw-r--r--   3 hdfs supergroup    106.0 M 2016-09-20 14:25 /tmp/klempa-teragenout-10GB/part-m-00000
-rw-r--r--   3 hdfs supergroup    106.0 M 2016-09-20 14:25 /tmp/klempa-teragenout-10GB/part-m-00001
-rw-r--r--   3 hdfs supergroup    106.0 M 2016-09-20 14:25 /tmp/klempa-teragenout-10GB/part-m-00002
```
* check the dfs blocksize there
```
[hdfs@klempa1 ~]$ hdfs dfs -stat "name %n blocksize %o" /tmp/klempa-teragenout-10GB/*
name _SUCCESS blocksize 134217728
name part-m-00000 blocksize 134217728
name part-m-00001 blocksize 134217728
name part-m-00002 blocksize 134217728
name part-m-00003 blocksize 134217728
name part-m-00004 blocksize 134217728
name part-m-00005 blocksize 134217728
name part-m-00006 blocksize 134217728
name part-m-00007 blocksize 134217728
name part-m-00008 blocksize 134217728
name part-m-00009 blocksize 134217728
name part-m-00010 blocksize 134217728
name part-m-00011 blocksize 134217728
name part-m-00012 blocksize 134217728
name part-m-00013 blocksize 134217728
name part-m-00014 blocksize 134217728
```
* wrong value, lets regenerate the data properly
```
[hdfs@klempa1 ~]$ yarn jar /opt/cloudera/parcels/CDH-5.8.0-1.cdh5.8.0.p0.42/jars/hadoop-mapreduce-examples-*.jar teragen -Dmapreduce.job.maps=90 -Ddfs.blocksize=32M 100000000 /tmp/klempa-teragenout-10GB-32M
16/09/20 15:48:06 INFO client.RMProxy: Connecting to ResourceManager at klempa1.cdh.seb/172.31.9.86:8032
16/09/20 15:48:07 INFO terasort.TeraSort: Generating 100000000 using 90
16/09/20 15:48:07 INFO mapreduce.JobSubmitter: number of splits:90
16/09/20 15:48:07 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1474372773568_0006
16/09/20 15:48:07 INFO impl.YarnClientImpl: Submitted application application_1474372773568_0006
16/09/20 15:48:07 INFO mapreduce.Job: The url to track the job: http://klempa1.cdh.seb:8088/proxy/application_1474372773568_0006/
16/09/20 15:48:07 INFO mapreduce.Job: Running job: job_1474372773568_0006
16/09/20 15:48:13 INFO mapreduce.Job: Job job_1474372773568_0006 running in uber mode : false
16/09/20 15:48:13 INFO mapreduce.Job:  map 0% reduce 0%
16/09/20 15:48:21 INFO mapreduce.Job:  map 2% reduce 0%
16/09/20 15:48:22 INFO mapreduce.Job:  map 3% reduce 0%
16/09/20 15:48:23 INFO mapreduce.Job:  map 6% reduce 0%
16/09/20 15:48:26 INFO mapreduce.Job:  map 9% reduce 0%
16/09/20 15:48:27 INFO mapreduce.Job:  map 11% reduce 0%
16/09/20 15:48:28 INFO mapreduce.Job:  map 12% reduce 0%
16/09/20 15:48:35 INFO mapreduce.Job:  map 14% reduce 0%
16/09/20 15:48:36 INFO mapreduce.Job:  map 16% reduce 0%
16/09/20 15:48:38 INFO mapreduce.Job:  map 17% reduce 0%
16/09/20 15:48:40 INFO mapreduce.Job:  map 18% reduce 0%
16/09/20 15:48:56 INFO mapreduce.Job:  map 19% reduce 0%
16/09/20 15:48:59 INFO mapreduce.Job:  map 20% reduce 0%
16/09/20 15:49:04 INFO mapreduce.Job:  map 21% reduce 0%
16/09/20 15:49:11 INFO mapreduce.Job:  map 22% reduce 0%
16/09/20 15:49:15 INFO mapreduce.Job:  map 23% reduce 0%
16/09/20 15:49:18 INFO mapreduce.Job:  map 24% reduce 0%
16/09/20 15:49:25 INFO mapreduce.Job:  map 25% reduce 0%
16/09/20 15:49:36 INFO mapreduce.Job:  map 26% reduce 0%
16/09/20 15:49:45 INFO mapreduce.Job:  map 27% reduce 0%
16/09/20 15:49:47 INFO mapreduce.Job:  map 28% reduce 0%
16/09/20 15:49:57 INFO mapreduce.Job:  map 29% reduce 0%
16/09/20 15:49:58 INFO mapreduce.Job:  map 30% reduce 0%
16/09/20 15:50:01 INFO mapreduce.Job:  map 31% reduce 0%
16/09/20 15:50:09 INFO mapreduce.Job:  map 32% reduce 0%
16/09/20 15:50:17 INFO mapreduce.Job:  map 33% reduce 0%
16/09/20 15:50:18 INFO mapreduce.Job:  map 34% reduce 0%
16/09/20 15:50:23 INFO mapreduce.Job:  map 35% reduce 0%
16/09/20 15:50:30 INFO mapreduce.Job:  map 36% reduce 0%
16/09/20 15:50:32 INFO mapreduce.Job:  map 37% reduce 0%
16/09/20 15:50:46 INFO mapreduce.Job:  map 38% reduce 0%
16/09/20 15:50:56 INFO mapreduce.Job:  map 40% reduce 0%
16/09/20 15:51:02 INFO mapreduce.Job:  map 42% reduce 0%
16/09/20 15:51:12 INFO mapreduce.Job:  map 43% reduce 0%
16/09/20 15:51:17 INFO mapreduce.Job:  map 45% reduce 0%
16/09/20 15:51:23 INFO mapreduce.Job:  map 46% reduce 0%
16/09/20 15:51:25 INFO mapreduce.Job:  map 47% reduce 0%
16/09/20 15:51:29 INFO mapreduce.Job:  map 48% reduce 0%
16/09/20 15:51:30 INFO mapreduce.Job:  map 49% reduce 0%
16/09/20 15:51:31 INFO mapreduce.Job:  map 50% reduce 0%
16/09/20 15:51:40 INFO mapreduce.Job:  map 51% reduce 0%
16/09/20 15:51:45 INFO mapreduce.Job:  map 52% reduce 0%
16/09/20 15:51:51 INFO mapreduce.Job:  map 53% reduce 0%
16/09/20 15:51:57 INFO mapreduce.Job:  map 54% reduce 0%
16/09/20 15:52:03 INFO mapreduce.Job:  map 55% reduce 0%
16/09/20 15:52:06 INFO mapreduce.Job:  map 56% reduce 0%
16/09/20 15:52:08 INFO mapreduce.Job:  map 57% reduce 0%
16/09/20 15:52:09 INFO mapreduce.Job:  map 58% reduce 0%
16/09/20 15:52:18 INFO mapreduce.Job:  map 59% reduce 0%
16/09/20 15:52:20 INFO mapreduce.Job:  map 60% reduce 0%
16/09/20 15:52:21 INFO mapreduce.Job:  map 61% reduce 0%
16/09/20 15:52:24 INFO mapreduce.Job:  map 62% reduce 0%
16/09/20 15:52:34 INFO mapreduce.Job:  map 63% reduce 0%
16/09/20 15:52:38 INFO mapreduce.Job:  map 64% reduce 0%
16/09/20 15:52:48 INFO mapreduce.Job:  map 65% reduce 0%
16/09/20 15:52:50 INFO mapreduce.Job:  map 66% reduce 0%
16/09/20 15:52:58 INFO mapreduce.Job:  map 67% reduce 0%
16/09/20 15:53:00 INFO mapreduce.Job:  map 68% reduce 0%
16/09/20 15:53:06 INFO mapreduce.Job:  map 69% reduce 0%
16/09/20 15:53:08 INFO mapreduce.Job:  map 70% reduce 0%
16/09/20 15:53:18 INFO mapreduce.Job:  map 71% reduce 0%
16/09/20 15:53:28 INFO mapreduce.Job:  map 72% reduce 0%
16/09/20 15:53:29 INFO mapreduce.Job:  map 73% reduce 0%
16/09/20 15:53:39 INFO mapreduce.Job:  map 74% reduce 0%
16/09/20 15:53:47 INFO mapreduce.Job:  map 75% reduce 0%
16/09/20 15:53:53 INFO mapreduce.Job:  map 76% reduce 0%
16/09/20 15:54:03 INFO mapreduce.Job:  map 77% reduce 0%
16/09/20 15:54:14 INFO mapreduce.Job:  map 78% reduce 0%
16/09/20 15:54:20 INFO mapreduce.Job:  map 79% reduce 0%
16/09/20 15:54:29 INFO mapreduce.Job:  map 80% reduce 0%
16/09/20 15:54:34 INFO mapreduce.Job:  map 81% reduce 0%
16/09/20 15:54:35 INFO mapreduce.Job:  map 82% reduce 0%
16/09/20 15:54:36 INFO mapreduce.Job:  map 83% reduce 0%
16/09/20 15:54:41 INFO mapreduce.Job:  map 84% reduce 0%
16/09/20 15:54:44 INFO mapreduce.Job:  map 85% reduce 0%
16/09/20 15:54:47 INFO mapreduce.Job:  map 86% reduce 0%
16/09/20 15:54:49 INFO mapreduce.Job:  map 87% reduce 0%
16/09/20 15:54:50 INFO mapreduce.Job:  map 89% reduce 0%
16/09/20 15:54:52 INFO mapreduce.Job:  map 90% reduce 0%
16/09/20 15:54:58 INFO mapreduce.Job:  map 91% reduce 0%
16/09/20 15:54:59 INFO mapreduce.Job:  map 92% reduce 0%
16/09/20 15:55:02 INFO mapreduce.Job:  map 93% reduce 0%


16/09/20 15:55:09 INFO mapreduce.Job:  map 94% reduce 0%
16/09/20 15:55:12 INFO mapreduce.Job:  map 95% reduce 0%
16/09/20 15:55:15 INFO mapreduce.Job:  map 96% reduce 0%
16/09/20 15:55:23 INFO mapreduce.Job:  map 97% reduce 0%
16/09/20 15:55:31 INFO mapreduce.Job:  map 98% reduce 0%
16/09/20 15:55:33 INFO mapreduce.Job:  map 99% reduce 0%
16/09/20 15:55:40 INFO mapreduce.Job:  map 100% reduce 0%
16/09/20 15:55:42 INFO mapreduce.Job: Job job_1474372773568_0006 completed successfully
16/09/20 15:55:42 INFO mapreduce.Job: Counters: 31
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=10777040
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=7721
		HDFS: Number of bytes written=10000000000
		HDFS: Number of read operations=360
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=180
	Job Counters 
		Launched map tasks=90
		Other local map tasks=90
		Total time spent by all maps in occupied slots (ms)=3365178
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=3365178
		Total vcore-seconds taken by all map tasks=3365178
		Total megabyte-seconds taken by all map tasks=3445942272
	Map-Reduce Framework
		Map input records=100000000
		Map output records=100000000
		Input split bytes=7721
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=6888
		CPU time spent (ms)=368360
		Physical memory (bytes) snapshot=26951770112
		Virtual memory (bytes) snapshot=137827209216
		Total committed heap usage (bytes)=35699294208
	org.apache.hadoop.examples.terasort.TeraGen$Counters
		CHECKSUM=214760662691937609
	File Input Format Counters 
		Bytes Read=0
	File Output Format Counters 
		Bytes Written=10000000000
```
* check the filesizes and block sizes
```
[hdfs@klempa1 ~]$ hdfs dfs -ls -h /tmp/klempa-teragenout-10GB-32M
Found 91 items
-rw-r--r--   3 hdfs supergroup          0 2016-09-20 15:55 /tmp/klempa-teragenout-10GB-32M/_SUCCESS
-rw-r--r--   3 hdfs supergroup    106.0 M 2016-09-20 15:48 /tmp/klempa-teragenout-10GB-32M/part-m-00000
-rw-r--r--   3 hdfs supergroup    106.0 M 2016-09-20 15:48 /tmp/klempa-teragenout-10GB-32M/part-m-00001
-rw-r--r--   3 hdfs supergroup    106.0 M 2016-09-20 15:48 /tmp/klempa-teragenout-10GB-32M/part-m-00002
-rw-r--r--   3 hdfs supergroup    106.0 M 2016-09-20 15:48 /tmp/klempa-teragenout-10GB-32M/part-m-00003
-rw-r--r--   3 hdfs supergroup    106.0 M 2016-09-20 15:48 /tmp/klempa-teragenout-10GB-32M/part-m-00004
```
```
[hdfs@klempa1 ~]$ hdfs dfs -stat "name %n blocksize %o" /tmp/klempa-teragenout-10GB-32M/*
name _SUCCESS blocksize 33554432
name part-m-00000 blocksize 33554432
name part-m-00001 blocksize 33554432
name part-m-00002 blocksize 33554432
name part-m-00003 blocksize 33554432
name part-m-00004 blocksize 33554432
```
* run the sort
```
[hdfs@klempa1 ~]$ time yarn jar /opt/cloudera/parcels/CDH-5.8.0-1.cdh5.8.0.p0.42/jars/hadoop-mapreduce-examples-*.jar terasort -Dmapreduce.job.reduces=10 /tmp/klempa-teragenout-10GB-32M /tmp/klempa-terasortout-10GB-32M
16/09/20 15:59:53 INFO terasort.TeraSort: starting
16/09/20 15:59:54 INFO input.FileInputFormat: Total input paths to process : 90
Spent 306ms computing base-splits.
Spent 6ms computing TeraScheduler splits.
Computing input splits took 313ms
Sampling 10 splits of 360
Making 10 from 100000 sampled records
Computing parititions took 882ms
Spent 1197ms computing partitions.
16/09/20 15:59:55 INFO client.RMProxy: Connecting to ResourceManager at klempa1.cdh.seb/172.31.9.86:8032
16/09/20 15:59:56 INFO mapreduce.JobSubmitter: number of splits:360
16/09/20 15:59:56 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1474372773568_0007
16/09/20 15:59:56 INFO impl.YarnClientImpl: Submitted application application_1474372773568_0007
16/09/20 15:59:56 INFO mapreduce.Job: The url to track the job: http://klempa1.cdh.seb:8088/proxy/application_1474372773568_0007/
16/09/20 15:59:56 INFO mapreduce.Job: Running job: job_1474372773568_0007
16/09/20 16:00:03 INFO mapreduce.Job: Job job_1474372773568_0007 running in uber mode : false
16/09/20 16:00:03 INFO mapreduce.Job:  map 0% reduce 0%

...
16/09/20 16:06:31 INFO mapreduce.Job:  map 100% reduce 65%
16/09/20 16:06:32 INFO mapreduce.Job:  map 100% reduce 67%
16/09/20 16:06:33 INFO mapreduce.Job:  map 100% reduce 68%
16/09/20 16:06:34 INFO mapreduce.Job:  map 100% reduce 69%
16/09/20 16:06:35 INFO mapreduce.Job:  map 100% reduce 77%
16/09/20 16:06:38 INFO mapreduce.Job:  map 100% reduce 84%
16/09/20 16:06:39 INFO mapreduce.Job:  map 100% reduce 88%
16/09/20 16:06:41 INFO mapreduce.Job:  map 100% reduce 90%
16/09/20 16:06:42 INFO mapreduce.Job:  map 100% reduce 91%
16/09/20 16:06:44 INFO mapreduce.Job:  map 100% reduce 94%
16/09/20 16:06:45 INFO mapreduce.Job:  map 100% reduce 95%
16/09/20 16:06:48 INFO mapreduce.Job:  map 100% reduce 96%
16/09/20 16:06:51 INFO mapreduce.Job:  map 100% reduce 97%
16/09/20 16:07:02 INFO mapreduce.Job:  map 100% reduce 98%
16/09/20 16:07:05 INFO mapreduce.Job:  map 100% reduce 99%
16/09/20 16:07:23 INFO mapreduce.Job:  map 100% reduce 100%
16/09/20 16:07:38 INFO mapreduce.Job: Job job_1474372773568_0007 completed successfully
16/09/20 16:07:38 INFO mapreduce.Job: Counters: 49
	File System Counters
		FILE: Number of bytes read=4480894832
		FILE: Number of bytes written=8900286465
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=10000048960
		HDFS: Number of bytes written=10000000000
		HDFS: Number of read operations=1110
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=20
	Job Counters 
		Launched map tasks=360
		Launched reduce tasks=10
		Data-local map tasks=360
		Total time spent by all maps in occupied slots (ms)=2094618
		Total time spent by all reduces in occupied slots (ms)=783842
		Total time spent by all map tasks (ms)=2094618
		Total time spent by all reduce tasks (ms)=783842
		Total vcore-seconds taken by all map tasks=2094618
		Total vcore-seconds taken by all reduce tasks=783842
		Total megabyte-seconds taken by all map tasks=2144888832
		Total megabyte-seconds taken by all reduce tasks=802654208
	Map-Reduce Framework
		Map input records=100000000
		Map output records=100000000
		Map output bytes=10200000000
		Map output materialized bytes=4374518773
		Input split bytes=48960
		Combine input records=0
		Combine output records=0
		Reduce input groups=100000000
		Reduce shuffle bytes=4374518773
		Reduce input records=100000000
		Reduce output records=100000000
		Spilled Records=200000000
		Shuffled Maps =3600
		Failed Shuffles=0
		Merged Map outputs=3600
		GC time elapsed (ms)=34098
		CPU time spent (ms)=1409960
		Physical memory (bytes) snapshot=177901408256
		Virtual memory (bytes) snapshot=567753318400
		Total committed heap usage (bytes)=210128338944
	Shuffle Errors
		BAD_ID=0
		CONNECTION=0
		IO_ERROR=0
		WRONG_LENGTH=0
		WRONG_MAP=0
		WRONG_REDUCE=0
	File Input Format Counters 
		Bytes Read=10000000000
	File Output Format Counters 
		Bytes Written=10000000000
16/09/20 16:07:38 INFO terasort.TeraSort: done

real	7m46.540s
user	0m9.516s
sys	0m0.423s
```
* add the cache
```
[hdfs@klempa1 ~]$ hdfs cacheadmin -addPool testPool
Successfully added cache pool testPool.
```
[hdfs@klempa1 ~]$ hdfs cacheadmin -modifyPool testPool -maxTtl 15m
Successfully modified cache pool testPool to have max time-to-live 15m
[hdfs@klempa1 ~]$ hdfs cacheadmin -addDirective -path /tmp/klempa-teragenout-10GB-32M -pool testPool
Added cache directive 2
[hdfs@klempa1 ~]$  hdfs cacheadmin -listPools -stats testPool
Found 1 result.
NAME      OWNER  GROUP  MODE            LIMIT            MAXTTL  BYTES_NEEDED  BYTES_CACHED  BYTES_OVERLIMIT  FILES_NEEDED  FILES_CACHED
testPool  hdfs   hdfs   rwxr-xr-x   unlimited  000:00:15:00.000   10000000000             0                0            91             1

[hdfs@klempa1 ~]$ time yarn jar /opt/cloudera/parcels/CDH-5.8.0-1.cdh5.8.0.p0.42/jars/hadoop-mapreduce-examples-*.jar terasort -Dmapreduce.job.reduces=10 /tmp/klempa-teragenout-10GB-32M /tmp/klempa-terasortout-10GB-32M-2
16/09/20 16:13:47 INFO terasort.TeraSort: starting
16/09/20 16:13:48 INFO input.FileInputFormat: Total input paths to process : 90
Spent 277ms computing base-splits.
Spent 5ms computing TeraScheduler splits.
Computing input splits took 282ms
Sampling 10 splits of 360
Making 10 from 100000 sampled records
Computing parititions took 693ms
Spent 977ms computing partitions.
16/09/20 16:13:49 INFO client.RMProxy: Connecting to ResourceManager at klempa1.cdh.seb/172.31.9.86:8032
16/09/20 16:13:50 INFO mapreduce.JobSubmitter: number of splits:360
16/09/20 16:13:50 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1474372773568_0008
16/09/20 16:13:50 INFO impl.YarnClientImpl: Submitted application application_1474372773568_0008
16/09/20 16:13:50 INFO mapreduce.Job: The url to track the job: http://klempa1.cdh.seb:8088/proxy/application_1474372773568_0008/
16/09/20 16:13:50 INFO mapreduce.Job: Running job: job_1474372773568_0008
16/09/20 16:13:56 INFO mapreduce.Job: Job job_1474372773568_0008 running in uber mode : false
16/09/20 16:13:56 INFO mapreduce.Job:  map 0% reduce 0%
16/09/20 16:14:03 INFO mapreduce.Job:  map 1% reduce 0%
16/09/20 16:14:06 INFO mapreduce.Job:  map 2% reduce 0%
16/09/20 16:14:08 INFO mapreduce.Job:  map 3% reduce 0%
16/09/20 16:14:13 INFO mapreduce.Job:  map 4% reduce 0%
16/09/20 16:14:15 INFO mapreduce.Job:  map 5% reduce 0%
16/09/20 16:14:20 INFO mapreduce.Job:  map 6% reduce 0%
16/09/20 16:14:21 INFO mapreduce.Job:  map 7% reduce 0%
16/09/20 16:14:26 INFO mapreduce.Job:  map 8% reduce 0%
16/09/20 16:14:28 INFO mapreduce.Job:  map 9% reduce 0%
16/09/20 16:14:33 INFO mapreduce.Job:  map 10% reduce 0%
16/09/20 16:22:13 INFO mapreduce.Job:  map 100% reduce 98%
16/09/20 16:22:19 INFO mapreduce.Job:  map 100% reduce 99%
16/09/20 16:22:22 INFO mapreduce.Job:  map 100% reduce 100%
16/09/20 16:22:29 INFO mapreduce.Job: Job job_1474372773568_0008 completed successfully
16/09/20 16:22:29 INFO mapreduce.Job: Counters: 50
	File System Counters
		FILE: Number of bytes read=4480191667
		FILE: Number of bytes written=8899584780
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=10000048960
		HDFS: Number of bytes written=10000000000
		HDFS: Number of read operations=1110
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=20
	Job Counters 
		Launched map tasks=360
		Launched reduce tasks=10
		Data-local map tasks=354
		Rack-local map tasks=6
		Total time spent by all maps in occupied slots (ms)=2196047
		Total time spent by all reduces in occupied slots (ms)=1002310
		Total time spent by all map tasks (ms)=2196047
		Total time spent by all reduce tasks (ms)=1002310
		Total vcore-seconds taken by all map tasks=2196047
		Total vcore-seconds taken by all reduce tasks=1002310
		Total megabyte-seconds taken by all map tasks=2248752128
		Total megabyte-seconds taken by all reduce tasks=1026365440
	Map-Reduce Framework
		Map input records=100000000
		Map output records=100000000
		Map output bytes=10200000000
		Map output materialized bytes=4374518773
		Input split bytes=48960
		Combine input records=0
		Combine output records=0
		Reduce input groups=100000000
		Reduce shuffle bytes=4374518773
		Reduce input records=100000000
		Reduce output records=100000000
		Spilled Records=200000000
		Shuffled Maps =3600
		Failed Shuffles=0
		Merged Map outputs=3600
		GC time elapsed (ms)=34200
		CPU time spent (ms)=1419600
		Physical memory (bytes) snapshot=177772171264
		Virtual memory (bytes) snapshot=568054235136
		Total committed heap usage (bytes)=210192302080
	Shuffle Errors
		BAD_ID=0
		CONNECTION=0
		IO_ERROR=0
		WRONG_LENGTH=0
		WRONG_MAP=0
		WRONG_REDUCE=0
	File Input Format Counters 
		Bytes Read=10000000000
	File Output Format Counters 
		Bytes Written=10000000000
16/09/20 16:22:29 INFO terasort.TeraSort: done

real	8m43.098s
user	0m9.102s
sys	0m0.407s
* higher running time, some gotchas - ulimit -l, dfs.datanode.max.locked.memory
```
echo hdfs - memlock 10000000 >> /etc/security/limits.conf
```
adjusted dfs.datanode.max.locked.memory using CM, see !(screenshot)[dfs.datanode.max.locked.memory.png]. Restarted datanodes.
* setting up cache using cacheadmin
```
[hdfs@klempa1 ~]$ hdfs cacheadmin -addPool testPool
[hdfs@klempa1 ~]$ hdfs cacheadmin -addDirective -path /tmp/klempa-terasortout-10GB-32M-1 -pool testPool
Added cache directive 7
[hdfs@klempa1 ~]$  hdfs cacheadmin -listPools -stats testPool
Found 1 result.
NAME      OWNER  GROUP  MODE            LIMIT  MAXTTL  BYTES_NEEDED  BYTES_CACHED  BYTES_OVERLIMIT  FILES_NEEDED  FILES_CACHED
testPool  hdfs   hdfs   rwxr-xr-x   unlimited   never   10000000099   10000000099                0            12            12
```
* During job running the we check memlock values for data node:
```
[root@klempa1 ec2-user]# ps ufax | grep DataNode
root      9216  0.0  0.0 103320   852 pts/2    S+   17:47   0:00                          \_ grep DataNode
hdfs     26096  2.3  7.4 1674072 1134680 ?     SLl  17:00   1:07  \_ /usr/java/jdk1.7.0_67-cloudera/bin/java -Dproc_datanode -Xmx1000m -Dhdfs.audit.logger=INFO,RFAAUDIT -Dsecurity.audit.logger=INFO,RFAS -Djava.net.preferIPv4Stack=true -Dhadoop.log.dir=/var/log/hadoop-hdfs -Dhadoop.log.file=hadoop-cmf-hdfs-DATANODE-klempa1.cdh.seb.log.out -Dhadoop.home.dir=/opt/cloudera/parcels/CDH-5.8.0-1.cdh5.8.0.p0.42/lib/hadoop -Dhadoop.id.str=hdfs -Dhadoop.root.logger=INFO,RFA -Djava.library.path=/opt/cloudera/parcels/CDH-5.8.0-1.cdh5.8.0.p0.42/lib/hadoop/lib/native -Dhadoop.policy.file=hadoop-policy.xml -Djava.net.preferIPv4Stack=true -server -Xms52428800 -Xmx52428800 -XX:+UseParNewGC -XX:+UseConcMarkSweepGC -XX:CMSInitiatingOccupancyFraction=70 -XX:+CMSParallelRemarkEnabled -XX:OnOutOfMemoryError=/usr/lib64/cmf/service/common/killparent.sh -Dhadoop.security.logger=INFO,RFAS org.apache.hadoop.hdfs.server.datanode.DataNode
[root@klempa1 ec2-user]# cat /proc/26096/status | grep VmLck
VmLck:	  972720 kB
```
* even after getting the conf right, terasort cant run faster. lets focus on some reading test (teravalidate)
```
[hdfs@klempa1 ~]$ time yarn jar /opt/cloudera/parcels/CDH-5.8.0-1.cdh5.8.0.p0.42/jars/hadoop-mapreduce-examples-*.jar terasort -Dmapreduce.job.reduces=10 /tmp/klempa-teragenout-10GB-32M /tmp/klempa-terasortout-10GB-32M-1
16/09/20 17:17:02 INFO terasort.TeraSort: starting
16/09/20 17:17:04 INFO input.FileInputFormat: Total input paths to process : 90
Spent 365ms computing base-splits.
Spent 8ms computing TeraScheduler splits.
Computing input splits took 373ms
Sampling 10 splits of 360
Making 10 from 100000 sampled records
Computing parititions took 835ms
Spent 1212ms computing partitions.
16/09/20 17:17:05 INFO client.RMProxy: Connecting to ResourceManager at klempa1.cdh.seb/172.31.9.86:8032
16/09/20 17:17:06 INFO mapreduce.JobSubmitter: number of splits:360
16/09/20 17:17:06 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1474405253698_0002
16/09/20 17:17:06 INFO impl.YarnClientImpl: Submitted application application_1474405253698_0002
16/09/20 17:17:06 INFO mapreduce.Job: The url to track the job: http://klempa1.cdh.seb:8088/proxy/application_1474405253698_0002/
16/09/20 17:17:06 INFO mapreduce.Job: Running job: job_1474405253698_0002
16/09/20 17:17:13 INFO mapreduce.Job: Job job_1474405253698_0002 running in uber mode : false
16/09/20 17:17:13 INFO mapreduce.Job:  map 0% reduce 0%
16/09/20 17:17:20 INFO mapreduce.Job:  map 1% reduce 0%
16/09/20 17:17:23 INFO mapreduce.Job:  map 2% reduce 0%
16/09/20 17:17:26 INFO mapreduce.Job:  map 3% reduce 0%
16/09/20 17:17:30 INFO mapreduce.Job:  map 4% reduce 0%
16/09/20 17:17:34 INFO mapreduce.Job:  map 5% reduce 0%
16/09/20 17:24:55 INFO mapreduce.Job:  map 100% reduce 100%
16/09/20 17:24:55 INFO mapreduce.Job: Job job_1474405253698_0002 completed successfully
16/09/20 17:24:55 INFO mapreduce.Job: Counters: 49
	File System Counters
		FILE: Number of bytes read=4481669679
		FILE: Number of bytes written=8901062792
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=10000048960
		HDFS: Number of bytes written=10000000000
		HDFS: Number of read operations=1110
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=20
	Job Counters 
		Launched map tasks=360
		Launched reduce tasks=10
		Data-local map tasks=360
		Total time spent by all maps in occupied slots (ms)=2106332
		Total time spent by all reduces in occupied slots (ms)=817512
		Total time spent by all map tasks (ms)=2106332
		Total time spent by all reduce tasks (ms)=817512
		Total vcore-seconds taken by all map tasks=2106332
		Total vcore-seconds taken by all reduce tasks=817512
		Total megabyte-seconds taken by all map tasks=2156883968
		Total megabyte-seconds taken by all reduce tasks=837132288
	Map-Reduce Framework
		Map input records=100000000
		Map output records=100000000
		Map output bytes=10200000000
		Map output materialized bytes=4374518773
		Input split bytes=48960
		Combine input records=0
		Combine output records=0
		Reduce input groups=100000000
		Reduce shuffle bytes=4374518773
		Reduce input records=100000000
		Reduce output records=100000000
		Spilled Records=200000000
		Shuffled Maps =3600
		Failed Shuffles=0
		Merged Map outputs=3600
		GC time elapsed (ms)=34874
		CPU time spent (ms)=1441260
		Physical memory (bytes) snapshot=176400408576
		Virtual memory (bytes) snapshot=567978663936
		Total committed heap usage (bytes)=210155601920
	Shuffle Errors
		BAD_ID=0
		CONNECTION=0
		IO_ERROR=0
		WRONG_LENGTH=0
		WRONG_MAP=0
		WRONG_REDUCE=0
	File Input Format Counters 
		Bytes Read=10000000000
	File Output Format Counters 
		Bytes Written=10000000000
16/09/20 17:24:55 INFO terasort.TeraSort: done

real	7m53.850s
user	0m9.473s
sys	0m0.466s
```
* we have executed teravalidate, times:
```
real	0m43.543s
user	0m5.294s
sys	0m0.265s
```
* after adding terasort result to cache, validate improves a little bit:
```
[hdfs@klempa1 ~]$ time yarn jar /opt/cloudera/parcels/CDH-5.8.0-1.cdh5.8.0.p0.42/jars/hadoop-mapreduce-examples-*.jar teravalidate -Dmapreduce.job.reduces=10 /tmp/klempa-terasortout-10GB-32M-1 /tmp/klempa-teravalidateout-2
16/09/20 17:31:52 INFO client.RMProxy: Connecting to ResourceManager at klempa1.cdh.seb/172.31.9.86:8032
16/09/20 17:31:52 INFO input.FileInputFormat: Total input paths to process : 10
Spent 36ms computing base-splits.
Spent 2ms computing TeraScheduler splits.
16/09/20 17:31:52 INFO mapreduce.JobSubmitter: number of splits:10
16/09/20 17:31:53 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1474405253698_0004
16/09/20 17:31:53 INFO impl.YarnClientImpl: Submitted application application_1474405253698_0004
16/09/20 17:31:53 INFO mapreduce.Job: The url to track the job: http://klempa1.cdh.seb:8088/proxy/application_1474405253698_0004/
16/09/20 17:31:53 INFO mapreduce.Job: Running job: job_1474405253698_0004
16/09/20 17:31:59 INFO mapreduce.Job: Job job_1474405253698_0004 running in uber mode : false
16/09/20 17:31:59 INFO mapreduce.Job:  map 0% reduce 0%
16/09/20 17:32:10 INFO mapreduce.Job:  map 14% reduce 0%
16/09/20 17:32:11 INFO mapreduce.Job:  map 23% reduce 0%
16/09/20 17:32:12 INFO mapreduce.Job:  map 42% reduce 0%
16/09/20 17:32:13 INFO mapreduce.Job:  map 52% reduce 0%
16/09/20 17:32:14 INFO mapreduce.Job:  map 58% reduce 0%
16/09/20 17:32:15 INFO mapreduce.Job:  map 64% reduce 0%
16/09/20 17:32:16 INFO mapreduce.Job:  map 68% reduce 0%
16/09/20 17:32:19 INFO mapreduce.Job:  map 80% reduce 0%
16/09/20 17:32:21 INFO mapreduce.Job:  map 85% reduce 0%
16/09/20 17:32:23 INFO mapreduce.Job:  map 95% reduce 0%
16/09/20 17:32:25 INFO mapreduce.Job:  map 100% reduce 0%
16/09/20 17:32:26 INFO mapreduce.Job:  map 100% reduce 100%
16/09/20 17:32:26 INFO mapreduce.Job: Job job_1474405253698_0004 completed successfully
16/09/20 17:32:26 INFO mapreduce.Job: Counters: 49
	File System Counters
		FILE: Number of bytes read=570
		FILE: Number of bytes written=1323114
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=10000001390
		HDFS: Number of bytes written=25
		HDFS: Number of read operations=33
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=2
	Job Counters 
		Launched map tasks=10
		Launched reduce tasks=1
		Data-local map tasks=10
		Total time spent by all maps in occupied slots (ms)=131457
		Total time spent by all reduces in occupied slots (ms)=4255
		Total time spent by all map tasks (ms)=131457
		Total time spent by all reduce tasks (ms)=4255
		Total vcore-seconds taken by all map tasks=131457
		Total vcore-seconds taken by all reduce tasks=4255
		Total megabyte-seconds taken by all map tasks=134611968
		Total megabyte-seconds taken by all reduce tasks=4357120
	Map-Reduce Framework
		Map input records=100000000
		Map output records=30
		Map output bytes=820
		Map output materialized bytes=960
		Input split bytes=1390
		Combine input records=0
		Combine output records=0
		Reduce input groups=21
		Reduce shuffle bytes=960
		Reduce input records=30
		Reduce output records=1
		Spilled Records=60
		Shuffled Maps =10
		Failed Shuffles=0
		Merged Map outputs=10
		GC time elapsed (ms)=1568
		CPU time spent (ms)=101400
		Physical memory (bytes) snapshot=6465937408
		Virtual memory (bytes) snapshot=16885534720
		Total committed heap usage (bytes)=6984564736
	Shuffle Errors
		BAD_ID=0
		CONNECTION=0
		IO_ERROR=0
		WRONG_LENGTH=0
		WRONG_MAP=0
		WRONG_REDUCE=0
	File Input Format Counters 
		Bytes Read=10000000000
	File Output Format Counters 
		Bytes Written=25

real	0m36.884s
user	0m5.361s
sys	0m0.250s
```
* documentation used: 
    * http://hadoop.apache.org/docs/r2.4.1/hadoop-project-dist/hadoop-hdfs/CentralizedCacheManagement.html#Configuration
    * http://blog.cloudera.com/blog/2014/08/new-in-cdh-5-1-hdfs-read-caching/
    * http://stackoverflow.com/a/5789425


