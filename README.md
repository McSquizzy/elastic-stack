# Elastic-Stack Dockerized Setup
This repo contains a ready to go elastic stack installation with tls activated.


# Setup
1. Clone Repo
2. Adjust environment variables in .env (DO NOT CHANGE `ELASTIC_USERNAME`)
3. Generate keys using `setup.docker-compose.yml` (`docker-compose -f setup.docker-compose.yml up`)
4. Run main docker-compose file (`docker-compose up -d`)
5. If elasticsearch container did not start sucessfully:
    1. Set owner permissions on `elk-stack` directory (`sudo chown -R elk-stack $USER`)
6. Set up [Beats](https://github.com/elastic/beats) to send data to elasticsearch or an elastic agent for endpoint security
 

# Components

## Elasticsearch

**Host:** elasticsearch

### Config

`elasticsearch/config/elasticsearch.yml` Configures elasticsearch.

## Logstash
**Host:** logstash

### Config

`logstash/config/logstash.yml`  
`logstash/config/pipelines.yml` Registers pipelines using a defined config file.  
`logstash/pipeline/main.yml` Each pipeline must have an `input`, `filter` and `output` tag. Input defines what data should be processed in the pipeline. Filter defines how the data should be processed. Output defines where the data should be sent.

## Filebeat

Filebeat is a logfile shipper which can send data to elasticsearch directly or via Logstash to aggregate data. Filebeata must be installed on each client which should send data to elasticsearch. 


## Kibana

**Host:** kibana

### Config

`kibana/config/kibana.yml` Configures Kibana.


# Configuration

## Filebeat

To test the filebeat config, run `filebeat test config`  
to test the filebeat output, run `filebeat test output`


