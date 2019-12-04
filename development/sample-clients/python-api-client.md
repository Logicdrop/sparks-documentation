# Python API Client

## Requirements.

Python 2.7 and 3.4+

## Installation & Usage

### pip install
We suggest using `pip` to install the package. In order to gain access to the Sparks package you will need to edit, or create, your `pip.conf` file if you are working 
from Unix or MacOS. The file you will need to edit is, `pip.ini` on Windows.

* On Unix the file can be found at, `$HOME/.config/pip/pip.conf`
* On MacOS the file can be found at either, `$HOME/Library/Application Support/pip/pip.conf` or `$HOME/.config/pip/pip.conf`
* On Windows the file can be found at `%APPDATA%\pip\pip.ini`

This file may not exist, so if that is the case you can create it in the desired location. The file should contain the
following contents,

```
[global]
index=https://{username}:{password}@depot.logicdrop.com/repository/pypi-public/pypi
index-url=https://{username}:{password}@depot.logicdrop.com/repository/pypi-public/simple
trusted-host=depot.logicdrop.com
```

Where `{username}` is your given username, and `{password}` is your given password to access the package.

Once you have configured pip to look at the Logicdrop location, you can run the command,

```
pip install logicdrop-sparks-openapi
```

Depending on your computer settings, you may need to run `pip` with root permissions,

```
sudo pip install logicdrop-sparks-openapi
```

### Getting Started
Inside a `.py` file, the following code is a quick example of how to implement `logicdrop-sparks-openapi`,

```python
from logicdrop.sparks.openapi.api.project_services_api import ProjectServicesApi
from logicdrop.sparks.openapi.configuration import Configuration
from logicdrop.sparks.openapi.api_client import ApiClient

configuration = Configuration()
configuration.access_token = 'ACCESS_TOKEN'

project_service = ProjectServicesApi(ApiClient(configuration))
client = 'CLIENT_NAME'

try:
  api_response = project_service.list_projects(client)
  # Do something with api_response here
  # print(api_response)
except:
  print("Exception when calling ProjectServicesApi->list_projects")
```



