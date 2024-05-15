---
title: Overview of Engine Rest
---
This document will cover the following aspects of Engine Rest in the DEMO-camunda-bpm-platform repo:

1. The role and functionality of Engine Rest.
2. The implementation of Engine Rest in the codebase.

# Role and Functionality of Engine Rest

Engine Rest in the context of the Camunda BPM platform is a REST API that provides access to the process engine. It allows developers to interact with the process engine, perform operations, and retrieve data using HTTP requests. This makes it possible to integrate the process engine into various applications and services.

<SwmSnippet path="/engine-rest/engine-rest/src/main/java/org/camunda/bpm/engine/rest/impl/AbstractRestProcessEngineAware.java" line="56">

---

# Implementation of Engine Rest

The `getProcessEngine` method is a key part of the Engine Rest implementation. It retrieves the instance of the process engine that is currently in use. If no process engine is available, it throws an `InvalidRequestException`. This method is used throughout the codebase to access the process engine.

```java
  protected ProcessEngine getProcessEngine() {
    if (processEngine == null) {
      throw new InvalidRequestException(Status.BAD_REQUEST, "No process engine available");
    }
    return processEngine;
  }
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
