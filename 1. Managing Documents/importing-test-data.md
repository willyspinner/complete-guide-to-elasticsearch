# Importing test data

## Importing test data with cURL

```
curl -H "Content-Type: application/json" -XPOST 'http://localhost:9200/product/_doc/_bulk?pretty' --data-binary "@products-bulk.json"
```

WHERE `products-bulk.json` contains the structured bulk operations mentioned in batch operations.

