---
title: Future Enhancements of the DMN Model
---
This document will cover the functionality of the DMN Model in the DEMO-camunda-bpm-platform repository, focusing on:

1. The role and usage of the DMN Model
2. The methods associated with the DMN Model

<SwmSnippet path="/model-api/dmn-model/src/main/java/org/camunda/bpm/model/dmn/Dmn.java" line="128">

---

# Role and Usage of the DMN Model

The DMN Model is represented by the `Dmn` class. It provides methods for reading and writing DMN Model Instances from and to files or streams, validating the model, and creating an empty model. It also registers known types of the DMN model.

```java
public class Dmn {

  /** the singleton instance of {@link Dmn}. If you want to customize the behavior of Dmn,
   * replace this instance with an instance of a custom subclass of {@link Dmn}. */
  public static Dmn INSTANCE = new Dmn();

  /** the parser used by the Dmn implementation. */
  private DmnParser dmnParser = new DmnParser();
  private final ModelBuilder dmnModelBuilder;

  /** The {@link Model}
   */
  private Model dmnModel;

  /**
   * Allows reading a {@link DmnModelInstance} from a File.
   *
   * @param file the {@link File} to read the {@link DmnModelInstance} from
   * @return the model read
   * @throws DmnModelException if the model cannot be read
   */
```

---

</SwmSnippet>

<SwmSnippet path="/model-api/dmn-model/src/main/java/org/camunda/bpm/model/dmn/Dmn.java" line="381">

---

# Methods Associated with the DMN Model

The `getDmnModel` method is used to retrieve the current DMN Model instance.

```java
  /**
   * @return the {@link Model} instance to use
   */
  public Model getDmnModel() {
    return dmnModel;
  }
```

---

</SwmSnippet>

<SwmSnippet path="/model-api/dmn-model/src/main/java/org/camunda/bpm/model/dmn/Dmn.java" line="392">

---

The `setDmnModel` method is used to set a new DMN Model instance.

```java
  /**
   * @param dmnModel the cmmnModel to set
   */
  public void setDmnModel(Model dmnModel) {
    this.dmnModel = dmnModel;
  }
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
