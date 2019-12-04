# [Node.js](https://nodejs.org/) API Client
A Javascript package which uses the `request` package to perform the Sparks API calls

## Installation

#### Access NPM Package
To access the NPM package, you will need to add a `.npmrc` file to the root of your
project. The file should contain the following content,

```
registry={repo-location}
_auth={auth-secret}
```

You can retrieve your `auth-secret` and `repo-location` from the project admin.

#### Install NPM Package

Install the Sparks API package via:

```text
npm install @logicdrop/sparks-openapi-nodejs
```

## Getting Started

To use the API Client, follow this example code:

```javascript
var SparksOpenApi = require('@logicdrop/sparks-openapi-nodejs');

var defaultClient = SparksOpenApi.ApiClient.instance;
// Configure OAuth2 access token for authorization: oauth2
var oauth2 = defaultClient.authentications['oauth2'];
oauth2.tokenUrl = "https://api.staging.com/oauth2/token";
oauth2.clientId = "YOUR APPLICATION ID";
oauth2.clientSecret = "YOUR APPLICATION SECRET";

var api = new SparksOpenApi.CacheServicesApi(oauth2)
var client = "client_example"; // {String} Client name
var cache = "cache_example"; // {String} Cache name
var key = "key_example"; // {String} Entry key
api.evictEntry(client, cache, key).then(function(data) {
  console.log('API called successfully. Returned data: ' + data);
}, function(error) {
  console.error(error);
});
```

