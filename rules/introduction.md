# Introduction to Sparks Compute Engine

The Sparks Compute Engine provides a powerful environment to author and execute process which perform decision making, data augmentation, validation and more on a proven and scalable platform. All provisioning, container management, deployment and scalability is handled by the platform, allowing an API to be defined and provisioned as simply as uploading an excel workbook.

### Introduction to Business Rules and Related Terminology

The Sparks Compute Engine uses standardized terminology which help to clarify concepts and procedures. 

1. **Rule** - A rule is a single atomic logic statement comprised of a "when" clause \(the condition\) and a "then" clause \(the consequences when the condition is met\).
2. **Business Rule** - Synonymous to rule, a business rule is a rule relating to some business process or procedure.
3. **Rule set** - A collection of one or more rules relating to a single purpose.
4. **Rules Engine** - An engine which is capable of executing one or more rule sets to produce an outcome.
5. **Fact** - A piece of input our output data provided to or produced by the rules engine at execution time.

All actions performed by the Sparks Compute Engine are achieved through the definition and execution of rule sets. Rules may be defined ad-hoc though the API or Portal user interface, or most commonly, uploaded as decision table created in Microsoft Excel. In the case of decision tables, each row then becomes a rule when imported with each sheet in the workbook pertaining to a rule set. 

#### Facts

Facts in the Sparks Compute Engine provide a template for any data passed into or out of the compute engine. Facts may be created and managed using the Sparks API or in the Portal user interface. 

{% hint style="info" %}
Generally it best to keep facts as flat and lean as possible to maximize the performance of the engine. For this reason, your facts defined in Sparks may often be a subset or flattened view of a more complicated data structure.
{% endhint %}

