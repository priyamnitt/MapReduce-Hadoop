# MapReduce-Hadoop
MapReduce-Hadoop

## Installation details
After installing Java, install Hadoop with following commands -

<b>Download hadoop installation files</b>
```
wget https://archive.apache.org/dist/hadoop/core/hadoop-3.3.6/hadoop-3.3.6.tar.gz
```

<b>Extract installations files using following command</b>
```
tar -xvf hadoop-3.3.6.tar.gz
```

<b> Add following external jars in eclipse project</b>\
From root node of project, go to `Build Path → Configure Build Path` from context menu.\
In the Libraries tab, click Add External Jars...
* hadoop-2.4.0/share/hadoop/hdfs/hadoop-common-3.3.6.jar
* hadoop-2.4.0/share/hadoop/hdfs/hadoop-hdfs-3.3.6.jar
* hadoop-2.4.0/share/hadoop/mapreduce/hadoop-mapreduce-client-common-3.3.6.jar
* hadoop-2.4.0/share/hadoop/mapreduce/hadoop-mapreduce-client-core-3.3.6.jar
* ...

<b>Confirm Installation</b>
```
priyamkr:~$ java -version
openjdk version "11.0.20.1" 2023-10-05
OpenJDK Runtime Environment (build 11.0.20.1+1-google-release-571111042)
OpenJDK 64-Bit Server VM (build 11.0.20.1+1-google-release-571111042, mixed mode, sharing)
```

```
priyamkr:~$ hadoop version
Hadoop 3.3.6
Source code repository https://github.com/apache/hadoop.git -r 1be78238728da9266a4f88195058f08fd012bf9c
Compiled by ubuntu on 2023-06-18T08:22Z
Compiled on platform linux-x86_64
Compiled with protoc 3.7.1
From source with checksum 5652179ad55f76cb287d9c633bb53bbd
```

