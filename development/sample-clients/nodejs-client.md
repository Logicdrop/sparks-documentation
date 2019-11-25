# NodeJS API Client

## Installation

### For [Node.js](https://nodejs.org/)

#### npm

To publish the library as a [npm](https://www.npmjs.com/), please follow the procedure in ["Publishing npm packages"](https://docs.npmjs.com/getting-started/publishing-npm-packages).

Then install it via:

```text
npm install sparks_open_api --save
```

Finally, you need to build the module:

```text
npm run build
```

**Local development**

To use the library locally without publishing to a remote npm registry, first install the dependencies by changing into the directory containing `package.json` \(and this README\). Let's call this `JAVASCRIPT_CLIENT_DIR`. Then run:

```text
npm install
```

Next, [link](https://docs.npmjs.com/cli/link) it globally in npm with the following, also from `JAVASCRIPT_CLIENT_DIR`:

```text
npm link
```

To use the link you just defined in your project, switch to the directory you want to use your sparks\_open\_api from, and run:

```text
npm link /path/to/<JAVASCRIPT_CLIENT_DIR>
```

Finally, you need to build the module:

```text
npm run build
```

#### git

If the library is hosted at a git repository, e.g.[https://github.com/GIT\_USER\_ID/GIT\_REPO\_ID](https://github.com/GIT_USER_ID/GIT_REPO_ID) then install it via:

```text
    npm install GIT_USER_ID/GIT_REPO_ID --save
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

Please follow the [installation]() instruction and execute the following JS code:

```javascript
var SparksOpenApi = require('sparks_open_api');

var defaultClient = SparksOpenApi.ApiClient.instance;
// Configure API key authorization: api
var api = defaultClient.authentications['api'];
api.apiKey = "YOUR API KEY"
// Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
//api.apiKeyPrefix['X-Logicdrop-ApiKey'] = "Token"
// Configure Bearer (JWT) access token for authorization: jwt
var jwt = defaultClient.authentications['jwt'];
jwt.accessToken = "YOUR ACCESS TOKEN"
// Configure OAuth2 access token for authorization: oauth2
var oauth2 = defaultClient.authentications['oauth2'];
oauth2.accessToken = "YOUR ACCESS TOKEN"

var api = new SparksOpenApi.CacheServicesApi()
var client = "client_example"; // {String} Client name
var cache = "cache_example"; // {String} Cache name
var key = "key_example"; // {String} Entry key
api.evictEntry(client, cache, key).then(function(data) {
  console.log('API called successfully. Returned data: ' + data);
}, function(error) {
  console.error(error);
});
```

