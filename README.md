# Elasticsearch and Kibana Setup

This repository contains a Docker Compose setup for Elasticsearch and Kibana version 8.0.1. 
It includes configurations for exposing Elasticsearch on port 9200 and Kibana on port 5601, using a named volume for data persistence (`esdata`), and setting up a custom bridge network (`elastic`) with a specified subnet.

## Usage
0. Docker Sanctions:

    0.1. use docker.ir proxy : for docker deamon : add "registry-mirrors": ["https://registry.docker.ir"] in /etc/docker/daemon.json
    
    0.2. use image from proxy : in docker-compose add registry.docker.ir as image perfix, for example image: elasticsearch:8.0.1 ==> image: registry.docker.ir/elasticsearch:8.0.1
    
    0.3. pull image from other repository for example "sudo docker pull registry.docker.ir/elasticsearch:8.0.1" and add original tag "docker image tag registry.docker.ir/elasticsearch:8.0.1 elasticsearch:8.0.1"

1. Clone this repository:
git clone https://github.com/jaavid/fc-docker.git cd fc-docker


2. Start the services:
docker-compose up -d


3. Access Kibana at http://localhost:5601.

## Configuration Details

- **Elasticsearch**: Runs as a single-node cluster with security disabled for simplicity.
- **Kibana**: Depends on Elasticsearch and exposes its UI on port 5601.
- **Network**: A custom bridge network named `elastic` with a subnet of `172.28.0.0/16`.
- **Volume**: Uses a named volume `esdata` for persistent storage of Elasticsearch data.

## Health Check

Elasticsearch's health check runs every 30 seconds to ensure the service is operational.