# Cassandra OpsCenter Docker Image

Based on Cassandra Datastax OpsCenter, version 5.2.0.

## Build Docker Image

	docker build -t nikhilrp/opscenter .

## Push Image

    docker push nikhilrp/opscenter

## Run

### Opscenter

By default:

	docker run -d --name opscenter nikhilrp/opscenter

You may also want to expose OpsCenter service ports:

    docker run -d --name opscenter -p 8888:8888 -p 61620:61620 nikhilrp/opscenter

## Acknowledgements

This docker image based on this excellent repository https://github.com/abh1nav/docker-opscenter .
