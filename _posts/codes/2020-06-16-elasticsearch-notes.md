---
layout: post
title: "Elasticsearch Notes on Queries "
tagline: "Notes on Elasticsearch "
category: Code
skills: ["Elasticsearch",]
---


# To find records with no field `product_count`.
```
GET /shop_data/_count
{
  "query": {
        "bool": {
          "must_not": [
            {
              "exists": {
                "field": "product_count"
              }
            }
          ]
        }
  }

}
```

#### To add a field with default value if the field doesnt exist

```
POST /shop_data/_update_by_query
{
   "query": {
        "bool": {
          "must_not": [
            {
              "exists": {
                "field": "product_count"
              }
            }
          ]
        }
  },
  "script" : {
    "inline" : "ctx._source.product_count= 0;"
  }
}
```
