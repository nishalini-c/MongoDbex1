# MongoDbex1
**1. Create a Database called customers.**
 ```
  use customer
```
**2. Create a collection called customerdetails.**
```
db.createCollection("customerdetails")
```
**3. Insert all documents into the collection named customer details**
```
customers> db.customerdetails.insertMany([{name:"john",age:25,gender:"male",city:"New york"},{name:"Emily",age:22,gender:"Female",city:"London"},{name:"Daniel",age:28,gender:"male",city:"Sydney"},{name:"Sophia",age:24,gender:"Female",city:"Paris"},{name:"William",age:26,gender:"male",city:"Chicago"},{name:"Olivia",age:23,gender:"Female",city:"Los Angeles"},{name:"Benjamin",age:27,gender:"male",city:"Toronto"},{name:"Mila",age:29,gender:"Female",city:"Berlin"},{name:"James",age:30,gender:"male",city:"Tokyo"}])
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId("654ca46dd4532536a0d3f1f5"),
    '1': ObjectId("654ca46dd4532536a0d3f1f6"),
    '2': ObjectId("654ca46dd4532536a0d3f1f7"),
    '3': ObjectId("654ca46dd4532536a0d3f1f8"),
    '4': ObjectId("654ca46dd4532536a0d3f1f9"),
    '5': ObjectId("654ca46dd4532536a0d3f1fa"),
    '6': ObjectId("654ca46dd4532536a0d3f1fb"),
    '7': ObjectId("654ca46dd4532536a0d3f1fc"),
    '8': ObjectId("654ca46dd4532536a0d3f1fd")
  }
}
```
**04. Retrieve all documents from the collection and sort the results by the “age” field in ascending order.**
```customers> db.customerdetails.find().sort({age:1}).pretty()
[
  {
    _id: ObjectId("654ca46dd4532536a0d3f1f6"),
    name: 'Emily',
    age: 22,
    gender: 'Female',
    city: 'London'
  },
  {
    _id: ObjectId("654ca46dd4532536a0d3f1fa"),
    name: 'Olivia',
    age: 23,
    gender: 'Female',
    city: 'Los Angeles'
  },
  {
    _id: ObjectId("654ca46dd4532536a0d3f1f8"),
    name: 'Sophia',
    age: 24,
    gender: 'Female',
    city: 'Paris'
  },
  {
    _id: ObjectId("654ca46dd4532536a0d3f1f5"),
    name: 'john',
    age: 25,
    gender: 'male',
    city: 'New york'
  },
  {
    _id: ObjectId("654ca46dd4532536a0d3f1f9"),
    name: 'William',
    age: 26,
    gender: 'male',
    city: 'Chicago'
  },
  {
    _id: ObjectId("654ca46dd4532536a0d3f1fb"),
    name: 'Benjamin',
    age: 27,
    gender: 'male',
    city: 'Toronto'
  },
  {
    _id: ObjectId("654ca46dd4532536a0d3f1f7"),
    name: 'Daniel',
    age: 28,
    gender: 'male',
    city: 'Sydney'
  },
  {
    _id: ObjectId("654ca46dd4532536a0d3f1fc"),
    name: 'Mila',
    age: 29,
    gender: 'Female',
    city: 'Berlin'
  },
  {
    _id: ObjectId("654ca46dd4532536a0d3f1fd"),
    name: 'James',
    age: 30,
    gender: 'male',
    city: 'Tokyo'
  }
]
```
**5. Count the number of females.**
```
 db.customerdetails.countDocuments({gender:"Female"})
4
```
**6. Insert one document into the customerdetails collection.**
```
db.customerdetails.insertOne({name:"Nilax",age:"24",gender:"Male",city:"jaffna"})
{
  acknowledged: true,
  insertedId: ObjectId("654ca916d4532536a0d3f1fe")
}
```
**07. Update city=SriLanka to John.**
```
db.customerdetails.update({name:"john",age:25,gender:"male"},{$set:{city:"Srilanka"}},{upsert:"true"})
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
```
**08. Remove the customer from Tokyo.**
```
 db.customerdetails.remove({name:"Jams",age:30,gender:"male",city:"Tokyo"})
{ acknowledged: true, deletedCount: 0 }
```
**09. Find customers not from Los Angeles.**
```
db.customerdetails.find({city:{$ne:"Los Angeles"}})
[
  {
    _id: ObjectId("654ca46dd4532536a0d3f1f5"),
    name: 'john',
    age: 25,
    gender: 'male',
    city: 'Srilanka'
  },
  {
    _id: ObjectId("654ca46dd4532536a0d3f1f6"),
    name: 'Emily',
    age: 22,
    gender: 'Female',
    city: 'London'
  },
  {
    _id: ObjectId("654ca46dd4532536a0d3f1f7"),
    name: 'Daniel',
    age: 28,
    gender: 'male',
    city: 'Sydney'
  },
  {
    _id: ObjectId("654ca46dd4532536a0d3f1f8"),
    name: 'Sophia',
    age: 24,
    gender: 'Female',
    city: 'Paris'
  },
  {
    _id: ObjectId("654ca46dd4532536a0d3f1f9"),
    name: 'William',
    age: 26,
    gender: 'male',
    city: 'Chicago'
  },
  {
    _id: ObjectId("654ca46dd4532536a0d3f1fb"),
    name: 'Benjamin',
    age: 27,
    gender: 'male',
    city: 'Toronto'
  },
  {
    _id: ObjectId("654ca46dd4532536a0d3f1fc"),
    name: 'Mila',
    age: 29,
    gender: 'Female',
    city: 'Berlin'
  },
  {
    _id: ObjectId("654ca916d4532536a0d3f1fe"),
    name: 'Nilax',
    age: '24',
    gender: 'Male',
    city: 'jaffna'
  }
]
```
**10. Find the customers who are older than age 25**
```
db.customerdetails.find({ age: { $gt: 25 } })
[
  {
    _id: ObjectId("654ca46dd4532536a0d3f1f7"),
    name: 'Daniel',
    age: 28,
    gender: 'male',
    city: 'Sydney'
  },
  {
    _id: ObjectId("654ca46dd4532536a0d3f1f9"),
    name: 'William',
    age: 26,
    gender: 'male',
    city: 'Chicago'
  },
  {
    _id: ObjectId("654ca46dd4532536a0d3f1fb"),
    name: 'Benjamin',
    age: 27,
    gender: 'male',
    city: 'Toronto'
  },
  {
    _id: ObjectId("654ca46dd4532536a0d3f1fc"),
    name: 'Mila',
    age: 29,
    gender: 'Female',
    city: 'Berlin'
  }
]
```
**11. Retrieve the males who are less than 25.**
```
 db.customerdetails.find({ gender: "Male", age: { $lt: 25 } })

```
**12. Update Francis age to 35, if Francis is not available upsert.**
```
coustomers> db.customerdetails.updateOne({ name: "Francis" }, { $set: { age: 35 } }, { upsert: true })
{
  acknowledged: true,
  insertedId: ObjectId("654cf983852f81b55f76d1b5"),
  matchedCount: 0,
  modifiedCount: 0,
  upsertedCount: 1
}
```
**13. Retrieve males who are younger than 30 and older than25.**
```
 db.customerdetails.find({ gender:"male" , age: { $gt:25, $lt:30}})
[
  {
    _id: ObjectId("654cf95e2eefc34f08a3fb0b"),
    name: 'Daniel',
    age: 28,
    gender: 'male',
    city: 'Sydney'
  },
  {
    _id: ObjectId("654cf95e2eefc34f08a3fb0d"),
    name: 'William',
    age: 26,
    gender: 'male',
    city: 'Chicago'
  },
  {
    _id: ObjectId("654cf95e2eefc34f08a3fb0f"),
    name: 'Benjamin',
    age: 27,
    gender: 'male',
    city: 'Toronto'
  }
]

```
**14. Find a customer who is lesser than or equal to 23.**
```
coustomers> db.customerdetails.findOne({ age: { $lte: 23 } })
{
  _id: ObjectId("654cf95e2eefc34f08a3fb0a"),
  name: 'Emily',
  age: 22,
  gender: 'Female',
  city: 'London'
}
```
**15. Remove the customer from Tokyo.**
```
db.customerdetails.remove({name:"Jams",age:30,gender:"male",city:"Tokyo"})
{ acknowledged: true, deletedCount: 0 }
```

