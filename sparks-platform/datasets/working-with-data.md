# Working with Datasets

To navigate to the Datasets workspace, click on the **Datasets** tile from an open project, or **Data** in the navigation sidebar.

From the Datasets workspace you can view and navigate to existing datasets, or create a new one by clicking on the **New Dataset** button in the upper-right-hand corner.

![](https://lh3.googleusercontent.com/30YYUjmYKmAly-x757izlM5KPC84EL7lwsbuVCHitvB1BRkU2IEzpw-IOfGZ7wNN9xFcVyjmzt9Ox-KbjxkqRcaO71ojbvFbJdM-8b5X6WfGvWXMMeJ1de_GUiFTpl9za-6gMBew)

When creating a dataset, you are presented with the option of a single document or a collection. This choice is dictated by the nature of the data you with to store \(one record or a large, unbounded collection, possibly to an external source.\) More on these in the [next section](types-of-datasets.md).

Similar to Projects, Datasets allow organization with tags, and editing using the same artifact action menu.

When a dataset is created, a path URL is established for access via the API. 

{% hint style="warning" %}
Exercise caution when changing the path of a dataset and ensure that reference to that dataset from the API are updated as required.
{% endhint %}

When removing a dataset of a single document or Sparks collection type is removed, that data will be cleaned up and deleted. For datasets referencing external sources, the external data will remain unchanged and will simply disconnect from Sparks.

