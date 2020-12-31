# movie len demo

### mapping
```
curl -H "Content-Type: application/json" -XPUT 127.0.0.1:9200/movies -d '
{
    "mappings": {
        "properties": {
            "year": {
                "type": "date"
            }
        }
    }
}'
```

### get mapping defitions
```
curl -H "Content-Type: application/json" -XGET '127.0.0.1:9200/movies/_mapping?pretty'
```


### insert 
```
curl -H "Content-Type: application/json" -XPUT 127.0.0.1:9200/movies/_doc/109487 -d '
{
    "genre": ["IMAX", "Sci-Fi"],
    "title": "Interstellar",
    "year": 2014
}'
```

### get
```
curl -H "Content-Type: application/json" -XGET '127.0.0.1:9200/movies/_doc/109487?pretty'
```

### add data by bulk api
```
wget http://media.sundog-soft.com/es7/movies.json
curl -H "Content-Type: application/json" -XPUT '127.0.0.1:9200/_bulk?pretty' --data-binary @movies.json
```