```
curl -H "Content-Type: application/json" -XGET '127.0.0.1:9200/_cluster/state?pretty' >> es-cluster-state.json
curl -H "Content-Type: application/json" -XPUT "http://127.0.0.1:9200/demo-falttened"
curl -H "Content-Type: application/json" -XPUT "127.0.0.1:9200/demo-falttened/_mapping" -d '
{
    "properties": {
        "host": { "type": "flattened" }
    }
}'
curl -H "Content-Type: application/json" -XGET "127.0.0.1:9200/demo-falttened/_mapping?pretty"
curl -H "Content-Type: application/json" -XPUT '127.0.0.1:9200/demo-flattened/_doc/1' -d '{
    "message": "[5592:1:0309/123054.737712:ERROR:child_process_sandbox_support_impl_linux.cc(79)] FontService unique font name matching request did not receive a response.",
    "fileset": {
        "name": "syslog"
    },
    "process": {
        "name": "org.gnome.Shell.desktop",
        "pid": 3383
    },
    "@timestamp": "2020-03-09T18:00:54.000+05:30",
    "host": {
        "hostname": "bionic",
        "name": "bionic"
    }
}'
curl -H "Content-Type: application/json" -XPOST '127.0.0.1:9200/demo-flattened/_update/1' -d '{
    "doc": {
        "host": {
            "osVersion": "Bionic Beaver",
            "osArchitecture": "x86_64"
        }
    }
}'
```