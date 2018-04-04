# 快速搭建  kafka-zookeeper
> 快速搭建本地的kafka zookeeper 单机环境。

- Step1: 下载已经配置的版本 [Kafka2.11]()，并解压
    ```
    unzip kafka2.11.zip
    cd kafka/
    ```
    
- Step2: 启动Kafka 
    ```
    启动zookeeper

    bin/zookeeper-server-start.sh config/zookeeper.properties &

    启动kafka

    bin/kafka-server-start.sh config/server.properties &

    停止kafka
    bin/kafka-server-stop.sh

    停止zookeeper
    bin/zookeeper-server-stop.sh
    ````

- Step 3: 测试
    ```
    创建topic
    bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic test

    展示topic
    bin/kafka-topics.sh --list --zookeeper localhost:2181

    描述topic
    bin/kafka-topics.sh --describe --zookeeper localhost:2181 --topic my-replicated-topic

    生产者：
    bin/kafka-console-producer.sh --broker-list 130.51.23.95:9092 --topic my-replicated-topic

    消费者：
    bin/kafka-console-consumer.sh --zookeeper 130.51.23.95:2181 --topic test --from-beginnin
    ```
    
**参考：**   
- 理论   https://blog.csdn.net/tangdong3415/article/details/53432166
- 指令： https://www.cnblogs.com/dragkiss/p/5668019.html
- 集群安装： https://blog.csdn.net/zxy987872674/article/details/72466504
