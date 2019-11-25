# Authorizing Requests to the API

To authorize requests to the Sparks API from a back-end application, an application must be created to provide a token via the Machine Credentials OAuth2 flow.

{% hint style="info" %}
When using the Sparks Portal UI, a token is obtained for your specific user account in the background and these steps are not required.
{% endhint %}

### Creating a machine-to-machine credential

An application credential allows access to the Sparks API for a specific client at a specified role. 

1. In the Sparks Portal user interface, access the client settings, then applications. 
2. Create a new application and specify the role to designate \(usually Admin.\)
3. Make note of the newly assigned `Client ID` and `Client Secret`.

An application may also be created from the Sparks API \(with a valid token of course\): [Sparks API: Create an Application](https://docs.logicdrop.io/#operation/createApplication)

{% hint style="warning" %}
Be careful with these credentials! Practice good secret management and never share them or check them in to source control, or others may gain access to your Sparks account data.
{% endhint %}

### Obtaining a token

Next, use the client ID and secret you obtained to make a token request to the Sparks Authorization server:

```bash
{
    "client_id":"{{Your client ID}}",
    "client_secret":"{{Your client secret}}",
    "audience":"https://api.logicdrop.io",
    "grant_type":"client_credentials"
}
```

{% api-method method="post" host="https://auth.logicdrop.io" path="/oauth/token" %}
{% api-method-summary %}
Request a token
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
{{Your client ID}}
{% endapi-method-parameter %}

{% api-method-parameter name="client\_secret" type="string" required=true %}
{{Your client secret}}
{% endapi-method-parameter %}

{% api-method-parameter name="audience" type="string" required=true %}
https://api.logicdrop.io
{% endapi-method-parameter %}

{% api-method-parameter name="grant\_type" type="string" required=true %}
client\_credentials
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "access_token": "eyJ0eXAiOiJKV1QiLCJhbG...",
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
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1N...
```

### Refreshing the token

When a token is close to expiration, repeat the token request to obtain a fresh token. At this time the authorization server does not accept refresh tokens for machine-to-machine tokens for security. The default token expiration is 24 hours.

### Rotating Secrets and Revoking Access

It is recommended occasionally to rotate the secret for your issued application credentials. Using the rotate secret option in the Portal UI or Sparks API will rotate and return a new secret \(the old secret will no longer function.\) 

If you wish to remove access completely for an application, deleting the application in the Portal UI or Sparks API will decommission it for future token requests.

