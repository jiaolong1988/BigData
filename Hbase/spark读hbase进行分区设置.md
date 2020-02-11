[toc]

### 相关知识点

- [HBase快照（Snapshot）技术](https://blog.csdn.net/scgaliguodong123_/article/details/46817059)
- [Spark在读取Hbase的时候，RDD分区数量为**数据所属Region的数量**](https://www.cnblogs.com/listenfwind/p/10122838.html)
- [HBase Scan的重要参数](https://www.jianshu.com/p/87ac710a2da9)
- [利用SQL BulkLoad快速导入海量数据](https://blog.csdn.net/whdxjbw/article/details/81145672)

###  TableInputFormat类进行spark分区设置

- [重载getSplits自定义hbase mapreduce时map数量](https://blog.csdn.net/xx7330842/article/details/52925588)



### 总结

1. Spark在读取Hbase的时候，RDD分区数量为**数据所属Region的数量**

2. rowkey是以字典顺序排序存储的，因此数据在各个region中是顺序存储的，scan查询时候要注意数据是否在一个region中，否则会查询出多余数据。



