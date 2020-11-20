# CISC 525 Module 10 Output of Exercise #5.

You must provide this output as a part of your homework assignment.
You must share this repository with me
For each command you run on Kibana's web console, make sure to provide the input and output of the
command as follows:

## Kibana Console

- command input: Checking the cluster health.

```http

GET /_cluster/health
```

- command output

```json

{
  "cluster_name" : "elasticsearch",
  "status" : "yellow",
  "timed_out" : false,
  "number_of_nodes" : 1,
  "number_of_data_nodes" : 1,
  "active_primary_shards" : 5,
  "active_shards" : 5,
  "relocating_shards" : 0,
  "initializing_shards" : 0,
  "unassigned_shards" : 4,
  "delayed_unassigned_shards" : 0,
  "number_of_pending_tasks" : 0,
  "number_of_in_flight_fetch" : 0,
  "task_max_waiting_in_queue_millis" : 0,
  "active_shards_percent_as_number" : 55.55555555555556
}
```

- alternative curl:
  
```bash

curl -XGET "http://localhost:9200/_cluster/health"
```

- Command input: check nodes - running only single node

```http

GET /_cat/nodes?v

```

- Command output:

```json
ip        heap.percent ram.percent cpu load_1m load_5m load_15m node.role master name
127.0.0.1           13          74   1    0.37    0.26     0.14 dilm      *      student-VirtualBox
```

- Alternative Curl command:

```bash

curl -XGET "http://localhost:9200/_cat/nodes?v"
```

- Command input: checking for indices equivalent to relational DB

```http

GET /_cat/indices?v

```

- Command output:

```json
health status index                    uuid                   pri rep docs.count docs.deleted store.size pri.store.size
green  open   .kibana_task_manager_1   9D3oQE8zQ2-q0qM4XCMITg   1   0          2            1     26.9kb         26.9kb
green  open   .apm-agent-configuration DvPDzd-uRPWLOWR-FlVKbQ   1   0          0            0       283b           283b
green  open   .kibana_1                Tye9xrNRSNufstAaXD6HeA   1   0         22           10     52.5kb         52.5kb
yellow open   products                 Gji8TlbEQWW-X4pDeCD-gQ   2   2          3            0        9kb            9kb

```

- Alternative Curl command:

```bash

curl -XGET "http://localhost:9200/_cat/indices?v"
```

- Command input: Searching everything

```http

GET /.kibana/_search
{
  "query": {
    "match_all": {}
  }
}
```

- Command output:

```json
{
  "took" : 0,
  "timed_out" : false,
  "_shards" : {
    "total" : 1,
    "successful" : 1,
    "skipped" : 0,
    "failed" : 0
  },
  "hits" : {
    "total" : {
      "value" : 22,
      "relation" : "eq"
    },
    "max_score" : 1.0,
    "hits" : [
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "space:default",
        "_score" : 1.0,
        "_source" : {
          "space" : {
            "name" : "Default",
            "description" : "This is your default space!",
            "color" : "#00bfb3",
            "disabledFeatures" : [ ],
            "_reserved" : true
          },
          "type" : "space",
          "references" : [ ],
          "migrationVersion" : {
            "space" : "6.6.0"
          },
          "updated_at" : "2020-03-21T11:56:30.286Z"
        }
      },
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "config:7.6.1",
        "_score" : 1.0,
        "_source" : {
          "config" : {
            "buildNum" : 29118
          },
          "type" : "config",
          "references" : [ ],
          "updated_at" : "2020-03-21T11:56:40.954Z"
        }
      },
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "telemetry:telemetry",
        "_score" : 1.0,
        "_source" : {
          "telemetry" : {
            "userHasSeenNotice" : true
          },
          "type" : "telemetry",
          "references" : [ ],
          "updated_at" : "2020-03-21T11:56:59.847Z"
        }
      },
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "ui-metric:Kibana_home:sampleDataConfirm",
        "_score" : 1.0,
        "_source" : {
          "ui-metric" : {
            "count" : 1
          },
          "type" : "ui-metric",
          "updated_at" : "2020-03-21T12:31:48.378Z"
        }
      },
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "ui-metric:console:PUT_index",
        "_score" : 1.0,
        "_source" : {
          "ui-metric" : {
            "count" : 1
          },
          "type" : "ui-metric",
          "updated_at" : "2020-03-22T13:24:40.385Z"
        }
      },
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "ui-metric:console:DELETE_delete",
        "_score" : 1.0,
        "_source" : {
          "ui-metric" : {
            "count" : 2
          },
          "type" : "ui-metric",
          "updated_at" : "2020-03-25T00:47:47.403Z"
        }
      },
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "ui-metric:console:POST_update",
        "_score" : 1.0,
        "_source" : {
          "ui-metric" : {
            "count" : 6
          },
          "type" : "ui-metric",
          "updated_at" : "2020-03-25T00:46:17.290Z"
        }
      },
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "maps-telemetry:maps-telemetry",
        "_score" : 1.0,
        "_source" : {
          "maps-telemetry" : {
            "settings" : {
              "showMapVisualizationTypes" : false
            },
            "indexPatternsWithGeoFieldCount" : 0,
            "mapsTotalCount" : 0,
            "timeCaptured" : "2020-11-20T03:45:57.131Z",
            "attributesPerMap" : {
              "dataSourcesCount" : {
                "min" : 0,
                "max" : 0,
                "avg" : 0
              },
              "layersCount" : {
                "min" : 0,
                "max" : 0,
                "avg" : 0
              },
              "layerTypesCount" : { },
              "emsVectorLayersCount" : { }
            }
          },
          "type" : "maps-telemetry",
          "references" : [ ],
          "updated_at" : "2020-11-20T03:45:57.131Z"
        }
      },
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "ui-metric:kibana-user_agent:Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:83.0) Gecko/20100101 Firefox/83.0",
        "_score" : 1.0,
        "_source" : {
          "ui-metric" : {
            "count" : 1
          },
          "type" : "ui-metric",
          "references" : [ ],
          "updated_at" : "2020-11-20T03:46:25.432Z"
        }
      },
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "ui-metric:Kibana_home:welcomeScreenMount",
        "_score" : 1.0,
        "_source" : {
          "ui-metric" : {
            "count" : 3
          },
          "type" : "ui-metric",
          "updated_at" : "2020-11-20T03:46:25.434Z"
        }
      }
    ]
  }
}

```

- Alternative Curl command:

```bash

curl -XGET "http://localhost:9200/.kibana/_search"
```

- Command input: Create indices called Pages

```http

PUT /pages

```

- Command output:

```json
{
  "acknowledged" : true,
  "shards_acknowledged" : true,
  "index" : "pages"
}

```

- Alternative Curl command:

```bash

curl -XPUT "http://localhost:9200/pages"
```

- Command input: Check if pages is created

```http

GET /_cat/indices?v

```

- Command output:

```json
health status index                    uuid                   pri rep docs.count docs.deleted store.size pri.store.size
yellow open   pages                    SrwuLOW9TgG_57Sn0ZG-hw   1   1          0            0       230b           230b
green  open   .kibana_task_manager_1   9D3oQE8zQ2-q0qM4XCMITg   1   0          2            1     26.9kb         26.9kb
green  open   .apm-agent-configuration DvPDzd-uRPWLOWR-FlVKbQ   1   0          0            0       283b           283b
green  open   .kibana_1                Tye9xrNRSNufstAaXD6HeA   1   0         22            8     62.6kb         62.6kb
yellow open   products                 Gji8TlbEQWW-X4pDeCD-gQ   2   2          3            0        9kb            9kb


```

- Alternative Curl command:

```bash

curl -XGET "http://localhost:9200/_cat/indices?v"
```

- Command input: Check for shards

```http

GET /_cat/shards?v

```

- Command output:

```json
index                    shard prirep state      docs  store ip        node
.apm-agent-configuration 0     p      STARTED       0   283b 127.0.0.1 student-VirtualBox
.kibana_1                0     p      STARTED      22 70.4kb 127.0.0.1 student-VirtualBox
.kibana_task_manager_1   0     p      STARTED       2 26.9kb 127.0.0.1 student-VirtualBox
pages                    0     p      STARTED       0   230b 127.0.0.1 student-VirtualBox
pages                    0     r      UNASSIGNED                       
products                 1     p      STARTED       1    4kb 127.0.0.1 student-VirtualBox
products                 1     r      UNASSIGNED                       
products                 1     r      UNASSIGNED                       
products                 0     p      STARTED       2  4.9kb 127.0.0.1 student-VirtualBox
products                 0     r      UNASSIGNED                       
products                 0     r      UNASSIGNED                       

```

- Alternative Curl command:

```bash

curl -XGET "http://localhost:9200/_cat/shards?v"
```
- Command input: Delete pages index

```http

DELETE /pages

```

- Command output:

```json
{
  "acknowledged" : true
}

```

- Alternative Curl command:

```bash

curl -XDELETE "http://localhost:9200/pages"
```
- Command input: Check if pages is deleted

```http

GET /_cat/indices?v

```

- Command output:

```json
health status index                    uuid                   pri rep docs.count docs.deleted store.size pri.store.size
green  open   .kibana_task_manager_1   9D3oQE8zQ2-q0qM4XCMITg   1   0          2            1     26.9kb         26.9kb
green  open   .apm-agent-configuration DvPDzd-uRPWLOWR-FlVKbQ   1   0          0            0       283b           283b
green  open   .kibana_1                Tye9xrNRSNufstAaXD6HeA   1   0         22            2     58.4kb         58.4kb
yellow open   products                 Gji8TlbEQWW-X4pDeCD-gQ   2   2          3            0        9kb            9kb


```

- Alternative Curl command:

```bash

curl -XGET "http://localhost:9200/_cat/indices?v"
```
- Command input: Delete products

```http

DELETE /products

```

- Command output:

```json
{
  "acknowledged" : true
}

```

- Alternative Curl command:

```bash

curl -XDELETE "http://localhost:9200/products"
```

- Command input: Create products

```http

PUT /products
{
  "settings": {
    "number_of_shards": 2,
    "number_of_replicas": 2
  }
}

```

- Command output:

```json
{
  "acknowledged" : true,
  "shards_acknowledged" : true,
  "index" : "products"
}

```

- Alternative Curl command:

```bash

curl -XPUT "http://localhost:9200/products" -H 'Content-Type: application/json' -d'{ "settings": { "number_of_shards": 2,"number_of_replicas": 2}}

```

- Command input: Create a document with random-ID

```http

POST /products/_doc
{
  "name": "Coffee Maker",
  "price": 64,
  "in_stock": 10
}

```

- Command output:

```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "vTJa5HUBbFeDIgBo8sNu",
  "_version" : 1,
  "result" : "created",
  "_shards" : {
    "total" : 3,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 0,
  "_primary_term" : 1
}

```

- Alternative Curl command:

```bash

curl -XPOST "http://localhost:9200/products/_doc" -H 'Content-Type: application/json' -d'{ "name": "Coffee Maker",
"price": 64,"in_stock": 10}

```

- Command input: Create a document with random-ID

```http

POST /products/_doc
{
  "name": "Coffee Maker",
  "price": 64,
  "in_stock": 10
}

```

- Command output:

```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "vjJe5HUBbFeDIgBoFsNJ",
  "_version" : 1,
  "result" : "created",
  "_shards" : {
    "total" : 3,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 0,
  "_primary_term" : 1
}


```

- Alternative Curl command:

```bash

curl -XPOST "http://localhost:9200/products/_doc" -H 'Content-Type: application/json' -d'{ "name": "Coffee Maker",
"price": 64,"in_stock": 10}

```

- Command input: Create a document with ID value of 100

```http

POST /products/_doc/100
{
  "name": "Machine Maker",
  "price": 99,
  "in_stock": 12
}

```

- Command output:

```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 1,
  "result" : "created",
  "_shards" : {
    "total" : 3,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 1,
  "_primary_term" : 1
}

```

- Alternative Curl command:

```bash

curl -XPOST "http://localhost:9200/products/_doc/100" -H 'Content-Type: application/json' -d'{"name": "Machine Maker","price": 99,"in_stock": 12}

```

- Command input: Search for products

```http

GET /products/_search

```

- Command output:

```json
{
  "took" : 481,
  "timed_out" : false,
  "_shards" : {
    "total" : 2,
    "successful" : 2,
    "skipped" : 0,
    "failed" : 0
  },
  "hits" : {
    "total" : {
      "value" : 3,
      "relation" : "eq"
    },
    "max_score" : 1.0,
    "hits" : [
      {
        "_index" : "products",
        "_type" : "_doc",
        "_id" : "vjJe5HUBbFeDIgBoFsNJ",
        "_score" : 1.0,
        "_source" : {
          "name" : "Coffee Maker",
          "price" : 64,
          "in_stock" : 10
        }
      },
      {
        "_index" : "products",
        "_type" : "_doc",
        "_id" : "100",
        "_score" : 1.0,
        "_source" : {
          "name" : "Machine Maker",
          "price" : 99,
          "in_stock" : 12
        }
      },
      {
        "_index" : "products",
        "_type" : "_doc",
        "_id" : "vTJa5HUBbFeDIgBo8sNu",
        "_score" : 1.0,
        "_source" : {
          "name" : "Coffee Maker",
          "price" : 64,
          "in_stock" : 10
        }
      }
    ]
  }
}
```

- Alternative Curl command:

```bash

curl -XGET "http://localhost:9200/products/_search"
```

- Command input: get product with specifi ID of 100

```http

GET /products/_doc/100

```

- Command output:

```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 1,
  "_seq_no" : 1,
  "_primary_term" : 1,
  "found" : true,
  "_source" : {
    "name" : "Machine Maker",
    "price" : 99,
    "in_stock" : 12
  }
}
```

- Alternative Curl command:

```bash

curl -XGET "http://localhost:9200/products/_doc/100"
```

- Command input: Search with invalid ID

```http

GET /products/_doc/aefkljwebkjgjwe

```

- Command output:

```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "aefkljwebkjgjwe",
  "found" : false
}

```

- Alternative Curl command:

```bash

curl -XGET "http://localhost:9200/products/_doc/aefkljwebkjgjwe"
```

- Command input: Update in_stock value from 12 to 3

```http

POST /products/_update/100
{
  "doc": {
    "in_stock": 3
  }
}

```

- Command output:

```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 2,
  "result" : "updated",
  "_shards" : {
    "total" : 3,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 2,
  "_primary_term" : 1
}

```

- Alternative Curl command:

```bash

curl -XPOST "http://localhost:9200/products/_update/100" -H 'Content-Type: application/json' -d'{"doc": {"in_stock": 3}}
```
- Command input: Add new fields to products- tags

```http

POST /products/_update/100
{
  "doc": {
    "tags": ["electronics"]
  }
}

```

- Command output:

```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 3,
  "result" : "updated",
  "_shards" : {
    "total" : 3,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 3,
  "_primary_term" : 1
}

```

- Alternative Curl command:

```bash

curl -XPOST "http://localhost:9200/products/_update/100" -H 'Content-Type: application/json' -d'{"doc": {"tags": ["electronics"]}}

```

- Command input: Reduce the in_stock value by 1

```http

POST /products/_update/100
{
  "script": {
    "source": "ctx._source.in_stock--"
  }
}

```

- Command output:

```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 4,
  "result" : "updated",
  "_shards" : {
    "total" : 3,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 4,
  "_primary_term" : 1
}

```

- Alternative Curl command:

```bash

curl -XPOST "http://localhost:9200/products/_update/100" -H 'Content-Type: application/json' -d'{"script": {"source": "ctx._source.in_stock--"}}

```

- Command input: update in_stock value to 10

```http

POST /products/_update/100
{
  "script": {
    "source": "ctx._source.in_stock = 10"
  }
}

```

- Command output:

```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 5,
  "result" : "updated",
  "_shards" : {
    "total" : 3,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 5,
  "_primary_term" : 1
}

```

- Alternative Curl command:

```bash

curl -XPOST "http://localhost:9200/products/_update/100" -H 'Content-Type: application/json' -d'{"script": {"source": "ctx._source.in_stock = 10"}}

```

- Command input: Delete document by ID 100

```http

DELETE /products/_doc/100

```

- Command output:

```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 6,
  "result" : "deleted",
  "_shards" : {
    "total" : 3,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 6,
  "_primary_term" : 1
}

```

- Alternative Curl command:

```bash

curl -XDELETE "http://localhost:9200/products/_doc/100"

```

- Command input: Verify product with ID 100 is Deleted

```http

GET /products/_search

```

- Command output:

```json
{
  "took" : 116,
  "timed_out" : false,
  "_shards" : {
    "total" : 2,
    "successful" : 2,
    "skipped" : 0,
    "failed" : 0
  },
  "hits" : {
    "total" : {
      "value" : 2,
      "relation" : "eq"
    },
    "max_score" : 1.0,
    "hits" : [
      {
        "_index" : "products",
        "_type" : "_doc",
        "_id" : "vjJe5HUBbFeDIgBoFsNJ",
        "_score" : 1.0,
        "_source" : {
          "name" : "Coffee Maker",
          "price" : 64,
          "in_stock" : 10
        }
      },
      {
        "_index" : "products",
        "_type" : "_doc",
        "_id" : "vTJa5HUBbFeDIgBo8sNu",
        "_score" : 1.0,
        "_source" : {
          "name" : "Coffee Maker",
          "price" : 64,
          "in_stock" : 10
        }
      }
    ]
  }
}

```

- Alternative Curl command:

```bash

curl -XGET "http://localhost:9200/products/_search"
```

- Command input: Delete test-index

```http

DELETE test-index

```

- Command output:

```json
{
  "error" : {
    "root_cause" : [
      {
        "type" : "index_not_found_exception",
        "reason" : "no such index [test-index]",
        "resource.type" : "index_or_alias",
        "resource.id" : "test-index",
        "index_uuid" : "_na_",
        "index" : "test-index"
      }
    ],
    "type" : "index_not_found_exception",
    "reason" : "no such index [test-index]",
    "resource.type" : "index_or_alias",
    "resource.id" : "test-index",
    "index_uuid" : "_na_",
    "index" : "test-index"
  },
  "status" : 404
}

```

- Alternative Curl command:

```bash

curl -XDELETE "http://localhost:9200/test-index"

```

- Command input: Create airport index

```http

PUT airport

```

- Command output:

```json
{
  "acknowledged" : true,
  "shards_acknowledged" : true,
  "index" : "airport"
}

```

- Alternative Curl command:

```bash

curl -XPUT "http://localhost:9200/airport"

```

- Command input: Delete airport index

```http

DELETE airport

```

- Command output:

```json
{
  "acknowledged" : true
}

```

- Alternative Curl command:

```bash

curl -XDELETE "http://localhost:9200/airport"

```

- Command input: Search "my-index" index 

```http

GET /my-index/_search

```

- Command output:

```json
{
  "error" : {
    "root_cause" : [
      {
        "type" : "index_not_found_exception",
        "reason" : "no such index [my-index]",
        "resource.type" : "index_or_alias",
        "resource.id" : "my-index",
        "index_uuid" : "_na_",
        "index" : "my-index"
      }
    ],
    "type" : "index_not_found_exception",
    "reason" : "no such index [my-index]",
    "resource.type" : "index_or_alias",
    "resource.id" : "my-index",
    "index_uuid" : "_na_",
    "index" : "my-index"
  },
  "status" : 404
}
```

- Alternative Curl command:

```bash

curl -XGET "http://localhost:9200/my-index/_search"

```

- Command input: Search "test-index" index

```http

GET /test-index/_search

```

- Command output:

```json
{
  "error" : {
    "root_cause" : [
      {
        "type" : "index_not_found_exception",
        "reason" : "no such index [test-index]",
        "resource.type" : "index_or_alias",
        "resource.id" : "test-index",
        "index_uuid" : "_na_",
        "index" : "test-index"
      }
    ],
    "type" : "index_not_found_exception",
    "reason" : "no such index [test-index]",
    "resource.type" : "index_or_alias",
    "resource.id" : "test-index",
    "index_uuid" : "_na_",
    "index" : "test-index"
  },
  "status" : 404
}
```

- Alternative Curl command:

```bash

curl -XGET "http://localhost:9200/test-index/_search"

```
