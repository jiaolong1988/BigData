### livy 提交Spark-Pi

curl -XPOST -H "Content-Type: application/json"  192.168.1.11:8998/batches --data '{ "conf": {"spark.master":"spark://master:7077"}, "file": "hdfs://namenode/test/spark-examples_2.11-2.3.0.jar", "className": "org.apache.spark.examples.SparkPi", "name": "sparkPi-standalone1", "executorCores":1, "executorMemory":"512m", "driverCores":1, "driverMemory":"512m", "queue":"default", "args":["100"]}'



### livy 提交Sprk-wordcount

curl -X POST  -H "Content-Type: application/json" 192.168.1.11:8998/batches --data '{"conf":{"spark.master":"spark://master:7077"} , "file": "hdfs://namenode/test/WordCount-Spark.jar", "name": "WordCount-standalone", "executorCores":1, "executorMemory":"512m", "driverCores":1, "driverMemory":"512m","queue":"default", "className": "WordCount", "args": ["hdfs://namenode/test/WordCount.txt", "hdfs://namenode/test/result/11"]}'



### livy 提交Spark-hbaseToredis

curl -X POST  -H "Content-Type: application/json" 192.168.1.11:8998/batches --data '{"conf":{"spark.master":"spark://master:7077"} , "file": "hdfs://namenode/test/bigData-import-1.0-SNAPSHOT-jar-with-dependencies.jar", "executorCores":4, "executorMemory":"8g", "driverCores":1, "driverMemory":"2g","queue":"default", "className": "com.quantyBrain.Import.SparkReadHBaseToRedisV2", "args": ["6", "2016-01-01 00:00:01", "2016-02-01 00:00:01", "1m", "6", "12"]}'



### 外网提交

curl -X POST  -H "Content-Type: application/json" 111.205.32.92:8998/batches --data '{"conf":{"spark.master":"spark://master:7077"} , "file": "hdfs://namenode/test/bigData-import-1.0-SNAPSHOT-jar-with-dependencies.jar", "executorCores":4, "executorMemory":"8g", "driverCores":1, "driverMemory":"2g","queue":"default", "className": "com.quantyBrain.Import.SparkReadHBaseToRedisV2", "args": ["6", "2016-01-01 00:00:01", "2016-02-01 00:00:11", "1m", "6", "12"]}'