# Cassandra Docker Image

Based on Cassandra Datastax, version 2.2.4.

## Build Docker Image

	docker build -t nikhilrp/cassandra .

## Push Image

    docker push nikhilrp/cassandra

## Run

### Opscenter

	docker run -d --name opscenter nikhilrp/opscenter

To get the OpsCenter IP from the container:

    OPS_IP=$(docker inspect -f '{{ .NetworkSettings.IPAddress }}' opscenter)

### Running Cassandra Nodes

3 Cassandra nodes for instance, would be launched in this way:

    docker run -d -p 9042:9042 --name cass1 -e OPS_IP=$OPS_IP nikhilrp/cassandra
    sleep $DEFAULT_SLEEP

    docker run -d -p 9042:9042 --name cass2 -e OPS_IP=$OPS_IP nikhilrp/cassandra
    sleep $DEFAULT_SLEEP

    docker run -d -p 9042:9042 --name cass3 -e OPS_IP=$OPS_IP nikhilrp/cassandra
    sleep $DEFAULT_SLEEP

## Acknowledgements

This docker image is based on excellent repository https://github.com/abh1nav/docker-cassandra .
