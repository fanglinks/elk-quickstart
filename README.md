# elk-quickstart

ELK Quickstart (Elasticsearch/Logstash/Kibana), Version 5.6.3
Perfect for a quick Kibana demo (only Elasticsearch and Kibana required + sample data)

## Start Elasticsearch

```bash
 # Move to Elasticsearch directory
 $ cd elasticsearch

 # Run
 $ clear; bin/elasticsearch
```

## Start Logstash

```bash
 # Move to Logstash directory
 $ cd logstash

 # Run with configuration file
 $ clear; bin/logstash -f myconfiguration.conf
```

## Import sample data

```bash
 # Move to sample-data directory
 $ cd sample-data

 # Run curl command
 $ curl -H 'Content-Type: application/x-ndjson' -XPOST 'localhost:9200/bank/account/_bulk?pretty' --data-binary @accounts.json
 $ curl -H 'Content-Type: application/x-ndjson' -XPOST 'localhost:9200/shakespeare/_bulk?pretty' --data-binary @shakespeare.json
```

## Start Kibana

```bash
 # Move to Kibana directory
 $ cd kibana

 # Run
 $ clear; bin/kibana
```

