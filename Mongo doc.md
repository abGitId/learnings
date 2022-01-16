## Mongo doc::
https://www.mongodb.com/try/download/tools

###### To import json collection:

```
syntax:
mongoimport --db <dbname> --collection <collectionName> --file <example>.json --drop
```

e.g

```
mongoimport --db flightmgtm --collection aircraft --file D:\practice\mongo\02\demos\sampledb\aircraft.json --drop
mongoimport --db flightmgtm --collection aircraft --file D:\practice\mongo\02\demos\sampledb\flights.json --drop
```



###### To check the count

```
db.<collectionName>.count()
db.aircraft.count()
```



###### display data

```
db.<collectionName>.find()
db.aircraft.find()

db.<collectionName>.find().pretty()
db.aircraft.find().pretty();
```



###### find

```
find(query,projection)
query: (optional) filtering using query methods
projection: (optional) specify which fields to display/hide
```



###### document projection structure

```
find({},{field1:value1, field2:value2})

field: name of the field to be included or excluded
value: 1 for inclusion and 0 for exclusion
```



###### Sort method

```
db.<collectionName>.find({},{}).sort({field1:value1, field2:value2})
field: name of the field you want to sort
value: 1 for ascending order and -1 for descending
```



---------------------------------
###### Document query structure

```
{field:{$operator:value}}
 
```

###### operators:

$eq = equal
$ne = not equal
$in = in query
$nin = not in query

$lt = less than
$lte = less than equal
$gt = greater than
$gte = greater than equal

###### equal 

```
db.flights.find({duration:120}, {duration:1, "departure.city":1}).pretty();
```



###### or

```
db.flights.find({duration:{$eq:120}}, {duration:1, "departure.city":1}).pretty();
```



###### Not equal

```
db.flights.find({duration:{$ne:120}}, {duration:1, "departure.city":1}).pretty();
```



###### AND operator

find Flight duration less than 2 hrs and all are international flight

```
db.flight.find({$and:[field1:"val", field2:"val"]},{});

db.flights.find({$and:[{duration:{$lt:120}}, {type:"International"}]},{});

db.flights.find({"crew.nationality":"German"},{"crew.nationality":1});
```



###### free text search

-free text support for string and array of string fields

- we can not perform free test search without a text Index

###### creating text index:

```
db.<collectionName>.createIndex({field1: "text", field2: "text"})
e.g
db.crew.createIndex({name:"text"})

db.crew.find({$search:{$text:"free text search string"}},{})
```



###### Sorting by relevance

we can aggregate result by score using $meta projection operator

```
db.crew.find({$search:{$text:"free text search string"}},{score: {$meta:"textScore"}})

db.flights.find({}, {duration:1, "departure.city":1}).pretty();

db.flights.find({}, {duration:1, "departure.city":1}).pretty().sort({duration:-1});


```

###### for pagination we can use limit & skip

```
db.flights.find({}, {duration:1, "departure.city":1}).pretty().sort({duration:-1}).limit(2);

db.flights.find({}, {duration:1, "departure.city":1}).pretty().sort({duration:-1}).limit(2).skip(4);
```




--------------------------------
###### like query in mongo::

```
syntax:

db.<collection>.find.
{"model":{$regex :'Boeig', $options: "i"}}
```

