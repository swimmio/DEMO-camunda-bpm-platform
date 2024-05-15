---
title: Overview of the CMMN Model
---
This document will cover the following aspects of the CMMN Model in the DEMO-camunda-bpm-platform repo:

1. The role of the CMMN Model in the codebase
2. How the CMMN Model is implemented and used in the codebase.

# Role of the CMMN Model

The CMMN Model in the DEMO-camunda-bpm-platform repo is a crucial component of the Camunda Platform's workflow and process automation capabilities. It is used to define and manage the lifecycle of case management models, which are a type of process model used in complex and unpredictable scenarios.

<SwmSnippet path="/model-api/cmmn-model/src/main/java/org/camunda/bpm/model/cmmn/Cmmn.java" line="135">

---

# Implementation and Usage of the CMMN Model

The `Cmmn` class is the main entry point for working with the CMMN Model. It provides methods for reading a model from a file or stream, writing a model to a file or stream, and creating an empty model. It also provides access to the `CmmnModelInstance`, which represents a CMMN model instance, and the `CmmnModelBuilder`, which is used to build the CMMN model.

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

<SwmSnippet path="/model-api/cmmn-model/src/main/java/org/camunda/bpm/model/cmmn/CmmnModelInstance.java" line="22">

---

The `CmmnModelInstance` interface represents a CMMN model instance. It provides methods for getting and setting the definitions of the model, and for cloning the model instance.

```java
/**
 * @author Roman Smirnov
 *
 */
public interface CmmnModelInstance extends ModelInstance {

  /**
   * @return the {@link Definitions}, root element of the Cmmn Model.
   * */
  Definitions getDefinitions();

  /**
   * Set the Cmmn Definitions Root element
   * @param definitions the {@link Definitions} element to set
   * */
  void setDefinitions(Definitions definitions);

  /**
   * Copies the CMMN model instance but not the model. So only the wrapped DOM document is cloned.
   * Changes of the model are persistent between multiple model instances.
   *
```

---

</SwmSnippet>

<SwmSnippet path="/model-api/cmmn-model/src/main/java/org/camunda/bpm/model/cmmn/Cmmn.java" line="222">

---

The `createEmptyModel` method in the `Cmmn` class is used to create a new, empty CMMN model instance.

```java
  /**
   * Allows creating an new, empty {@link CmmnModelInstance}.
   *
   * @return the empty model.
   */
  public static CmmnModelInstance createEmptyModel() {
    return INSTANCE.doCreateEmptyModel();
  }
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
