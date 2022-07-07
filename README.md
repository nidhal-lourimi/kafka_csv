  �k�a�f�k�a�_�c�s�v�
# kafka-connect-spooldir


## Description

using kafka connector & spooldir plugin to proccess data from csv file

## Getting Started

### Dependencies

* docker needed before installing program.
* confluentinc/cp-zookeeper:5.3.1, confluentinc/cp-kafka-connect:6.2.0, confluentinc/cp-kafka,jcustenborder-kafka-connect-spooldir etc.,

### Installing

* run this command on the host path
```sh
                                 docker compose -f "docker-compose.yml" up -d --build
```

### Executing program

* create an instance of kafka connector and inject all config need it 
using postman or curl http://localhost:8083/connectors
```
{ 
  "name": "CsvSpoolDir", 
  "config": { 
    "tasks.max": "1", 
    "connector.class": "com.github.jcustenborder.kafka.connect.spooldir.SpoolDirCsvSourceConnector", 
    "input.path": "/data/unprocessed", 
    "input.file.pattern": "csv-spooldir-source.csv", 
    "error.path": "/data/error", 
    "finished.path": "/data/processed", 
    "halt.on.error": "false", 
    "topic": "spooldir-testing-topic", 
    "csv.first.row.as.header": "true", 
    "schema.generation.enabled": "true" 
  } 
}
```
