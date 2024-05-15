---
title: Overview of the engine-cdi Module
---
This document will cover the following aspects of the engine-cdi module in the Camunda BPM Platform:

1. The role of engine-cdi in the Camunda BPM Platform.
2. The implementation of engine-cdi in the codebase.

# Role of engine-cdi

The engine-cdi module in the Camunda BPM Platform is a core component that provides Contexts and Dependency Injection (CDI) support for the process engine. It is defined as an artifact with the ID `camunda-engine-cdi` in the `pom.xml` file of the `engine-cdi/core` directory. The module includes a set of classes and interfaces that facilitate the integration of the process engine with CDI-enabled environments.

<SwmSnippet path="/engine-cdi/core/src/main/java/org/camunda/bpm/engine/cdi/ProcessEngineCdiException.java" line="26">

---

# Implementation of engine-cdi

One of the key classes in the engine-cdi module is the `ProcessEngineCdiException` class. This class represents exceptions that occur within the engine-cdi module. It is used extensively throughout the codebase to handle error conditions related to the process engine's interaction with CDI.

```java
public class ProcessEngineCdiException extends ProcessEngineException {

  private static final long serialVersionUID = 1L;

  public ProcessEngineCdiException(String message, Throwable cause) {
    super(message, cause);
  }

  public ProcessEngineCdiException(String message) {
    super(message);  
  }

}
```

---

</SwmSnippet>

<SwmSnippet path="/engine-cdi/core/src/main/java/org/camunda/bpm/engine/cdi/CdiStandaloneProcessEngineConfiguration.java" line="24">

---

The `CdiStandaloneProcessEngineConfiguration` class is another important part of the engine-cdi module. This class extends the `StandaloneProcessEngineConfiguration` class and overrides the `initExpressionManager` method to use the `CdiExpressionManager`. This allows the process engine to work with expressions in a CDI context.

```java
public class CdiStandaloneProcessEngineConfiguration extends StandaloneProcessEngineConfiguration {

  @Override
  protected void initExpressionManager() {
    expressionManager = new CdiExpressionManager();
    super.initExpressionManager();
  }

  @Override
  protected void initArtifactFactory() {
    artifactFactory = new CdiArtifactFactory();
  }
}
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
