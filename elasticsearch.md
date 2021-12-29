Structured queries.
Full-text queries.



https://www.elastic.co/guide/en/elastic-stack-get-started/7.3/get-started-elastic-stack.html

curl -L -O https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.3.2-darwin-x86_64.tar.gz
tar -xzvf elasticsearch-7.3.2-darwin-x86_64.tar.gz
cd elasticsearch-7.3.2
./bin/elasticsearch
http://127.0.0.1:9200/

curl -L -O https://artifacts.elastic.co/downloads/kibana/kibana-7.3.2-darwin-x86_64.tar.gz
tar xzvf kibana-7.3.2-darwin-x86_64.tar.gz
cd kibana-7.3.2-darwin-x86_64/
./bin/kibana
http://localhost:5601

curl -L -O https://artifacts.elastic.co/downloads/beats/metricbeat/metricbeat-7.3.2-darwin-x86_64.tar.gz
tar xzvf metricbeat-7.3.2-darwin-x86_64.tar.gz
cd metricbeat-7.3.2-darwin-x86_64
./metricbeat modules enable system
./metricbeat -e
https://www.elastic.co/guide/en/elastic-stack-get-started/7.3/get-started-elastic-stack.html

curl -L -O https://artifacts.elastic.co/downloads/logstash/logstash-7.3.2.tar.gz
tar -xzvf logstash-7.3.2.tar.gz
cd logstash-7.3.2
./bin/logstash -f path/to/config/demo-metrics-pipeline.conf


#Start Elastic Search
cd elasticsearch-6.6.1/bin
./elasticsearch

http://127.0.0.1:9200/

Start two more instances of Elasticsearch
./elasticsearch -Epath.data=data2 -Epath.logs=log2
./elasticsearch -Epath.data=data3 -Epath.logs=log3

1. Health check
`http://127.0.0.1:9200/_cat/health?v`

2. Index Document

`curl -X PUT "localhost:9200/customer/_doc/1?pretty" -H 'Content-Type: application/json' -d'
{
  "name": "John Doe"
}
'`
3. Get Dcoument

curl -X GET "localhost:9200/customer/_doc/1?pretty"

4. Index the account data into the bank index with the following _bulk request:

curl -H "Content-Type: application/json" -XPOST "localhost:9200/bank/_bulk?pretty&refresh" --data-binary "@accounts.json"
curl "localhost:9200/_cat/indices?v"

5. retrieves all documents in the bank index sorted by account number:
curl -X GET "localhost:9200/bank/_search?pretty" -H 'Content-Type: application/json' -d'
{
  "query": { "match_all": {} },
  "sort": [
    { "account_number": "asc" }
  ]
}
'
6. find customers whose addresses contain mill or lane:

curl -X GET "localhost:9200/bank/_search?pretty" -H 'Content-Type: application/json' -d'
{
  "query": { "match": { "address": "mill lane" } }
}
'
7. request only matches addresses that contain the phrase mill lane:

curl -X GET "localhost:9200/bank/_search?pretty" -H 'Content-Type: application/json' -d'
{
  "query": { "match_phrase": { "address": "mill lane" } }
}
'

8. customers who are 40 years old, but excludes anyone who lives in Idaho (ID):

curl -X GET "localhost:9200/bank/_search?pretty" -H 'Content-Type: application/json' -d'
{
  "query": {
    "bool": {
      "must": [
        { "match": { "age": "40" } }
      ],
      "must_not": [
        { "match": { "state": "ID" } }
      ]
    }
  }
}
'

9. a balance between $20,000 and $30,000 (inclusive).

curl -X GET "localhost:9200/bank/_search?pretty" -H 'Content-Type: application/json' -d'
{
  "query": {
    "bool": {
      "must": { "match_all": {} },
      "filter": {
        "range": {
          "balance": {
            "gte": 20000,
            "lte": 30000
          }
        }
      }
    }
  }
}
'

Analyze results with aggregationsedit

10. For example, the following request uses a terms aggregation to group all of the accounts in the bank index by state, and returns the ten states with the most accounts in descending order:

Because the request set size=0, the response only contains the aggregation results.

curl -X GET "localhost:9200/bank/_search?pretty" -H 'Content-Type: application/json' -d'
{
  "size": 0,
  "aggs": {
    "group_by_state": {
      "terms": {
        "field": "state.keyword"
      }
    }
  }
}
'

11. For example, the following request nests an avg aggregation within the previous group_by_state aggregation to calculate the average account balances for each state.
curl -X GET "localhost:9200/bank/_search?pretty" -H 'Content-Type: application/json' -d'
{
  "size": 0,
  "aggs": {
    "group_by_state": {
      "terms": {
        "field": "state.keyword"
      },
      "aggs": {
        "average_balance": {
          "avg": {
            "field": "balance"
          }
        }
      }
    }
  }
}
'
12. you could sort using the result of the nested aggregation by specifying the order within the terms aggregation:
curl -X GET "localhost:9200/bank/_search?pretty" -H 'Content-Type: application/json' -d'
{
  "size": 0,
  "aggs": {
    "group_by_state": {
      "terms": {
        "field": "state.keyword",
        "order": {
          "average_balance": "desc"
        }
      },
      "aggs": {
        "average_balance": {
          "avg": {
            "field": "balance"
          }
        }
      }
    }
  }
}
'
https://www.elastic.co/guide/en/elasticsearch/reference/current/settings.html

Aggregations 



View All Index

`http://127.0.0.1:9200/_cat/indices?h=index`

View All Data of Index

`http://127.0.0.1:9200/nutraj/_search?pretty=true` (nutraj is index name)
