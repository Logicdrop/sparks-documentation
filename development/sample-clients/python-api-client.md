# Python API Client

## Requirements.

Python 2.7 and 3.4+

## Installation & Usage

### pip install

If the python package is hosted on a repository, you can install directly using:

```bash
pip install git+https://github.com/GIT_USER_ID/GIT_REPO_ID.git
```

\(you may need to run `pip` with root permission: `sudo pip install git+https://github.com/GIT_USER_ID/GIT_REPO_ID.git`\)

Then import the package:

```python
import logicdrop.sparks.openapi
```

### Setuptools

Install via [Setuptools](http://pypi.python.org/pypi/setuptools).

```bash
python setup.py install --user
```

\(or `sudo python setup.py install` to install the package for all users\)

Then import the package:

```python
import logicdrop.sparks.openapi
```

## Getting Started

Please follow the [installation procedure]() and then run the following:

```python
from __future__ import print_function
import time
import logicdrop.sparks.openapi
from logicdrop.sparks.openapi.rest import ApiException
from pprint import pprint

configuration = logicdrop.sparks.openapi.Configuration()
# Configure API key authorization: api
configuration.api_key['X-Logicdrop-ApiKey'] = 'YOUR_API_KEY'
# Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
# configuration.api_key_prefix['X-Logicdrop-ApiKey'] = 'Bearer'
configuration = logicdrop.sparks.openapi.Configuration()
# Configure Bearer authorization (JWT): jwt
configuration.access_token = 'YOUR_BEARER_TOKEN'
configuration = logicdrop.sparks.openapi.Configuration()
# Configure OAuth2 access token for authorization: oauth2
configuration.access_token = 'YOUR_ACCESS_TOKEN'

# Defining host is optional and default to https://api.staging.com
configuration.host = "https://api.staging.com"
# Create an instance of the API class
api_instance = logicdrop.sparks.openapi.CacheServicesApi(logicdrop.sparks.openapi.ApiClient(configuration))
client = 'client_example' # str | Client name
cache = 'cache_example' # str | Cache name
key = 'key_example' # str | Entry key

try:
    # Evict cache entry
    api_response = api_instance.evict_entry(client, cache, key)
    pprint(api_response)
except ApiException as e:
    print("Exception when calling CacheServicesApi->evict_entry: %s\n" % e)
```



