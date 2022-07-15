# First commands with ElasticSearch

> This section we are going to pass all shakespeare script to our elasticsearch

## So letsgo
first of all

We need to create a elasticsearch service, so we have an basic configuration in **ElasticConfigure**

run the docker-compose.yml

``` bash
docker compose up -d # this way you running with detach mode
# or 
docker compose up # this way you will see the logs
```
Run this command to see if our elastic already running
```bash
curl -X GET "localhost:9200"

# if return this is because already running 
{
  "name" : "elasticsearch",
  "cluster_name" : "es-docker-cluster",
  "cluster_uuid" : "Jr6CRPLoQlS_O__k0Tp2ww",
  "version" : {
    "number" : "7.7.1",
    "build_flavor" : "default",
    "build_type" : "docker",
    "build_hash" : "ad56dce891c901a492bb1ee393f12dfff473a423",
    "build_date" : "2020-05-28T16:30:01.040088Z",
    "build_snapshot" : false,
    "lucene_version" : "8.5.1",
    "minimum_wire_compatibility_version" : "6.8.0",
    "minimum_index_compatibility_version" : "6.0.0-beta1"
  },
  "tagline" : "You Know, for Search"
}
```

We is two simple commands, just to test elastic

``` bash
curl -X PUT "localhost:9200/my-index-000001?pretty"

curl -X GET "localhost:9200/my-index-000001/_doc/0?_source=false&pretty"
# going to return this
{
  "_index" : "my-index-000001",
  "_type" : "_doc",
  "_id" : "0",
  "found" : false
}
```

Right, now we are download an mapping (we could create a one too) and going to pass the mapping in request, this mapping is just like an schema.


``` bash
# downloading mapping
wget http://media.sundog-soft.com/es7/shakes-mapping.json

#create an index that will have the mapping chema
curl -H "Content-Type: application/json" -XPUT localhost:9200/shakespeare --data-binary @shakes-mapping.json  
```

And now we download the Shakespeare script and post it on ElasticSearch's "Shakespeare" index

``` bash
# download script
wget http://media.sundog-soft.com/es7/shakespeare_7.0.json

# making a post do shakespeare index
curl -H "Content-Type: application/json" -XPOST localhost:9200/shakespeare/_bulk?pretty --data-binary @shakespeare_7.0.json
```

Now we have all the Shakespeare script in our elasticsearch, this way we can make quick requests for some speech or character using Elastic GET requests

``` bash
curl -H "Content-Type: application/json" -XGET "http://localhost:9200/shakespeare/_search?pretty" -d "{\"query\": {\"match_phrase\": {\"text_entry\" : \"to be or not to be\"}}}"
```