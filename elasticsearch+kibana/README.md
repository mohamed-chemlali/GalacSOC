# GalacSOC
## Installation:
### Install elasticsearch image
```
docker pull docker.elastic.co/elasticsearch/elasticsearch:7.8.0
```
### Install kibana image
```
docker pull docker.elastic.co/kibana/kibana:7.8.0

```
## How to use:
### Using Docker compose file

1. Run the docker compose file 
```
docker-compose up
```
2. Set vm.max_map_count to at least 262144
```
sysctl -w vm.max_map_count=262144
```
### Separate Config 
1. Config elasticsearch
```
docker run -d -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" docker.elastic.co/elasticsearch/elasticsearch:7.8.0
sysctl -w vm.max_map_count=262144

```
2. Config kibana

Replace XXXX with elasticsearch container ID or name 

```
docker run --link XXXX:elasticsearch -p 5601:5601 docker.elastic.co/kibana/kibana:7.8.0
```
