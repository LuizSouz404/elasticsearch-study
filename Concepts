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


