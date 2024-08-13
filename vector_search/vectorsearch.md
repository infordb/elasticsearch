## simple example

```
DELETE image-index

PUT /image-index
{
  "mappings": {
    "properties": {
      "image-vector": {
        "type": "dense_vector",
        "dims": 3,
        "index": true,
        "similarity": "l2_norm"
      },
      "title-vector": {
        "type": "dense_vector",
        "dims": 5,
        "index": true,
        "similarity": "l2_norm"
      },
      "title": {
        "type": "text"
      },
      "file-type": {
        "type": "keyword"
      }
    }
  }
}


POST /image-index/_bulk?refresh=true
{ "index": { "_id": "1" } }
{ "image-vector": [1, 5, -20], "title-vector": [12, 50, -10, 0, 1], "title": "moose family", "file-type": "jpg" }
{ "index": { "_id": "2" } }
{ "image-vector": [42, 8, -15], "title-vector": [25, 1, 4, -12, 2], "title": "alpine lake", "file-type": "png" }
{ "index": { "_id": "3" } }
{ "image-vector": [15, 11, 23], "title-vector": [1, 5, 25, 50, 20], "title": "full moon", "file-type": "jpg" }


## search
POST /image-index/_search
{
  "knn": {
    "field": "image-vector",
    "query_vector": [-5, 9, -12],
    "k": 10,
    "num_candidates": 100
  },
  "fields": [ "title", "file-type" ]
}


## search except _source 
POST /image-index/_search
{
  "knn": {
    "field": "image-vector",
    "query_vector": [-5, 9, -12],
    "k": 10,
    "num_candidates": 100
  },
  "fields": [ "title", "file-type" ],
  "_source": false
}

```

## exclude _source (vector field)
```

DELETE image-index

PUT /image-index
{
  "mappings": {
    "_source": {
      "excludes": [
        "image-vector",
        "title-vector"
      ]
    },    
    "properties": {
      "image-vector": {
        "type": "dense_vector",
        "dims": 3,
        "index": true,
        "similarity": "l2_norm"
      },
      "title-vector": {
        "type": "dense_vector",
        "dims": 5,
        "index": true,
        "similarity": "l2_norm"
      },
      "title": {
        "type": "text"
      },
      "file-type": {
        "type": "keyword"
      }
    }
  }
}

```



