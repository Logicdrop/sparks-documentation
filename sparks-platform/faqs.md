# FAQs

## Will my existing Drools rules work in the Sparks Platform?

They should. We have used numerous examples using the latest Drools GitHub repository and other online sources as the basis for our own examples. For the most part we have been able to practically copy-and-paste rules and types into Sparks and they have worked.

## How large can a “document” and its content be?

We use MongoDB as our primary NoSQL store so the max size of a document is 16MB.

## How can the rule processor be invoked - per request, batch, etc.?

All requests can be made to the processor using a REST call or our API clients. We have clients who execute a combination of per-request, usually when interacting with some UX application, and batch when there are numerous calls that need to be made and the response time does not have to be immediate.

## What can I access from inside my rules?

Anything you normally would. Aside from incorporating any third-party libraries and being able to pass in almost any form of data into the request, we also have our own ComputeApi which is injected into each ruleset so that you can call out to other Sparks services.

## How large can a ruleset be \(number of rules\)?

We have clients, using decision tables, that generate upwards of 5-10k+ rules. We have also had implementations where the rules were all freeform but handled incredibly complex algorithm consequences or pattern matching constraints and produced very dynamic results.

## What are the performance characteristics of executing rules?

We see regular response time averages in single digit milliseconds for many rulesets. For complicated rulsets containing many thousands of rules and lots of re-firing, this can rise to 10-100ms or more. Basically, it depends on the nature of the rules executing. Feel free to reach out to our team for specific advice on your own situation.

## How many requests can the Sparks API handle?

Currently, we have a cap each API client at 100 requests per second which can be increased by request for our professional and enterprise customers. The Sparks API runs on a redundant kubernetes clusters on AWS, which can, theoretically, scale to meet any demand so long as additional EC2 hardware is available on AWS.

## Do I have to use the Sparks Data Services?

No, if you are integrating our API with another application you can send your own data over \(depending on the service\). In that case, Sparks will most act as a type of controller and only use its internal NoSQL database for its own purposes only.

## What security is available through the API and/or in use by your platform?

We use Auth0 as our provider and can accommodate OAuth2, JWT, or API key based authentication. Authorization is maintained internally and each endpoint requires it. In addition to authentication, each call is further authorized against a client and a project typically at the very least.

## What SLAs are available for Sparks?

Like any business-centric SaaS platform, we take up-time very seriously. Generally, the services are available at 99.95% or above. The specific SLAs for Sparks vary based on subscription level, and our customer support team can provide the specifics of the various SLAs we offer: [support@logicdrop.com](mailto:support@logicdrop.com)  


