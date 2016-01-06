# Spark Standalone Cluster Docker Image

This repository contains a set of scripts and configuration files to run a [Apache Spark](https://spark.apache.org/) standalone cluster from [Docker](https://www.docker.io/) container.

* Spark 1.5.1
* Scala 2.11

## Build Docker Image

    docker build -t nikhilrp/spark .

## Push Image

    docker push nikhilrp/spark

## Run

To run a Spark Master node:

```
docker run -d -t \
-p 7077:7077 \
-p 8080:8080 \
--name spark_master \
nikhilrp/spark \
/start-master.sh "$@"
```

To run a worker node:

```
docker run -d -t -P  \
--name spark_worker_1 \
--link spark_master:spark_master  \
nikhilrp/spark  \
/start-worker.sh "$@"
```

You can run multiple workers. Every worker would be able to find master by its container name **spark_master**.


## Acknowledgements

This docker image is on this excellent repository https://github.com/epahomov/docker-spark .

## TODO
* Out of memory errors have to be handled effectively
