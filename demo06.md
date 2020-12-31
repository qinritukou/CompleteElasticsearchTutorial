# deal with concurrency control

###
```
curl -H "Content-Type: application/json" -XGET '127.0.0.1:9200/movies/_doc/109487?pretty'
curl -H "Content-Type: application/json" -XPUT '127.0.0.1:9200/movies/_doc/109487?if_seq_no=5&if_primary_term=1' -d '
{
    "genres": ["IMAX", "Sci-Fi"],
    "title": "Interestellar foo",
    "year": 2014
}'

curl -H "Content-Type: application/json" -XPOST '127.0.0.1:9200/movies/_doc/109487/_update?retry_on_conflict=5' -d '{
    "doc": {
        "title": "Interstellar typo"
    }
}'
```