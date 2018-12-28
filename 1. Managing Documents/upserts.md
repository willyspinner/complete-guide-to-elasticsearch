# Upserts

update a document if it exists. Otherwise, insert it.

Update or Insert, hence Upsert.

## Deleting the existing document

```
DELETE /product/_doc/1
```

## Inserting or updating a document (upsert)

turns out, the `_update` endpoint is turned into an upsert when we have an `upsert` field, (i.e. what to insert when the document to be updated doesn't exist.)

```
POST /product/_doc/1/_update
{
    "script" : "ctx._source.price += 5",
    "upsert" : {
        "price" : 100
    }
}
```

## Retrieving the document

```
GET /product/_doc/1
```