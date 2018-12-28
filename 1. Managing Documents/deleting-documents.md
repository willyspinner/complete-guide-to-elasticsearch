# Deleting documents

## Deleting document by ID

```
DELETE /product/_doc/1
```

## Adding test documents

```
POST /product/_doc
{
  "name": "Processing Events with Logstash",
  "category": "course"
}
```

```
POST /product/_doc
{
  "name": "The Art of Scalability",
  "category": "book"
}
```

## Deleting documents by query

this is available at the index level. We basically delete documents by our match query to the our document's `category` field.

```
POST /product/_delete_by_query
{
  "query": {
    "match": {
      "category": "book"
    }
  }
}
```

(we will look at match queries later in the future).

NOTE: it doesn't have to be a match query. It can be other queries.

