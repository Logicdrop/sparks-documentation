# Java Spring API Client

## Requirements

Building the API client library requires:

1. Java 1.8+
2. Maven/Gradle

## Installation

To install the API client library to your local Maven repository, simply execute:

```text
mvn clean install
```

To deploy it to a remote Maven repository instead, configure the settings of the repository and execute:

```text
mvn clean deploy
```

Refer to the [OSSRH Guide](http://central.sonatype.org/pages/ossrh-guide.html) for more information.

### Maven users

Add this dependency to your project's POM:

```markup
<dependency>
  <groupId>io.logicdrop.sparks</groupId>
  <artifactId>sparks-openapi-spring</artifactId>
  <version>4.3.2-SNAPSHOT</version>
  <scope>compile</scope>
</dependency>
```

### Gradle users

Add this dependency to your project's build file:

```groovy
compile "io.logicdrop.sparks:sparks-openapi-spring:4.1.1-SNAPSHOT"
```

### Others

At first generate the JAR by executing:

```text
mvn clean package
```

Then manually install the following JARs:

* `target/sparks-openapi-spring-4.1.1-SNAPSHOT.jar`
* `target/lib/*.jar`

## Getting Started

Please follow the [installation]() instruction and execute the following Java code:

```java
import io.logicdrop.openapi.spring.*;
import io.logicdrop.openapi.spring.auth.*;
import io.logicdrop.openapi.spring.models.*;
import io.logicdrop.openapi.spring.api.CacheServicesApi;

public class CacheServicesApiExample {

    public static void main(String[] args) {
        ApiClient defaultClient = new ApiClient();
        defaultClient.setBasePath("https://api.staging.com");

        // Configure API key authorization: api
        ApiKeyAuth api = (ApiKeyAuth) defaultClient.getAuthentication("api");
        api.setApiKey("YOUR API KEY");
        // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
        //api.setApiKeyPrefix("Token");

        // Configure HTTP bearer authorization: jwt
        HttpBearerAuth jwt = (HttpBearerAuth) defaultClient.getAuthentication("jwt");
        jwt.setBearerToken("BEARER TOKEN");

        // Configure OAuth2 access token for authorization: oauth2
        OAuth oauth2 = (OAuth) defaultClient.getAuthentication("oauth2");
        oauth2.setAccessToken("YOUR ACCESS TOKEN");

        CacheServicesApi apiInstance = new CacheServicesApi(defaultClient);
        String client = "client_example"; // String | Client name
        String cache = "cache_example"; // String | Cache name
        String key = "key_example"; // String | Entry key
        try {
            String result = apiInstance.evictEntry(client, cache, key);
            System.out.println(result);
        } catch (ApiException e) {
            System.err.println("Exception when calling CacheServicesApi#evictEntry");
            System.err.println("Status code: " + e.getCode());
            System.err.println("Reason: " + e.getResponseBody());
            System.err.println("Response headers: " + e.getResponseHeaders());
            e.printStackTrace();
        }
    }
}
```

## Recommendation

It's recommended to create an instance of `ApiClient` per thread in a multithreaded environment to avoid any potential issues.

