# ElasticSearch Logstash & Kibana or ELK Stack Sample

Commands that you may want to copy and paste into your Kibana console

```http

# check the health of cluster
GET /_cluster/health

#check nodes - running only single node
GET /_cat/nodes?v

# checking for indices equivalent to relational DB
GET /_cat/indices?v

#Searching everything
GET /.kibana/_search
{
  "query": {
    "match_all": {}
  }
}

GET /_cat/indices?v

#Create indices of Pages
PUT /pages
# Check if pages is created
GET /_cat/indices?v

#check for shards
GET /_cat/shards?v

DELETE /pages

# Check if pages is Deleted
GET /_cat/indices?v

DELETE /products

#Create products, with number of shards and replicas
PUT /products
{
  "settings": {
    "number_of_shards": 2,
    "number_of_replicas": 2
  }
}
#Create a document type/table
# Create with random ID
POST /products/_doc
{
  "name": "Coffee Maker",
  "price": 64,
  "in_stock": 10
}
# Create with random ID
POST /products/_doc
{
  "name": "Coffee Maker",
  "price": 64,
  "in_stock": 10
}
# Create with id value of 100
POST /products/_doc/100
{
  "name": "Machine Maker",
  "price": 99,
  "in_stock": 12
}

# search for products
GET /products/_search

# get product with specifi ID
GET /products/_doc/100

#Search with invalid ID
GET /products/_doc/aefkljwebkjgjwe

#Update document update in_stock value 12 to 3
POST /products/_update/100
{
  "doc": {
    "in_stock": 3
  }
}

#Add new fields - tags
POST /products/_update/100
{
  "doc": {
    "tags": ["electronics"]
  }
}

#reduce in_stock value by 1
POST /products/_update/100
{
  "script": {
    "source": "ctx._source.in_stock--"
  }
}
#Update stock value to 10
POST /products/_update/100
{
  "script": {
    "source": "ctx._source.in_stock = 10"
  }
}

# Delete document by ID
DELETE /products/_doc/100

DELETE test-index

# Create airport
PUT airport

DELETE airport

#Searrch "my-index" index 
GET /my-index/_search

#Searrch "test-index" index 
GET /test-index/_search

```
