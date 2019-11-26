# Introduction to Sparks Compute

The Sparks Compute service provides a powerful environment to author and execute processes which perform decision making, data augmentation, validation and more on a proven and scalable platform. All provisioning, container management, deployment and scalability is handled by the platform, allowing an API to be defined and provisioned as simply as uploading an excel workbook.

## Introduction to Business Rules and Related Terminology

The Sparks Compute Engine uses standardized terminology which helps to clarify concepts and procedures.

1. **Rule** - A rule is a single atomic logic statement comprised of a "when" clause \(the condition\) and a "then" clause \(the consequences when the condition is met\).
2. **Business Rule** - Synonymous to rule, a business rule is a rule relating to some business process or procedure.
3. **Rule set** - A collection of one or more rules relating to a single purpose.
4. **Rules Engine** - An engine which is capable of executing one or more rule sets to produce an outcome.
5. **Fact** - A piece of input our output data provided to or produced by the rules engine at execution time.
6. **Rule Container** - A deployed process in Sparks which is configured to execute a rule set.

### Performing Actions

All actions performed by the Sparks Compute Engine are achieved through the definition and execution of rule sets. Rules are not executed in sequence, but rather compiled into a decision tree by the engine and executed simultaneously.

{% hint style="info" %}
Note that it is possible for one rule's output to affect the input condition of another. In this case, the affected branches of the decision tree are re-executed until the state is no longer mutated or the execution limit is exhausted.
{% endhint %}

Rules may be defined ad-hoc though the API or Portal user interface, or most commonly, uploaded as decision tables created in Microsoft Excel. In the case of decision tables, each row then becomes a rule when imported with each sheet in the workbook pertaining to a rule set.

### Facts

Facts in the Sparks Compute Engine provide a template for any data passed into or out of the compute engine. Facts may be created and managed using the Sparks API or in the Portal user interface.

{% hint style="info" %}
Generally it best to keep facts as flat and lean as possible to maximize the performance of the engine. For this reason, your facts defined in Sparks may often be a subset or flattened view of a more complicated data structure.
{% endhint %}

### Containers

To execute rule sets on the Sparks platform, they must first be deployed to a container. Deploying a container is as easy as calling start or rebuild from the Sparks API or using the Portal user interface. Each container is specific to a version of the rule set as the point it was built and is given a unique API URL for execution. Stopping a container cleans up the resources and shuts down the container endpoint.

{% hint style="info" %}
Multiple versions of a rule set may be published on separate container versions, making it possible to test new changes before moving dependent process to point to the new container version.
{% endhint %}

