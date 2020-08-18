# Elastic-Stack Dockerized Setup
The Elastic stack is the target for course progress logging and system availability logs. The NISLAB Elastic stack contains following three components:

![alt text](https://www.elastic.co/guide/en/infrastructure/guide/current/images/monitoring-architecture.png "Elastic Stack Components")

Diferent Beats gather their specified data and send it to elasticsearch (Example). Elasticsearch is a real-time, distributed storage, search, and analytics engine. We use Kibana to search, view, and interact with data stored in Elasticsearch.


## Setup
1. Clone Repo
2. Adjust environment variables in .env (DO NOT CHANGE `ELASTIC_USERNAME`)
3. Generate keys using `setup.docker-compose.yml` (`docker-compose -f setup.docker-compose.yml up`)
4. Run main docker-compose file (`docker-compose up -d`)
5. If elasticsearch container did not start sucessfully:
    1. Set owner permissions on `elk-stack` directory (`sudo chown -R elk-stack`)
6. Set up different [Beats](https://github.com/elastic/beats) to send data to elasticsearch