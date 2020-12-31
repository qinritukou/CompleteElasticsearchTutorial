### add series mapping
```
curl -H "Content-Type: application/json" -XPUT '127.0.0.1:9200/series' -d '
{
    "mappings": {
        "properties": {
            "file_to_franchise": {
                "type": "join",
                "relations": { "franchise": "film" }
            }
        }
    }
}'
wget http://media.sundog-soft.com/es7/series.json
curl -H "Content-Type: application/json" -XPUT '127.0.0.1:9200/_bulk?pretty' --data-binary @series.json
curl -H "Content-Type: application/json" -XGET '127.0.0.1:9200/series/_search?pretty' -d '
{
    "query": {
        "has_parent": {
            "parent_type": "franchise",
            "query": {
                "match": {
                    "title": "Start Wars"
                }
            }
        }
    }
}'
curl -H "Content-Type: application/json" -XGET '127.0.0.1:9200/series/_search?pretty' -d '
{
    "query": {
        "has_child": {
            "type": "film",
            "query": {
                "match": {
                    "title": "The Force Awakens"
                }
            }
        }
    }
}'
```
