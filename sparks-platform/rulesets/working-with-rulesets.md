# Working with Rulesets

To navigate to the Ruleset workspace, click on the Rulesets tile from the project workspace or the Rules item in the sidebar to see a list of available rulesets.

![](https://lh4.googleusercontent.com/JEKREytM9mMODYeXBR8c2Bmol0l01yDLPDpPOiA8X6nGZq1yX6Dl6pOHWXuk3t1-Mq3THFrHmTm83YyhMz-D2ixVNBOFEtcaa92-kprZU1SrGQQcBKah8TdzUvv_prAs-4ai6NiV)

From the Rulesets workspace you can either navigate into a ruleset, create a new ruleset by clicking the New Ruleset button in the upper-right-hand corner, or test rules against running containers.

Navigate into a ruleset and you will be presented with a ruleset screen:

![](https://lh6.googleusercontent.com/_7j06vwWV0VWXE7havm7NlPG-uHOiZSGAooMHbmY0h7jWKkNW7WYF1EMV3VP-uOCHyvxvvBncvzwc63M5w7A0CQygDEQXVtNaeOlSDUNGu3hVqLRwWW0At8eIaSlpl93PZSDStnS)

The ruleset screen is the central point where users will design, test, and manage a ruleset.

From the ruleset screen you can:

* Test rules against running containers
* Edit any freeform or guided rules
* Import decision tables
* Publish the latest container of the ruleset
* Manage all containers associated with the ruleset

## Containers

A container is a running instance of a ruleset. Each container that can be exposed as an independent API for execution and interacted with.

Exposed containers may represent the latest ruleset, a project versioned ruleset, or a specific version of the ruleset. 

You can have multiple containers, even of the same ruleset \(just with different identifiers\), running at the same time. This becomes handy when you need to test or modify a rulest and have a production version of that ruleset that you do not want to interfere with.

## Imports

These are outside packages you want to pull into your rules. These could be in-house developed APIs or libraries or third-party sources \(such as Maven dependencies\). This feature is only available with Enterprise subscriptions.  


## Globals

Globals are values that can be used in and interacted with your rules. They should be kept stateless for safety. Some examples of globals always injected into the rules are logging, our own ComputeApi which internally exposes select functionality of the Sparks API to the rules \(data access, caching, messaging, email, etc.\).

Examples of other globals you might set \(key/value\):

* Boolean / RunOnly where RunOnly is a true/false flag you set in the rules. In turn, your rules may perform certain actions if the flag is true.
* List / MyMessages where MyMessages is a collection you can insert your own messages and retrieve them later in the results.

## Types

Types are user defined “facts” that represent data in a real-world fashion. They can be used to model a business domain or act as containers for transforming data from one form to another.

If Key is enabled, for one or more fields, that internally creates a “unique” identifier that identifies the fact. Depending on the type of ruleset \(equality or identity\), duplicate facts with the same key may be ignored as an optimization because one with the same value already exists.

![](https://lh4.googleusercontent.com/J_lO-J6qRENUoHco2ywJ5wgvYFJIcthUCaqRLaVWN21kycB_lXc4QoFrCF8wzWi0Zxt_tC7uxMbEf9U7InU-_MzjLmZLs_UVL9FbGViiUTjIl2I5MIpaeNXOZ-caJS3X35sW_LBv)  


When working with numbers or boolean types, because they can be constrained in the rules as null/not null or checked for a value, if you do not set a default you will have to test for nullability first because it may not of even been populated.

## **Rule Content**

Rule Content allows for custom rules, functions, and declarations. It may be used to import any Drools DRL file directly, and an many ways can shortcut manually defining the rules in Sparks. 

![](https://lh6.googleusercontent.com/tRK3hchAxEr0eG9bmt80HORayKHNQoI5kip_SxHY5zhcvDWO-PEhO91-JPJK6LgQA6CwEOLrF6zvDRzeCxWepz2MTKj7-YtiyBb1IrQbz8IIqbR7cv4mk46VHT8dSFxEW_s0UYwn)

Rule content can be a nice way to manage rules as a standard DRL file and then selectively expose only the rules you want users to work with using the editor. 

This allows a domain expert to build out complex rules, types, queries, functions, etc. in the rule content and then as needed only expose certain rules for users to be able to interact with.

## **Properties**

Properties are user-defined key-value pairs that allow you to annotate a ruleset with any data or labels you want to help define the ruleset. This helps when automating ruleset creation and management from the API.

Some examples of user properties could be:

| Key | Value |
| :--- | :--- |
| environment  | staging |
| usages | \["lending", "approval"\] |

