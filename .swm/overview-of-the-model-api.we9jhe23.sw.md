---
title: Overview of the Model-API
---
This document will cover the following aspects of the model-api in the DEMO-camunda-bpm-platform repository:

1. The implementation of model-api in different modules.
2. The functionality and usage of model-api in the codebase.

# Implementation of model-api

The model-api is implemented in several modules within the repository. These modules include xml-model, dmn-model, bpmn-model, and cmmn-model. Each of these modules has its own source code and resources, which are organized in a specific directory structure.

<SwmSnippet path="/model-api/cmmn-model/src/main/java/org/camunda/bpm/model/cmmn/Cmmn.java" line="135">

---

# Functionality and Usage of model-api

The `Cmmn` class in the cmmn-model module is a key part of the model-api. It provides methods for reading and writing CmmnModelInstances from and to various sources (like Files and InputStreams), validating the model instances, and converting them to String. It also provides a method to create an empty CmmnModelInstance. The `Cmmn` class is used in various parts of the codebase, including the engine and model-api modules.

```java
/**
 * @author Roman Smirnov
 *
 */
public class Cmmn {

  /** the singleton instance of {@link Cmmn}. If you want to customize the behavior of Cmmn,
   * replace this instance with an instance of a custom subclass of {@link Cmmn}. */
  public static Cmmn INSTANCE = new Cmmn();

  /** the parser used by the Cmmn implementation. */
  private CmmnParser cmmnParser = new CmmnParser();
  private final ModelBuilder cmmnModelBuilder;

  /** The {@link Model}
   */
  private Model cmmnModel;

  /**
   * Allows reading a {@link CmmnModelInstance} from a File.
   *
```

---

</SwmSnippet>

<SwmSnippet path="/model-api/cmmn-model/src/main/java/org/camunda/bpm/model/cmmn/Cmmn.java" line="401">

---

The `getCmmnModel` method in the `Cmmn` class returns the Model instance to use. This method is used in the `CmmnParser` class to create a new `CmmnModelInstanceImpl`.

```java
  /**
   * @return the {@link Model} instance to use
   */
  public Model getCmmnModel() {
    return cmmnModel;
  }
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
