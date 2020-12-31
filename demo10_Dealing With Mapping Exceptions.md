
```
curl -H "Content-Type: application/json" -XPUT '127.0.0.1:9200/microservice-logs' --data-raw '{
    "mappings": {
        "properties": {
            "timestamp": { "type": "date" },
            "service": { "type": "keyword" },
            "host_ip": { "type": "ip" },
            "port": { "type": "integer" },
            "message": { "type": "text" }
        }
    }
}'
curl -H "Content-Type: application/json" -XPOST '127.0.0.1:9200/microservice-logs/_doc?pretty' --data-raw '{
    "timestamp": "2020-04-11T12:34:56.789Z", 
    "service": "XYZ",
    "host_ip": "10.0.2.15",
    "port": "15000",
    "message": "Hello!"
}'  
curl -H "Content-Type: application/json" -XPOST '127.0.0.1:9200/microservice-logs/_doc?pretty' --data-raw '{
    "timestamp": "2020-04-11T12:34:56.789Z", 
    "service": "XYZ",
    "host_ip": "10.0.2.15",
    "port": "NONE",
    "message": "Im not well"
}'  
curl -H "Content-Type: application/json" -XPOST '127.0.0.1:9200/microservice-logs/_close'
curl -H "Content-Type: application/json" -XPUT '127.0.0.1:9200/microservice-logs/_settings' --data-raw '{
    "index.mapping.ignore_malformed": true
}'
curl -H "Content-Type: application/json" -XPOST '127.0.0.1:9200/microservice-logs/_open'
curl -H "Content-Type: application/json" -XPOST '127.0.0.1:9200/microservice-logs/_doc?pretty' --data-raw '{
    "timestamp": "2020-04-11T12:34:56.789Z", 
    "service": "XYZ",
    "host_ip": "10.0.2.15",
    "port": "NONE",
    "message": "Im not well"
}'  
curl -H "Content-Type: application/json" -XGET '127.0.0.1:9200/microservice-logs/_doc/iwcDuHYBM9k-ww9BK5S_?pretty'



curl -H "Content-Type: application/json" -XPOST '127.0.0.1:9200/microservice-logs/_doc?pretty' --data-raw '{
    "timestamp": "2020-04-11T12:34:56.789Z", 
    "service": "XYZ",
    "host_ip": "10.0.2.15",
    "port": "12345",
    "message": "Received...",
    "payload": { 
        "data": {
            "received": {
                "even": "more"
            }
        }
    }
}'  

```