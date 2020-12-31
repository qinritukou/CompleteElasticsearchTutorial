### search
```
curl -H "Content-Type: application/json" '127.0.0.1:9200/movies/_search?pretty' -d '
{
    "query": {
        "match": {
            "title": "Start Trek"
        }
    }
}
'

curl -H "Content-Type: application/json" '127.0.0.1:9200/movies/_search?pretty' -d '
{
    "query": {
        "match_phrase": {
            "genre": "sci"
        }
    }
}
'
```

```
curl -XDELETE 127.0.0.1:9200/movies
curl  -H "Content-Type: application/json" -XPUT 127.0.0.1:9200/movies -d '
{
    "mappings": {
        "properties": {
            "id": { "type": "integer" },
            "year": { "type": "date" },
            "genre": { "type": "keyword" },
            "title": { "type": "text", "analyzer": "english" }
        }
    }
}'
curl -H "Content-Type: application/json" -XPUT '127.0.0.1:9200/_bulk?pretty' --data-binary @movies.json
curl -H "Content-Type: application/json" '127.0.0.1:9200/movies/_search?pretty' -d '
{
    "query": {
        "match": {
            "genre": "sci"
        }
    }
}
'
curl -H "Content-Type: application/json" '127.0.0.1:9200/movies/_search?pretty' -d '
{
    "query": {
        "match": {
            "genre": "Sci-Fi"
        }
    }
}
'
```