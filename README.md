# Nevo Data Replication

This is an example project showing how to replicate data from a source database to a sink database.

- Docker containers for Microsoft SQL Server, Zookeeper, Kafka, Kafka Connect, Kafka UI, and Debezium
- How to enable CDC on Microsoft SQL Server
- Install Debezium Microsoft SQL Server connector
- Write CDC changes to Kafka topics using Debezium SQL Server connector.
- Write CDC changes to sink database to finish full replication procedure.

## Getting Started

1. Install `Azure Data Studio`
2. `docker-compose up`
3. In Azure Data Studio, open file `mssql_init.sql` and run file.
4. Run script `create_connector.sh`
2. Browse [http://localhost:8080](http://localhost:8080)

## Steps taken to build this project for iOS Mac:
1. Installed Azure Data Studio on Mac
2. Created docker-compose.yml - Microsoft SQL Server service in (mcr.microsoft.com/mssql/server:2019-latest)
3. Wrote msql_init.sql script to create db, create tables, insert records, and enable CDC
4. Added to docker-compose.yml - zookeeper, kafka, kafka-connect, and kafka-ui
5. Wrote `create_connector.sh` is is based on the results of `myssql_connector.json` via JSON.stringify() and pasted into curl command.

## Terms
- Source - the original data to be replicated
- Sink - (a cluster that is) the primary consumer of replication data
- Kafka - event streaming platform
    - Broker - Responsible for receiving and sending the messages, it consists in two parts: topics and partitions.
    - Topic - It’s an identifier used to organize the message into categories.
    - Partitions - A subdivision of a topic to organize and balance the data.
    - Kafka cluster - A cluster set, being the main instance of Kafka.
    - Producer - The source of the data, send and distribute the logs.
    - Consumer - Consumers subscribe to a topic and listen to them all the time, receiving logs.
    - Kafka Connectors
    - Kafka Transformers
    - Kafka Converters
- Debezium (db-z-ium) - open source distributed platform for change data capture that converts information from your existing databases into event streams, enabling applications to detect, and immediately respond to row-level changes in the databases

## CDC (Change Data Capture)
- For SQL Server, materialied views are not supported

## Resoures
- https://debezium.io/documentation/reference/2.1/connectors/sqlserver.html
- https://debezium.io/documentation/reference/2.1/tutorial.html
- https://kafka.apache.org/
- https://debezium.io/
- https://www.confluent.io/confluent-cloud/
- https://learn.microsoft.com/en-us/azure/event-hubs/event-hubs-kafka-connect-debezium
- https://medium.com/google-cloud/near-real-time-data-replication-using-debezium-4da77cef67ab
- https://medium.com/nagoya-foundation/simple-cdc-with-debezium-kafka-a27b28d8c3b8