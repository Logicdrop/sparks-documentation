# NodeJS API Client

A Javascript package which uses the `request` package to perform the Sparks API calls

## Installation

Install the Sparks API package via:

```text
npm install @logicdrop/sparks-openapi-nodejs
```

## Getting Started

To use the API Client, follow this example code:

```javascript
var SparksOpenApi = require('@logicdrop/sparks-openapi-nodejs');

var oauth2 = new SparksOpenApi.OAuth();
oauth2.username = "YOUR SPARKS USERNAME";
oauth2.password = "YOUR SPARKS PASSWORD";

var api = new SparksOpenApi.ProjectServicesApi(oauth2, 'https://api.logicdrop.io');
var client = "client_name"; // {String} Client name

api.listProjects(client).then(function(data) {
  console.log('API called successfully. Returned data: ', data);
}, function(error) {
  console.error(error);
});
```

