---
description: This sections outlines how to deploy or update a workbook once created.
---

# Deploying a Workbook

Deploying a workbook with the Logicdrop Sparks Platform is just making a simple API request. The user will do a POST request to the following endpoint:
```text
/compute/{client}/{project}/{artifact}/generate
```
In the body of the request, attach the workbook xlsx with the key name "file" as form-data.





