# Types of Datasets

Datasets can be classified as either document-based \(a single record\) or collection-based \(many records\).

### Document-based

Document-based datasets usually are best applied when the data can be self-contained within a single document, and the size is not likely to grow large or unbounded.

The “data,” or content, contained within the document can have a rich deep structure that combines properties \(fields\) and nested collections of elements into one document.

Using the document style we can combine data into a single dataset that would typically be located across multiple tables in a traditional relational database.

{% hint style="info" %}
**Example Document-Based Dataset**

This is an example of a single-document dataset, represented in JSON form. It contains a nested record, `address`, which typically would link to another table using a Foreign Key in a traditional relational database.

```text
"content": {
    "companyName": "Best Insurance",
    "address": {
        "street1": "12345 Example Avenue",
        "state": "MI",
        "city": "Detroit",
        "zip": "67890"
    }
}
```
{% endhint %}

One benefit of the document-based approach is that all the required data can be accessed with a single lookup. Data stored under “content” can be as rich or simple as you like and it is easy to simplify complex database relationships and combine data into a single well-defined document.

Another advantage to this “schema-less” approach is that not all elements have to have the same structure. You can have two datasets or a dataset with a list of elements that have completely different content and structure.

{% hint style="warning" %}
Just because there is no enforced schema in the document-based datasets does not mean you should let every element have a completely different structure if you can avoid it. If anything, consistency alone goes a long way in working with data. This flexibility is primarily convenient when data evolves over time.
{% endhint %}

### Collection-based

The other type of dataset the Sparks Platform supports are collection-based datasets. The source of a collection-based dataset may be an internal Sparks NoSQL collection, or proxied from an external source such as a SQL database, AWS S3 files, a distributed cache, etc. 

This format is useful when connecting to existing databases, or when the size of a dataset is likely to exceed the practical size and/or usefulness of using a document-based dataset. A good analogy of the collection-based dataset would be a database table. If there are 1000+’s of rows, each with different IDs, then it is likely to fit better into the collection-based paradigm.

The collection-based view of a dataset displays tabular rows of data which can be independently  created, edited, and deleted. 

![](https://lh6.googleusercontent.com/kMbhCsJTFXCABe9K3sFC2WDBXxmDYKkOWRDW2H_RmUSBgOFQoSeb73p-9fRDvlgRizRkBLEHLnBuGV_bdWXst72qBAva28hU3qDXxOu6ItBMlBCXEPoOHux8ZFH4Ub0QqqgD4e5i)

Collection-based datasets also support advance querying, sorting, and filtering of the rows within.

**Richly Structured Rows**

One unique difference in our collection-based dataset is when you choose to use our NoSQL datastore to house the data. In this scenario, each row and the fields within a row, can be a “deeply” structured document similar to how document-based collections work. This opens up a whole world of possibilities when working with data.

At a first glance, the record view looks the same as above until you navigate into a row with nested data for editing:

![](https://lh6.googleusercontent.com/lzOCYAJXjluiKhI9P1CGNX4GP4vYS9dTmqRxHbRHZ0OmLr5yBI_aDV5WUijVnrrmmPOETOjjcni7VqUKUvQaGslg5QFadlR0Pd25TTe8kOHYegR4wHiUD-chiLNyE5In6HD1BE89)

Selecting a row and editing it, you can see it has a rich data structure for its fields rather than just a field and value per row, and each nested field, such as `address`, can be edited independently with an expandable editor.

Using our NoSQL store we can have fields that are deeply structured data themselves like the below example.

```text
{
    "id": "5e3e16ddc8e45d13554ef5ab",
    "name": "John Doe",
    "phone": "123-456-7890",
    "address": {
        "street": "Somewhere",
        "zipcode": 12345
    },
    "traits": [
        "user",
        "beta"
    ]
}
```

Had we used a conventional database approach this row alone might have been structured with three tables that need to be related to each other through a combination of keys and a query.

{% hint style="info" %}
Though there is no hard rule when to use which there are some best practices we have adhered to, which work well. We generally use document-based datasets as much as possible and when the data can easily be self-contained. We use collection-based datasets when accessing external sources or if we are working with data that needs to adhere to ACID \(atomicity, consistency, isolation, durability\) principles.
{% endhint %}

{% hint style="info" %}
For a deeper explanation of this approach here is an article [6 Rules of Thumb for MongoDB Schema Design](https://www.mongodb.com/blog/post/6-rules-of-thumb-for-mongodb-schema-design-part-1) from the MongoDB blog.
{% endhint %}

