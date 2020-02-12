# Datasets

## Overview

Datasets represent the data services work space of the Sparks Platform. They expose a standardized way to manipulate, query, and manage internal and external data sources from one place.

With datasets, users can create and manage their own data structures and collections, similar to a database but far richer.

 A dataset may attach to external sources, and perform all the common functions you would expect from any data service - create, request, update, and delete \(CRUD\).

Each dataset, no matter the source, is exposed in the Sparks API with a unified model for querying and updating the data.

A dataset may attach to external sources, and perform all the common functions you would expect from any data service - create, request, update, and delete \(CRUD\).

Datasets can either be internal \(NoSQL and/or our distributed cache service\) or external.

Some examples of external sources Sparks can connect to are SQL databases, AWS S3 files, and more.

### Use Cases

Datasets can be used in a wide variety of ways. Some of the more common uses are:

●      Quickly scaffold applications with full create/request/update/delete \(CRUD\) data functionality \(hence, not having to write it yourself\)  
  


●      As a source of data for external applications and systems to interact with  
  


●      As a source of data to trigger rules when changes occur  
  


●      Collect “learned” facts from rules that can be exposed to other applications

### Working with Data

The Sparks Platform primarily relies on MongoDB as its default NoSQL store. It is used for its own internals and client managed data as the default provider.

To navigate to the Datasets workspace, click on the **Datasets** tile from the project workspace or the **Data** item in the sidebar to see a list of available datasets.

![](file:///C:/Users/jared/AppData/Local/Packages/oice_16_974fa576_32c1d314_2e59/AC/Temp/msohtmlclip1/01/clip_image002.gif)

From the Datasets workspace you can either navigate into an existing dataset or create a new one by clicking on the **New Dataset** button in the upper-right-hand corner.

### Types of Datasets

Datasets can be classified as either document or collection-based.

#### Document-based

Document-based datasets usually are best applied when the data can be self-contained within the document itself.

The “data” or content contained within the document can have a rich deep structure that combines properties \(fields\) and collections of elements into one document.

Here is an example of a dataset that combines company details with address information into a single document. In a RDBMS, this would typically be structured as a one-to-many relationship where a company relates to addresses by a PK/FK relationship.  


Using the document style we can combine that data into a single dataset and the only key we need to use to access all of this detail is the ID of the dataset \(not shown in this snippet\).

"content": {

    "companyName": "Best Insurance",

    "address": {

        "street1": "12345 Example Avenue",

        "state": "MI",

        "city": "Detroit",

        "zip": "67890"

    }

}

This is an example of a list of elements, pulled from an external source, combined into a single document \(and why the driverId field is present\). This dataset contains a “collection” of items. In a RDBMS, this would be structured as a table with multiple records \(typically relating back to something by their PK\).

"content": \[

    {

        "dayVehiclePlace": "STREET",

        "nightVehiclePlace": "STREET",

        "driverId": 400

    },

    {

        "dayVehiclePlace": "NIGHT",

        "nightVehiclePlace": "NIGHT",

        "driverId": 100

    },

\]

One benefit of the document-based approach is that all the required data can be accessed with a single lookup. Data stored under “content” can be as rich or simple as you like and it is easy to simplify complex database relationships and combine data into a single well-defined document.

Another advantage to this “schemaless” approach is that not all elements have to have the same structure. You can have two datasets or a dataset with a list of elements that have completely different content and structure.

**Just because there is no schema in the document-based datasets does not mean you should let every element have a completely different structure if you can avoid it. If anything, the consistency alone goes a long way in working with the data. Where this is convenient is when data evolves over time.**

#### Collection-based

The other type of dataset the Sparks Platform supports is collection-based datasets. Usually, this is data being pulled in \(proxied\) from another source like an SQL database, AWS S3 files, a distributed cache, etc. or when the number of records exceed the practical size and/or usefulness of using a document-based dataset. A good analogy of the collection-based dataset would be a database table. There are 1000+’s of rows, each with different IDs so that they can be queried and related to some “owning” source.

The collection-based view of a dataset is more similar to a conventional web app that displays rows of data.

![](file:///C:/Users/jared/AppData/Local/Packages/oice_16_974fa576_32c1d314_2e59/AC/Temp/msohtmlclip1/01/clip_image004.gif)

**Richly Structured Rows**

One unique difference in our collection-based dataset is when you choose to use our NoSQL datastore to house the multiple records.

In this scenario, each row and the fields within a row, can be a “deeply” structured document similar to how document-based collections work.

This opens up a whole new world of possibilities when working with data...

At a first glance, the record view looks the same as above until you navigate into one of the rows for editing...

![](file:///C:/Users/jared/AppData/Local/Packages/oice_16_974fa576_32c1d314_2e59/AC/Temp/msohtmlclip1/01/clip_image006.gif)

Selecting the “John Doe” row and editing it, you can see it has a rich data structure for its fields rather than just a field and value per row.

Using our NoSQL store we can have fields that are deeply structured data themselves like the below example.

"id": "5e3e16ddc8e45d13554ef5ab",

"name": "John Doe",

"phone": "123-456-7890",

"address": {

    "street": "Somewhere",

    "zipcode": 12345

},

"traits": \[

    "user",

    "beta"

\]

Had we used a conventional database approach this row alone might have been structured with three tables that need to be related to each other through a combination of keys and a query.

**Though there is no hard rule when to use which there are some best practices we have adhered to, which work well. We generally use document-based datasets as much as possible and when the data can easily be self-contained. We use collection-based datasets when accessing external sources or if we are working with data that needs to adhere to ACID \(atomicity, consistency, isolation, durability\) principles.**

**For a deeper explanation of this approach here is an article 6 Rules of Thumb for MongoDB Schema Design from the MongoDB blog.**

##  

