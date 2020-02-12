# Projects

Everything in the Sparks Platform revolves around the concept of a project. A project allows convenient grouping of many associated artifacts, such as **Datasets**, **Rulesets**, and **Assets**. A project and its artifacts usually define a specific domain or purpose.

Some project examples could be an insurance project that calculates a risk score and manages policy and risk data or a lending project that has rules relating to commercial properties and data about those properties and lenders.

Projects can be shared, imported/exported, and versioned. Anything created within a project will inherit its common properties as a starting point \(i.e. version\).

Whether you are using the portal or the API, a good way to think of a project is as the “entry-point” into its related artifacts.

{% hint style="info" %}
From the API, most requests require at least the client, and additionally the project, in the path such as  `/[service]/{client}/{project}/{operation}`
{% endhint %}

