# spark-kafka-cluster-on-docker
Spark 2 node cluster Master-Worker with kafka and zookeeper in docker

Everything is set up to work in a docker container. 
To launch just type

`docker-compose up`

This will spin 3 containers. 

Spark Master:
  Master node with Spark version 2.0.2

Spark Worker:
  Worker node with Spark version 2.0.2
  
Kafka (called datascience4) :
  Node with Kafka and Zookeeper
  
  
  
The docker compose configuration will set up the Kafka topic to 'word-count'.
You can change this by editing in the docker-compose.yml config file the environment variable 'TOPIC'.
  
This is the base config to run a simple word count example. You can launch spark streaming word count example as follows:
  
`docker exec -it dockerspark_master_1 bash`

(this will log you in in the master spark node) And then:

`spark-submit --master spark://master:7077 --packages org.apache.spark:spark-streaming-kafka-0-8-assembly_2.11:2.0.2 --jars examples/jars/spark-examples_2.11-2.0.2.jar /app/direct_kafka_wordcount.py datascience4:9092 word-count`


  
