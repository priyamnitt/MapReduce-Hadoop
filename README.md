# About me
<img width="263" alt="Screenshot 2023-12-03 at 12 09 51" src="https://github.com/priyamnitt/MapReduce-Hadoop/assets/104387538/03f4c53b-6043-4728-95f3-99d39e92a387">\
<b>Name - PRIYAM KUMAR\
Roll No - 114121069
Course - CSOE11 Big Data Analytics</b>

# MapReduce-Hadoop
MapReduce-Hadoop<br>
<img width="604" alt="Screenshot 2023-12-03 at 11 52 47" src="https://github.com/priyamnitt/MapReduce-Hadoop/assets/104387538/6d46aa3d-c957-4009-b1f1-0a0af5ba05c5">

## Installation details
<b> Install Java</b>
```
sudo apt install openjdk-8-jdk -y
```

<b>Download hadoop installation files</b>
```
wget https://archive.apache.org/dist/hadoop/core/hadoop-3.3.6/hadoop-3.3.6.tar.gz
```

<b>Extract installations files using following command</b>
```
tar -xvf hadoop-3.3.6.tar.gz
```

<b> Download OpenSSH</b>
```
sudo apt install openssh-server openssh-client -y
```

<b> Add following external jars in eclipse project</b>\
From root node of project, go to `Build Path → Configure Build Path` from context menu.\
In the Libraries tab, click Add External Jars...
* hadoop-2.4.0/share/hadoop/hdfs/hadoop-common-3.3.6.jar
* hadoop-2.4.0/share/hadoop/hdfs/hadoop-hdfs-3.3.6.jar
* hadoop-2.4.0/share/hadoop/mapreduce/hadoop-mapreduce-client-common-3.3.6.jar
* hadoop-2.4.0/share/hadoop/mapreduce/hadoop-mapreduce-client-core-3.3.6.jar
* ...

<b> User creation for Hadoop environment</b>
```
sudo adduser hadoop
sudo adduser priyamkr sudo
su - hadoop
```

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

## Single Node Hadoop Setup
This is also called pseudo-distributed mode, allows each Hadoop daemon to run as a single Java process. 
A Hadoop environment is configured by editing a set of configuration files:
* bashrc
* hadoop-env.sh
* core-site.xml
* hdfs-site.xml
* mapred-site-xml
* yarn-site.xml

#### Setting up the environment variables (bashrc)
```
nano ~/.bashrc
```

```
#Hadoop Related Options
export HADOOP_HOME=/home/hadoop/hadoop
export HADOOP_INSTALL=$HADOOP_HOME
export HADOOP_MAPRED_HOME=$HADOOP_HOME
export HADOOP_COMMON_HOME=$HADOOP_HOME
export HADOOP_HDFS_HOME=$HADOOP_HOME
export YARN_HOME=$HADOOP_HOME
export HADOOP_COMMON_LIB_NATIVE_DIR=$HADOOP_HOME/lib/native
export PATH=$PATH:$HADOOP_HOME/sbin:$HADOOP_HOME/bin
export HADOOP_OPTS="-Djava.library.path=$HADOOP_HOME/lib/native"
```

#### Configuration Changes in hadoop-env.sh file
Identify Java directory
```
priyamkr:~$ which javac
/usr/local/buildtools/java/jdk/bin/javac
priyamkr:~$ readlink -f /usr/bin/javac
/usr/lib/jvm/java-17-openjdk-amd64/bin/javac
```

```
nano $HADOOP_HOME/etc/hadoop/hadoop-env.sh
```

Update JAVA_HOME in hadoop-env.sh file
```
export JAVA_HOME=/usr/lib/jvm/java-17-openjdk-amd64
```

#### Configuration Changes in core-site.xml file
```
nano $HADOOP_HOME/etc/hadoop/core-site.xml
```

```
<configuration>
<property>
  <name>fs.default.name</name>
  <value>hdfs://localhost:9000</value>
</property>
</configuration>
```

#### Configuration Changes in hdfs-site.xml file
```
nano $HADOOP_HOME/etc/hadoop/hdfs-site.xml
```

```
<configuration>
<property>
 <name>dfs.replication</name>
 <value>1</value>
</property>

<property>
  <name>dfs.name.dir</name>
  <value>file:///home/hadoop/hadoopdata/hdfs/namenode</value>
</property>

<property>
  <name>dfs.data.dir</name>
  <value>file:///home/hadoop/hadoopdata/hdfs/datanode</value>
</property>
</configuration>
```

#### Configuration Changes in mapred-site-xml file
```
nano $HADOOP_HOME/etc/hadoop/mapred-site.xml
```

```
<configuration>
 <property>
  <name>mapreduce.framework.name</name>
  <value>yarn</value>
 </property>
</configuration>
```

#### Configuration Changes in yarn-site.xml file
```
nano $HADOOP_HOME/etc/hadoop/yarn-site.xml
```

```
<configuration>
 <property>
  <name>yarn.nodemanager.aux-services</name>
  <value>mapreduce_shuffle</value>
 </property>
</configuration>
```

#### Format NameNode
```
$ cd ~/hadoop/sbin
$ hdfs namenode -format
http://localhost:9864/
```

#### Start Hadoop Cluster
Navigate to the hadoop/sbin directory and execute the following commands to start the NameNode and DataNode:
```
$ ./start-dfs.sh
```

Once the namenode, datanodes, and secondary namenode are up and running, start the YARN resource and nodemanagers by typing:
```
$ ./start-yarn.sh
```

To verify all the Hadoop services/daemons are started successfully you can use the jps command.
```
$ jps
```

#### Access Hadoop UI from Browser

Hadoop NameNode started on default port 9870.
```
http://localhost:9870/
```

Now access port 8042 for getting the information about the cluster and all applications.
```
http://localhost:8042/
```

Access port 9864 to get details about your Hadoop node.
```
http://localhost:9864/
```
