# Authorizing Requests to the API

To authorize requests to the Sparks API from a back-end application, a application must be created to provide a token via the Machine Credentials OAuth2 flow.

{% hint style="info" %}
When using the Sparks Portal UI, the token is obtained for your specific user account in the background.
{% endhint %}

### Create a machine-to-machine credential

An application credential allows access to the Sparks API for a single client at a specified role. 

1. In the Sparks Portal user interface, access the client settings, then applications. 
2. Create a new application and specify the role to designate \(usually Admin.\)
3. Make note of the newly assigned `Client ID` and `Client Secret`.

### Obtaining a token

The following request can be made to the Sparks Authorization server to obtain a token.

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
{% api-method-parameter name="Content-Type" type="string" required=false %}
application/json
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="client\_id" type="string" required=false %}
{{Your client ID}}
{% endapi-method-parameter %}

{% api-method-parameter name="client\_secret" type="string" required=false %}
{{Your client secret}}
{% endapi-method-parameter %}

{% api-method-parameter name="audience" type="string" required=false %}
https://api.logicdrop.io
{% endapi-method-parameter %}

{% api-method-parameter name="grant\_type" type="string" required=false %}
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



