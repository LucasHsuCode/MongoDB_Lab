# Operator

## Create
If you don't have a collection yet, you can simply type:
```
$ db.authors.insertOne({name: "Brandon Sanderson", age: 60})
```
This will create the authors collection and insert one document into it.

To insert multiple documents, you can use the insertMany() method, like this:


```
db.books.insertMany([
    {
        title: "The Light Fantastic",
        author: "Terry Pratchett",
        pages: 250,
        rating: 6,
        genres: ["fantasy"]
    },
    {
        title: "Dune",
        author: "Frank Herbert",
        pages: 500,
        rating: 10,
        genres: ["sci-fi", "dystopian"]
    }
])
```
## Read
Reading data is a common operation in MongoDB. Here are some common examples of reading data:

Query all documents
If you want to query all documents in a collection, you can use the find() method as follows:
```
db.books.find()
```
This will return all documents in the books collection.
***

Query documents that match a condition
If you only want to query documents that match specific conditions, you can specify a query object as the first parameter of the find() method. For example, the following example will query all books whose author is "Terry Pratchett" and rating is 6:
```
db.books.find({author: "Terry Pratchett", rating: 6})
```
***
Select fields to return
If you only need certain fields from the documents, you can specify an options object as the second parameter of the find() method to indicate which fields to return. For example, the following example will only return the title and author fields:
```
db.books.find({}, {title: 1, author: 1})
```

In this example, 1 indicates that the field should be returned, while 0 indicates that the field should not be returned.

***
Query documents that match a condition and return selected fields
If you want to query documents that match specific conditions and only return certain fields, you can combine the previous two methods as follows:
```
db.books.find({author: "Terry Pratchett", rating: 6}, {title: 1, author: 1})
```
This will return all books whose author is "Terry Pratchett" and rating is 6, but only include their title and author fields.

These examples demonstrate the basic operations for reading data in MongoDB. You can choose which methods and options to use based on your needs and scenarios.
***
Query a Specific Document by ID
In MongoDB, each document in a collection has a unique _id field that identifies it. To query a specific document by its ID, you can use the findOne() method with an object that specifies the _id value.

For example, the following command retrieves the document with the **_id** value of **6415cd199bb1b657f7ddcfa2** from the books collection:
```
db.books.findOne({_id: ObjectId("6415cd199bb1b657f7ddcfa2")})
```
This command will return a single document that matches the specified _id value. Note that the _id value must be passed as an instance of the ObjectId class, which is provided by the MongoDB driver.
***
Querying for documents with a specific field value
To query for documents that have a specific field value, you can use a query object with the field name and the desired value. For example, the following command retrieves all documents in the **books** collection that have a **rating** value greater than 7:
```
db.books.find({rating: {$gt: 7}})
```
This command will return all documents in the books collection that have a rating value greater than 7.
***
Querying for documents with a range of values
To query for documents that have a field value within a range of values, you can use the **\$lt**, **\$lte**, **\$gt**, and **\$gte** operators in your query object. For example, the following command retrieves all documents in the books collection that have a rating value less than 8:
```
db.books.find({rating: {$lt: 8}})
```
This command will return all documents in the books collection that have a rating value less than 8.
***
Querying for documents with logical operators
You can use logical operators such as **\$or** and **\$and** to combine multiple criteria in your query object. For example, the following command retrieves all documents in the **books** collection that have a **rating** value of either 7 or 9:
```
db.books.find({$or: [{rating: 7}, {rating: 9}]})
```
This command will return all documents in the books collection that have a rating value of either 7 or 9.
***
Querying for documents with multiple criteria
You can combine multiple criteria in your query object to retrieve documents that meet all of the specified criteria. For example, the following command retrieves all documents in the books collection that have either a pages value less than 300 or a pages value greater than 400:
```
db.books.find({$or: [{pages: {$lt: 300}}, {pages:{$gt:400}}]})
```

This command will return all documents in the books collection that have either a pages value less than 300 or a pages value greater than 400.


***
Querying for documents with a field value in an array
To query for documents that have a field value that matches any value in an array, you can use the $in operator in your query object. For example, the following command retrieves all documents in the books collection that have a rating value of 7, 8, or 9:
```
db.books.find({rating: {$in: [7,8,9]}})
```

This command will return all documents in the books collection that have a rating value of 7, 8, or 9.

Querying for documents with a field value not in an array
To query for documents that have a field value that does not match any value in an array, you can use the $nin operator in your query object. For example, the following command retrieves all documents in the books collection that have a rating value that is not 7, 8, or 9:
```
db.books.find({rating: {$nin: [7,8,9]}})
```
This command will return all documents in the books collection that have a rating value that is not 7, 8, or 9.
***


These are just a few examples of how you can use the find() method to query data in MongoDB. There are many other operators and options that you can use to refine your queries, depending on your needs and scenarios.


#Update
```
db.books.updateOne({_id: ObjectId("6415cd199bb1b657f7ddcfa2")}, {$set: {rating: 8, pages:400}})
```
 This query will update a single document in the books collection with the specified _id value. The $set operator is used to set new values for the rating and pages fields. In this case, the rating field will be set to 8 and the pages field will be set to 400.

```
db.books.updateMany({author: "Terry Pratchett"}, {$set: {author: "Terry Pratchet"}})
```
 This query will update all documents in the books collection that have the specified author value of "Terry Pratchett". The $set operator is used to set the new value of author to "Terry Pratchet". In this case, the extra "t" at the end of "Pratchett" will be removed from all matching documents.

```
db.books.updateOne({_id: ObjectId("6415cd199bb1b657f7ddcfa2")}, {$inc: {pages: 2}})
```
 This query will update a single document in the books collection with the specified _id value. The $inc operator is used to increment the value of the pages field by 2.

```
db.books.updateOne({_id: ObjectId("6415cd199bb1b657f7ddcfa2")}, {$inc: {pages: -2}})
```
 This query will update a single document in the books collection with the specified _id value. The $inc operator is used to decrement the value of the pages field by 2.

```
db.books.updateOne({_id: ObjectId("6415cd199bb1b657f7ddcfa2")}, {$pull: {genres: "sci-fi"}})
```
 This query will update a single document in the books collection with the specified _id value. The $pull operator is used to remove the "sci-fi" value from the genres array field.

```
db.books.updateOne({_id: ObjectId("6415cd199bb1b657f7ddcfa2")}, {$push: {genres: "sci-fi"}})
```
 This query will update a single document in the books collection with the specified _id value. The $push operator is used to add the "sci-fi" value to the genres array field.

```
db.books.updateOne({_id: ObjectId("6415cd199bb1b657f7ddcfa2")}, {$push: {genres: {$each: ["1", "2"]}}})
```
 This query will update a single document in the books collection with the specified _id value. The $push operator is used to add the values "1" and "2" to the genres array field.

Note that these update queries can be very powerful, but they can also be dangerous if not used correctly. Be sure to use caution when updating documents in your database to avoid unintended consequences.


# Delete
```
db.books.deleteOne({_id: ObjectId("6415cd199bb1b657f7ddcfa2")})
```
This query will delete a single document from the **books** collection that has the specified **_id** value. For example, if there is a document with **_id** equal to **"6415cd199bb1b657f7ddcfa2"**, this query will delete that document.
```
db.books.deleteMany({author: "Terry Pratchett"})
```
This query will delete all documents from the **books** collection that have the specified **author** value of "Terry Pratchett". For example, if there are multiple documents in the books collection with the author field equal to **"Terry Pratchett"**, this query will delete all of those documents.

Note that both of these queries are irreversible, meaning that once a document is deleted, it cannot be recovered. So, it's important to use caution when running these commands and make sure that you are targeting the correct documents.