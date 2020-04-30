1. Create a database named `blog`.


```js
use blog; 
```

2. Create a collection called 'articles'.

```js
db.createCollection('articles')
```

3. Insert multiple documents(at least 3) into articles. It should have fields

```js
db.articles.insertMany([
{"title": "Views in Express", "text": "Express builds up the context object every time you call render", "author": "Anshu Saurabh"},

{"title": "Persisting your data with MongoDB", "text": "You could store your application’s data in memory, by setting variables", "author": "Anshu Saurabh"},

{"title": "Testing Express applications", "text": "Writing reliable code can be difficult. Even small software can be too complex for one person.", "author": "Anshu Saurabh"}])

```

4. Find all the articles using `db.COLLECTION_NAME.find()`

```js
db.articles.find().pretty()
```

5. Find a document using _id field.


```js
db.articles.find({ _id: ObjectId("5ea737722b228c3453c72972")});
```

6. Find documents using title and author's name field.

```js
db.articles.find({ author: "Anshu Saurabh", title:"Persisting your data with MongoDB"});
```

7. Find document using a specific tag.

```js
db.articles.find({ tags: {$in: ["mongodb", "SQL"] } });
```

8. Update title of a document using its _id field.

```js

db.articles.updateOne({ _id: ObjectId("5ea737722b228c3453c72972")}, {$set: {"title": "Testing with Express Framework"}})
```

9. Update a author's name using article's title.

```js
db.articles.updateOne({ "title": "Persisting your data with MongoDB"}, {$set: {"author": "Rishabh Anand"}})
```

10. rename details field to description from articles collection. 

```js
db.articles.updateMany( {}, { $rename: { "text": "description" } } )
```

11. Add additional tag in a specific document.

```js
db.articles.update({"title":"Testing Express applications"}, {$push: {tags: "tutorial"}});
```

12. Update an article's tags using $set and without $set.
  - Write the differences here ?
  
```js
//Set will update whole content of tags array whereas push will just add one element to array field of document
db.articles.update({"title":"Testing Express applications"}, {$set: {tags: ["database", "tutorial"}});
db.articles.update({"title":"Testing Express applications"}, {$push: {tags: ["database",}});
```

13. Increment an auhtor's age by 5.  

```js
db.articles.update({"title":"Testing Express applications"}, {$inc: {"author.age": 5}})
```
14. Delete a document using _id field with `db.COLLECTION_NAME.remove()`.

```js
db.articles.remove({ _id: ObjectId("5ea737722b228c3453c72972")})
```

Use sample.js data for below queries.

1. Find all males who play cricket.

```js
db.users.find({"gender": "Male"}, {"sports": { $in: ["cricket"] }}).pretty()
```

2. Update user with extra golf field in sports array whose name is "Steve Ortega".

```js
db.users.find({"name": "Steve Ortega"}, {"sports": { $push: "golf" }})  
```
3. Find all users who play either 'football' or 'cricket'.

```js
db.users.find({"sports": {$or : [ "football", "cricket"]}});
```

4. Find all users whose name includes 'ri' in their name.

```js
db.inventory.find( { name: { $regex: "/ri/g" } } )
```
