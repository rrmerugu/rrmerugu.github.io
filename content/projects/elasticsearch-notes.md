---
layout: post
title: "Elasticsearch Notes on Queries "
subtitle: "Notes on Elasticsearch "
categories: Code
tags: ["Elasticsearch",]
date: 2020-06-16
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
