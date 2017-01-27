FROM antlypls/kafka

RUN apt-get update && apt-get install nano

ARG PUBLIC_HOSTNAME
ARG ZOOKEEPER
ARG TOPIC

RUN   echo "listeners=PLAINTEXT://0.0.0.0:9092" >> /opt/kafka_2.11-0.10.0.1/config/server.properties
RUN   echo "advertised.listeners=PLAINTEXT://$PUBLIC_HOSTNAME:9092" >> /opt/kafka_2.11-0.10.0.1/config/server.properties

RUN   echo "[program:set_topic]" > /etc/supervisor/conf.d/set_topic.conf
RUN   echo "command=/opt/kafka_2.11-0.10.0.1/bin/kafka-topics.sh --create --zookeeper $ZOOKEEPER --replication-factor 1 --partitions 2 --topic $TOPIC" >> /etc/supervisor/conf.d/set_topic.conf
RUN   echo "autostart=true" >> /etc/supervisor/conf.d/set_topic.conf



# 2181 is zookeeper, 9092 is kafka
EXPOSE 2181 9092

CMD ["supervisord", "-n"]

