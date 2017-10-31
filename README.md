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

Configuration example for Database query (uncomment what you need, jdbc_driver_library already provided):
```bash
input {
    jdbc {
	# MySQL
        # jdbc_connection_string => "jdbc:mysql://localhost:3306/mydb"
        # jdbc_driver_library => "../driver/mysql-connector-java-5.1.44-bin.jar"
        # jdbc_driver_class => "com.mysql.jdbc.Driver"

	# PostgreSQL
	# jdbc_connection_string => "jdbc:postgresql://localhost:5432/mydb"
        # jdbc_driver_library => "../driver/postgresql-42.1.4.jar"
        # jdbc_driver_class => "org.postgresql.Driver"

        jdbc_user => "username"
        jdbc_validate_connection => true
        statement => "SELECT * from table"
    }
}
output {
    elasticsearch {
        protocol => http
        index => "index"
        document_type => "index"
        document_id => "%{uid}"
        host => "ES_NODE_HOST"
    }
}
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

