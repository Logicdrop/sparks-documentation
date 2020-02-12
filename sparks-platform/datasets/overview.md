# Overview

Datasets represent the data services workspace of the Sparks Platform. They expose a standardized way to manipulate, query, and manage internal and external data sources from one place.

With datasets, users can create and manage their own data structures and collections, similar to a database but far richer. A Sparks dataset may be _internal_, backed by a NoSQL document or collection, or _external ****_by connecting to your own hosted SQL databases, AWS S3 files, and more.

Each dataset, no matter the source, is exposed in the Sparks API with a unified model for querying and updating the data, effectively providing "data-as-a-service".

{% hint style="info" %}
The Sparks Platform primarily relies on MongoDB as its default NoSQL store. It is used for its own internals and client managed data as the default provider.
{% endhint %}

### Use Cases

Datasets can be used in a wide variety of ways. Some of the more common uses are:

* Quickly scaffold applications with full create/request/update/delete \(CRUD\) data functionality \(hence, not having to write a back-end yourself\)
* As a source of data for external applications and systems to interact with
* As a source of data to trigger rules when changes occur
* Collect “learned” facts from rules that can be exposed to other applications

