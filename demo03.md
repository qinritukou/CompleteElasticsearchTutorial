### mapping
A mapping is a schema defition. elasticsearch has reasonable defaults, but sometimes you need to customize them.
```
curl -XPUT 127.0.0.1:9200/movies -d '
{
    "mappings": {
        "properties": {
            "year": {"type": "date"}
        }
    }
}
'
```

### common mappings
1. Field types
    ```
    "properties": {
        "user_id": {
            "type": "long"
        }
    }
    ```
2. Field Index
    ```
    "properties": {
        "genre": {
            "index": "not_analyzed"
        }
    }
    ```
3. Field Analyzer
    ```
    "properties": {
        "description": {
            "analyzer": "english"
        }
    }
    ```
    1. Character Filters: Remove HTML encoding, convert & to and
    2. Tokenizer: Split strings on whitespace / punctuation / non-letters
    3. Token Filter: Lowercasing, stemming, synonyms, stopwords