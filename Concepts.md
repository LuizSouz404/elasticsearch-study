# Elasticsearch
General concepts

* Horizontally scalable search engine
* Each Shard is an inverted document index
* In addition to searching:
   * Supports structured data
   * Can aggregate data quickly
* Elasticsearch is basically an api rest, so its use is universal because with a simple HTTP request you can send and receive data.


# Kibana
General concepts

* Web interface for searching and viewing
* Complex aggregations, graphs, graphs and dashboards
* Widely used for log analysis

# Logstash & Beats
General concepts

* Data ingestion into Elasticsearch
* Filebeat can monitor log files, analyze and import them into Elasticsearch near-real-time
* Lostash can import data from multiple computers
* Not only used for log data

# X-pack (paid function)
General concepts

* Safety
* Alerts
* Monitoring
* Reports
* Machine Learning
* Graphs


# CONCEPTS API REST

## HTTP request
* Method: the request verb (GET, POST, PUT or DELETE)
* Protocol: which version of http (http/1.1)
* Host: which server do you want to send the request to
* URL: what resources are being requested
* Body: other necessary data
Headers: user-agent, content-type, etc.

### Representational State Transfer

Six characteristics
1. Client server architecture
2. Statelessness
3. Cacheability
4. Layered
5. On Demand
6. Uniform Interface

example Curl command

curl -H <Headers> <URL> <Method (-XGET,-XPOST,-XPUT)> -d <Body>


# Logical concepts

## Document

* Document is data you can search.
* They can be more than text.
* ElasticSearch is built on top of JSON.
* Each document has a unique ID and a type

## Index

* An index powers a search of all documents in a collection
* They contain an inverted index, which allows you to search everywhere at once

Analogy

Cluster => Database
Index => Tables
Document => rows

# Whats is a **Inverted Index**

look this example, we have two sentences a little bit equal

*Document 1*: Space: the final frontier. These are the trips

*Document 2*: He's bad, he's number one. He's the space cowboy with the laser gun!

*Inverted Index*
They appear in both documents and is how inverted index works

Space: 1,2
the: 1,2
final: 1
frontier: 1
He: 2
Bad: 2


* **TF-IDF**: Term Frequency * Inverse Document Frequency

* **Term Frequency**: Frequency with which an word appears ina document

* **Document Frequency**: It is the frequency with which a word appears in all document

* **Relevancy**: Term Frequency / Document Frequency, measure in an document

Scalability capacity

Index calling "shards"

Cluster are a set of computers that process data together 

An index is divided in shards
DOcuments are attributed to an specific shard

each shard could be in different node of an cluster
each shard is an index Lucene independent

## Shard is primary and replica

This index have two shards primary and two replica. You application must intersperse the request between node

The write request is directed to the primary shard, and then to the replica
The read request is directed to the primary shard or any other replica

We can set the amount of shards and replicas per http request,

for each shards there is a replica, in case each shards has a replica. Assuming there are 3 shards that each have 1 replica the total is 6

shards     1 ---- 2 ---- 3
           |      |      |
replica    1      1      1
total      2   +  2   +  2  = 6

Now if you have 3 shards and each shard has 2 replicas then there will be 9 shards

shards     1 ---- 2 ---- 3
           |      |      |
replica 1  1      1      1
replica 2  1      1      1
total      3   +  3  +   3   = 9