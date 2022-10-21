# Elastic Search

Data is stored in documents.  Documents are grouped into indices.  

Data is stored in shards.  Each index starts with one shard.  Index may be configured to have multiple shared distributed across nodes.


# Download


# Docker

[elasticsearch](https://hub.docker.com/_/elasticsearch)

	docker run -d --name elasticsearch -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" elasticsearch:tag

[kibana](https://hub.docker.com/_/kibana).  [Kibana guide](https://www.elastic.co/guide/en/kibana/current/docker.html#run-kibana-on-docker-for-dev)


# Documentation

All elastic [docs](https://www.elastic.co/guide/index.html)

Elastic search User [Guide](https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html)

Getting started [video](https://www.youtube.com/watch?v=VzZz6qJwYmY) https://www.elastic.co/webinars/getting-started-elasticsearch?msclkid=0f24a2e36d47171a9ca3c1ad84e25c5b&ultron=brand-sitelink&blade=adwords-s&Device=c&thor=elasticsearch&msclkid=0f24a2e36d47171a9ca3c1ad84e25c5b

Logging with the [ELK Stack](https://www.elastic.co/webinars/introduction-elk-stack?baymax=default&elektra=docs&storm=top-video)

logging with the [python client](https://www.elastic.co/guide/en/elasticsearch/client/python-api/current/index.html)

## Settings

`elasticsearch.yml` contains most [configuration settings](https://www.elastic.co/guide/en/elasticsearch/reference/current/settings.html)

`network.host`: must be set to allow remote connections

[Security](https://www.elastic.co/guide/en/elasticsearch/reference/current/configuring-security.html) 
are in `elasticsearch.yml`.




Elastic community videos:

 * [Beginners crash course](https://www.youtube.com/watch?v=gS_nHTWZEJ8)

# Install in Docker

See the guides above

See intg-core script to create the containers for development.

Create the elastic search container

Generate a token

	docker exec -it elasticsearch //usr/share/elasticsearch/bin/elasticsearch-create-enrollment-token -s kibana

Open a web browser to http://localhost:5601.  It should ask for the token.

Next it will ask for a verification code.  Generate this on kibana

	docker exec -it kibana sh bin/kibana-verification-code
	
# CURL requests

You may need to use `https`.  Also, may need to use `-k` to ignore certificate errors.



# Python Client

[Documentation](https://www.elastic.co/guide/en/elasticsearch/client/python-api/8.4/overview.html)

API:  [elasticsearch-py](https://elasticsearch-py.readthedocs.io/en/master/)




# Python Logging

Use module ecs-logging.  See this [primer](https://www.elastic.co/guide/en/ecs-logging/python/master/installation.html)

Turn on [ECS tracing fields](https://www.elastic.co/guide/en/ecs/master/ecs-tracing.html) to correlate logs across services.


Send logs with [Filebeat](https://www.elastic.co/beats/filebeat) to Elasticsearch.  [Quick Start](https://www.elastic.co/guide/en/beats/filebeat/8.4/filebeat-installation-configuration.html)

