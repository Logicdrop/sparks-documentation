---
description: This sections outlines how to deploy or update a workbook once created.
---

# Deploying a Workbook

### Deploying from the API

Deploying a workbook with the Logicdrop Sparks Platform is just making a simple API request. The user will do a POST request to the following endpoint:

{% api-method method="post" host="" path="/compute/{client}/{project}/{artifact}/generate" %}
{% api-method-summary %}

{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="client" type="string" required=true %}
Your client name
{% endapi-method-parameter %}

{% api-method-parameter name="project" type="string" required=true %}
The project name
{% endapi-method-parameter %}

{% api-method-parameter name="artifact" type="string" required=true %}
The name of the rule set in the project
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-form-data-parameters %}
{% api-method-parameter name="file" type="object" required=true %}
Workbook \*.xlsx file
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

In the body of the request, attach the workbook xlsx with the key name "file" as form-data.

The full API documentation is available here: [Uploading a workbook](https://docs.logicdrop.io/#operation/uploadWorkbook)

