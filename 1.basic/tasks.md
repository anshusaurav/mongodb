#### write commands for following mongodb opertaions

1. create a database named `sports`

```js
 use sports

```
2. list all databases present in local mongod server.

```js
 show dbs
```
3. create 3 collections named `cricket`, `football`, `TT` in sports database.

```js
 db.createCollection('cricket');
 db.createCollection('football')
 db.createCollection('TT')
```

4. add 3 players in each of above collections which should have fields like `name`, `age`, `email`, state and auction_price.\

```js
db.cricket.insert({'name': 'Anshu','age': 28, 'email': 'anshu.saurav@gmail.com'})
db.cricket.insert({'name': 'Rishabh','age':26, 'email':'rishabhrocky@gmail.com'})
db.cricket.insert({'name': 'Vivek','age':27, 'email':'vivekbrh01@gmail.com'})

db.football.insertMany([{'name': 'Apporv','age': 22, 'email': 'apoorvtiwary@gmail.com'},
{'name': 'Deepak','age': 20, 'email': 'dasjideepak@gmail.com'},
{'name': 'Anupam','age': 28, 'email': 'anupam.bengal@gmail.com'}]);

db.TT.insertMany([{'name': 'Mayank','age': 24, 'email': 'max007@gmail.com'},
{'name': 'Sunny','age': 23, 'email': 'itzsunny@gmail.com'},
{'name': 'Akshat','age': 26, 'email': 'akshatspeaks@gmail.com'}]);

```

5. list all collections in sports database

```js
show collections
```

6. rename `TT` collection to `tennis`.

```js
db.TT.renameCollection("Tennis")
```

7. create a capped collection called `khokho` which should have max 3 documents.
  Try inserting more than 3 and output the result here ?

```js

db.createCollection("khokho", {capped: true, size: 128*1024, max: 3});
db.khokho.insertMany([{'name': 'Naveen','age': 24, 'email': 'naveemchinnodu@gmail.com'},
{'name': 'Ram','age': 23, 'email': 'ramashankar@gmail.com'},
{'name': 'Ved','age': 26, 'email': 'vedbro@gmail.com'},
{'name': 'Akshay','age': 26, 'email': 'puplleboi@gmail.com'}]);
```

```text
  {
        "acknowledged" : true,
        "insertedIds" : [
                ObjectId("5ea69a0dce2dd35cb421d880"),
                ObjectId("5ea69a0dce2dd35cb421d881"),
                ObjectId("5ea69a0dce2dd35cb421d882"),
                ObjectId("5ea69a0dce2dd35cb421d883")
        ]
}
```

8. check whether a collection is capped or not?
```js
db.khokho.isCapped()
true
db.cricket.isCapped()
false
```

9. remove all documents from `football` collection.

```js
 db.football.remove({})

```

10. delete cricket collection completely.

```js
db.cricket.drop()
```

11. rename database sports to games

```js
db.copyDatabase("sports","games","localhost")
use games
db.dropDatabase();
```

12. delete sports database. 
```js
db.dropDatabase()
```
