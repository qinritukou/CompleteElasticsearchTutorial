### partial update api
```
curl -H "Content-Type: application/json" -XPOST '127.0.0.1:9200/movies/_doc/109487?pretty' -d '
{
    "genres": ["IMAX", "Sci-FI"],
    "title": "Interstellar foo",
    "year": 2014
}'

curl -H "Content-Type: application/json" -XGET '127.0.0.1:9200/movies/_doc/109487?pretty'
```

### search
```
curl -H "Content-Type: application/json" -XGET '127.0.0.1:9200/movies/_search?q=Dark&pretty'
```


