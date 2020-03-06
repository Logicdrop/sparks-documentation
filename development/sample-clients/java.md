# Java API Client

## Requirements

Building the API client library requires:

1. Java 11+
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
  <artifactId>sparks-openapi-java</artifactId>
  <version>4.3.2-SNAPSHOT</version>
  <scope>compile</scope>
</dependency>
```

### Gradle users

Add this dependency to your project's build file:

```groovy
compile "io.logicdrop.sparks:sparks-openapi-java:4.1.1-SNAPSHOT"
```

### Others

At first generate the JAR by executing:

```text
mvn clean package
```

Then manually install the following JARs:

* `target/sparks-openapi-java-4.1.1-SNAPSHOT.jar`
* `target/lib/*.jar`

## Getting Started

Please follow the [installation](java.md) instruction and execute the following Java code:

```java
import io.logicdrop.openapi.java.*;
import io.logicdrop.openapi.java.models.*;
import io.logicdrop.openapi.java.api.CacheServicesApi;

public class CacheServicesApiExample {

    public static void main(String[] args) {
        ApiClient defaultClient = new ApiClient();
        // Configure clients using the `defaultClient` object, such as
        // overriding the host and port, timeout, etc.
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

It's recommended to create an instance of `ApiClient` per thread in a multithreaded environment to avoid any potential issues. However, the instances of the api clients created from the `ApiClient` are thread-safe and can be re-used.

