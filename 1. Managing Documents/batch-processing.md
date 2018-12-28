# Batch processing

batch processing API, for every document, needs two lines.

first line: type of operation (index, update or delete) and matching what id.

second line (delete no need to specify): what to update or add.

## Adding documents

On first line, write what operation to do. (index)

```
POST /product/_doc/_bulk
{ "index": { "_id": "100" } }
{ "price": 100 }
{ "index": { "_id": "101" } }
{ "price": 101 }
```

## Updating and deleting documents

to update, we identify what id to update on the first line, and then write what fields to update in the second. 

```
POST /product/_doc/_bulk
{ "update": { "_id": "100" } }
{ "doc": { "price": 1000 } }
{ "delete": { "_id": "101" } }
```

## Retrieving affected documents

```
GET /product/_doc/100
```

```
GET /product/_doc/101
```