---
title: Engine-Rest Module Overview
---
This document will cover the following aspects of the engine-rest module in the Camunda BPM Platform:

1. The role and functionality of the EngineRestApplication class.
2. The usage of the EngineRestApplication class in different parts of the codebase.
3. The structure and content of the engine-rest directory.

<SwmSnippet path="/webapps/assembly/src/main/java/org/camunda/bpm/webapp/impl/engine/EngineRestApplication.java" line="27">

---

# Role and Functionality of EngineRestApplication

The EngineRestApplication class is a key component of the engine-rest module. It extends the Application class and overrides the getClasses method. This method returns a set of classes that provide named process engine access and configuration classes for the Camunda REST API.

```java
/**
 * The engine rest api exposed by the application.
 *
 * @author nico.rehwaldt
 */
public class EngineRestApplication extends Application {

  @Override
  public Set<Class<?>> getClasses() {
    Set<Class<?>> classes = new HashSet<Class<?>>();

    // only provide named process engine access.
    classes.add(NamedProcessEngineRestServiceImpl.class);

    // mandatory
    classes.addAll(CamundaRestResources.getConfigurationClasses());

    return classes;
  }
}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-boot-starter/starter-webapp-core/src/main/java/org/camunda/bpm/spring/boot/starter/webapp/CamundaBpmWebappInitializer.java" line="141">

---

# Usage of EngineRestApplication

The EngineRestApplication class is registered as a servlet in the CamundaBpmWebappInitializer class. This allows the engine-rest API to be exposed at the '/api/engine/\*' path.

```java
    registerServlet("Engine Api", EngineRestApplication.class,
        applicationPath + "/api/engine/*");
```

---

</SwmSnippet>

# Structure and Content of engine-rest Directory

The engine-rest directory contains several subdirectories, each serving a specific purpose. The engine-rest/src directory contains the source code for the engine-rest module. The engine-rest-openapi directory contains templates and resources for the OpenAPI specification of the engine-rest API.

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
