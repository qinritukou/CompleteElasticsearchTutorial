# shakespeare demo
wget http://media.sundog-soft.com/es7/shakes-mapping.json
curl -H "Content-Type: application/json" -XPUT 127.0.0.1:9200/shakespeare --data-binary @shakes-mapping.json

wget http://media.sundog-soft.com/es7/shakespeare_7.0.json
curl -H "Content-Type: application/x-ndjson" -XPOST '127.0.0.1:9200/shakespeare/_bulk' --data-binary "@shakespeare_7.0.json"
curl -H "Content-Type: application/json" -XGET '127.0.0.1:9200/shakespeare/_search?pretty' -d '
{
    "query": {
        "match_phrase": {
            "text_entry": "to be or not to be"
        }
    }
}' 


# some concpet 
1. TF-IDF means: Term Frequency * Inverse Document Frequency
2. Term Frequency: is how often a term appears in a given document
3. Document Frequency: is how often a term appears in all documents 
4. Term Frequency / Document Frequency: measures the relevance of a term in document 
