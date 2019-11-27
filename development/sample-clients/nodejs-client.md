# NodeJS API Client

## Installation

### For [Node.js](https://nodejs.org/)

#### npm

Install the Sparks API package via:

```text
npm install @logicdrop/sparks-openapi-nodejs --save
```

Finally, you need to build the module:

```text
npm run build
```

### For browser

The library also works in the browser environment via npm and [browserify](http://browserify.org/). After following the above steps with Node.js and installing browserify with `npm install -g browserify`, perform the following \(assuming _main.js_ is your entry file\):

```text
browserify main.js > bundle.js
```

Then include _bundle.js_ in the HTML pages.

### Webpack Configuration

Using Webpack you may encounter the following error: "Module not found: Error: Cannot resolve module", most certainly you should disable AMD loader. Add/merge the following section to your webpack config:

```javascript
module: {
  rules: [
    {
      parser: {
        amd: false
      }
    }
  ]
}
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

