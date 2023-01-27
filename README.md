

flink流计算处理分析日志全流程分析运用，未完待续。。。

# 1、下载安装jdk

# 2、下载安装Zookeeper

大家自行到官网下载

```
https://zookeeper.apache.org/releases.html
```

我用的apache-zookeeper-3.7.0-bin.tar.gz

```
tar -zxvf apache-zookeeper-3.7.0-bin.tar.gz -C /opt/

cd /opt/apache-zookeeper-3.7.0-bin/conf/

cp -r zoo_sample.cfg zoo.cfg

cd /opt/apache-zookeeper-3.7.0-bin/bin

./zkServer.sh start
```

# 3、下载kafka

```
http://kafka.apache.org/downloads.html
```

## 1、下载的kafka_2.11-2.4.0.tgz版本

```
tar -zxvf kafka_2.11-2.4.0.tgz -C /opt/

//修改下config/server.properties
cd /opt/kafka_2.11-2.4.0
vi config/server.properties
```

## 2、修改配置

```
//修改这两项配置
advertised.listeners=PLAINTEXT://192.168.52.200:9092
zookeeper.connect=localhost:2181
```

## 3、启动kafka

```
bin/kafka-server-start.sh -daemon config/server.properties
```

## 4、测试

```
cd /opt/kafka_2.11-2.4.0/bin

./kafka-console-consumer.sh  --bootstrap-server 192.168.52.200:9092 --consumer.config ../config/consumer.properties  --topic Flink_TEST  --from-beginning
```

看到如下就证明已经成功将数据成功导入kafka并且消费。

![img](https://docimg9.docs.qq.com/image/AgAABS4iltAO2FdsglVGvZgjB-XaZnTV.png?w=1612&h=757)

# 4、下载flink

