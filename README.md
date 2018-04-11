# hadoop-hive-tez
测试配置文件
hadoop版本：2.8.1
hive版本：2.3.3
tez版本：0.9.0

环境变量配置 /etc/profile 新增配置

export JAVA_HOME=/usr/java/jdk1.8.0_151
export JRE_HOME=${JAVA_HOME}/jre

#hadoop
export HADOOP_HOME=/home/hadoop/hadoop-2.8.1
export HADOOP_CONF_DIR=$HADOOP_HOME/etc/hadoop/
export PATH=$PATH:$HADOOP_HOME/bin
export PATH=$PATH:$HADOOP_HOME/sbin

#hive
export HIVE_HOME=/home/hadoop/hive-2.3.3
export PATH=$PATH:$HIVE_HOME/bin

#tez
export TEZ_HOME=/home/hadoop/tez-0.9.0
export TEZ_CONF_DIR=$TEZ_HOME/conf
export TEZ_JARS=$TEZ_HOME
export TEZ_LIB_DIR=$TEZ_HOME:$TEZ_HOME/lib


export HADOOP_CLASSPATH=$HADOOP_CLASSPATH:${TEZ_CONF_DIR}:${TEZ_HOME}/*:${TEZ_HOME}/lib/*



hive metastore服务启动：
hive --service metastore &  // 表示后台运行
hive --service cli // 表示启动客户 一般直接hive即可
hive cli启动
创建库：
hive > create database test;
创建表：
hive> create table test(name STRING);

测试：
hive> use test;
OK
Time taken: 0.936 seconds

hive> select * from test;
OK
afadfa
bbbbb
ccccc
ccccc
fffff
Time taken: 6.943 seconds, Fetched: 5 row(s)

hive> select * from test;
OK
afadfa
bbbbb
ccccc
ccccc
fffff
Time taken: 0.379 seconds, Fetched: 5 row(s)

hive> select count(name) from test;
Query ID = hadoop_20180411143659_8b1269e1-0ce5-4370-82ef-11ed1199f21a
Total jobs = 1
Launching Job 1 out of 1
Status: Running (Executing on YARN cluster with App id application_1523428469267_0001)

OK
5
Time taken: 26.964 seconds, Fetched: 1 row(s)
hive> select count(name) from test;
Query ID = hadoop_20180411143955_2481af90-662a-46db-b953-f74858e0e83a
Total jobs = 1
Launching Job 1 out of 1
Status: Running (Executing on YARN cluster with App id application_1523428469267_0001)

OK
5
Time taken: 21.902 seconds, Fetched: 1 row(s)

hive> insert into table test values('aaaa');
Query ID = hadoop_20180411144044_27828504-8354-42de-815d-29af3179558c
Total jobs = 1
Launching Job 1 out of 1
Status: Running (Executing on YARN cluster with App id application_1523428469267_0001)

Loading data to table test.test
OK
Time taken: 16.793 seconds

hive> 

