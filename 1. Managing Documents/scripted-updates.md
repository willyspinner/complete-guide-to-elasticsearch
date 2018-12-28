# Scripted updates

## Updating a document with a script

NOTE: ```ctx._source``` is the original document.



```
POST /product/_doc/1/_update
{
  "script": "ctx._source.price += 10"
}
```

## Retrieving the updated document

```
GET /product/_doc/1
```