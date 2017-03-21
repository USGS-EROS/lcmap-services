# LCMAP-Services

Provides a convenient way to run underlying LCMAP services locally.

* Zookeeper
* Mesos
* Marathon
* Cassandra
* Elasticsearch
* RabbitMQ
* Kafka

## Dependencies

* Docker 1.13
* Docker Compose 1.10

## Startup

```
docker-compose up
```

Cassandra, Elasticsearch, and RabbitMQ persist data in the `./volumes` so that
data is available after stopping and starting services. If you wish to start
fresh, remove the contents of `./volumes`.

## Using

All services expose ports through the host so that you can connect to them from
other applications without the hassle of locating the assigned IP addresses. You
may also wish to use these service with other docker containers. In such cases,
you may run the docker container like this:

```
docker run --net=lcmap usgseros/lcmap-landsat:0.1.0-SNAPSHOT $(cat config.edn)
```

This container will be able to refer to other containers using the service name
as the hostname. For example, the Cassandra container will be reachable from
within another container using the host and port `cassandra:9042`.
