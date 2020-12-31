# change the number of primary shards later
PUT /testindex 
{
    "settings": {
        "number_of_shards": 3,
        "number_of_replicas": 1
    }
}