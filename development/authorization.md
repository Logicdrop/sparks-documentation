# Authorizing Requests to the API

To authorize requests to the Sparks API, you can request a token using your username and password via the Password Grant OAuth2 flow. Though you could use your normal user account for this, we recommend creating a dedicated "API" user for remote use of the API. For example, "api@mycompany.com".

{% hint style="info" %}
When using the Sparks Portal UI, a token is obtained for your specific user account in the background and these steps are not required.
{% endhint %}

## User Password

### Obtaining an API token using a Sparks user and password 

To obtain a token to access the API, initiate a Password Grant OAuth2  request, using the following request body as a guide.

```bash
{
    "client_id":"rLxjriMyfD3PAdXTQfFyKFUODrseHvSg",
    "username": "{{Your username}}",
    "password":"{{Your password}}",
    "audience":"https://api.logicdrop.io",
    "grant_type":"password"
}
```

{% hint style="info" %}
The client ID is required and will be the same for every request.
{% endhint %}

{% api-method method="post" host="https://auth.logicdrop.io" path="/oauth/token" %}
{% api-method-summary %}
Request an API token
{% endapi-method-summary %}

{% api-method-description %}
Request an access token
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Content-Type" type="string" required=true %}
application/json
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="client\_id" type="string" required=true %}
rLxjriMyfD3PAdXTQfFyKFUODrseHvSg
{% endapi-method-parameter %}

{% api-method-parameter name="username" type="string" required=true %}
Your API user name
{% endapi-method-parameter %}

{% api-method-parameter name="password" type="string" required=true %}
Your API user password
{% endapi-method-parameter %}

{% api-method-parameter name="audience" type="string" required=true %}
https://api.logicdrop.io
{% endapi-method-parameter %}

{% api-method-parameter name="grant\_type" type="string" required=true %}
password
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
{
    "access_token": "...",
    "scope": "data admin core",
    "expires_in": 2592000,
    "token_type": "Bearer"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Use the token

Finally, use the token you have obtained in requests to the Sparks API by including it as a JWT bearer token in the `Authorization` header:

```bash
Authorization: Bearer ...
```

### Refreshing the token

When a token is close to expiration, repeat the token request to obtain a fresh token. At this time the authorization server does not accept refresh tokens for machine-to-machine tokens for security. The default token expiration is 24 hours.



