[toc]

### spark2.3.0 监控配置

1. **spark-defaults.conf 增加如下内容**

   ```
   spark.eventLog.enabled  true
   spark.eventLog.dir  hdfs:///spark/log          		## 日志路径，可配置为本地路径
   spark.eventLog.compress  true
   ```

2. **spark-env.sh 增加如下内容**

   ```
   export SPARK_HISTORY_OPTS="
   -Dspark.history.ui.port=4040                         ## 端口
   -Dspark.history.retainedApplications=5               ## 缓存应用数量
   -Dspark.history.fs.logDirectory=hdfs:///spark/log"   ## 日志路径，可配置为本地路径
   
   ## 拷贝命令
   export SPARK_HISTORY_OPTS="-Dspark.history.ui.port=4040 -Dspark.history.retainedApplications=5 -Dspark.history.fs.logDirectory=hdfs:///spark/log"
   ```

   > 注意：
   >
   > ​	hdfs高可用地址只能这样写，不能加前缀名称： hdfs:///var/log/spark  
   
3. **启动start-history-server.sh**
    ./start-history-server.sh

4. **hdfs**
   hdfs dfs -mkdir -p /user/hadoop
   hdfs dfs -ls /user/hadoop
   hdfs dfs -put /home/data/spark-data/word.txt /user/hadoop
   hdfs dfs -rm -r /var/log/spark/*

   hdfs dfs -put /home/data/spark-data/spark-test-data.txt /test/hdfs/spark/data
   hdfs dfs -mkdir -p /test/hdfs/spark/data
   hdfs dfs -mkdir -p /test/hdfs/spark/result

### 参考文章

1. [spark官网](http://spark.apache.org/docs/2.2.1/monitoring.html)
2. [spark 查看job history 日志](https://blog.csdn.net/stark_summer/article/details/46459701)
3. [spark history server 配置](https://blog.csdn.net/shenfuli/article/details/52948320)