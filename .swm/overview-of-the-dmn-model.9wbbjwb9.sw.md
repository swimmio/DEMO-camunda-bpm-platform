---
title: Overview of the DMN Model
---
This document will cover the following aspects of the DMN Model in the DEMO-camunda-bpm-platform repo:

1. The purpose and usage of the DMN Model
2. The methods and classes related to the DMN Model
3. The implementation of the DMN Model in the codebase.

# Purpose and Usage of the DMN Model

The DMN Model in the DEMO-camunda-bpm-platform repo is an integral part of the Decision Model and Notation (DMN) standard. It is used to define and manage business decisions in a standardized manner. The DMN Model is implemented in the `Dmn` class and is used throughout the codebase to handle various aspects of decision management.

<SwmSnippet path="/model-api/dmn-model/src/main/java/org/camunda/bpm/model/dmn/Dmn.java" line="128">

---

# Methods and Classes Related to the DMN Model

The `Dmn` class is the main class that implements the DMN Model. It contains methods such as `getDmnModel`, `setDmnModel`, and `validateModel` which are used to interact with the DMN Model. The `DmnModelInstance` interface is also a crucial part of the DMN Model, providing methods to interact with instances of the DMN Model.

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

<SwmSnippet path="/engine-dmn/engine/src/main/java/org/camunda/bpm/dmn/engine/impl/DefaultDmnEngine.java" line="59">

---

# Implementation of the DMN Model in the Codebase

The `DefaultDmnEngine` class uses the DMN Model to parse and evaluate decision tables. It uses the `Dmn` class to read the DMN Model from a file or a stream, and then uses the `DmnModelInstance` to interact with the parsed DMN Model.

```java
  public List<DmnDecision> parseDecisions(DmnModelInstance dmnModelInstance) {
    ensureNotNull("dmnModelInstance", dmnModelInstance);
    return transformer.createTransform()
      .modelInstance(dmnModelInstance)
      .transformDecisions();
  }

  public DmnDecision parseDecision(String decisionKey, InputStream inputStream) {
    ensureNotNull("decisionKey", decisionKey);
    List<DmnDecision> decisions = parseDecisions(inputStream);
    for (DmnDecision decision : decisions) {
      if (decisionKey.equals(decision.getKey())) {
        return decision;
      }
    }
    throw LOG.unableToFindDecisionWithKey(decisionKey);
  }

  public DmnDecision parseDecision(String decisionKey, DmnModelInstance dmnModelInstance) {
    ensureNotNull("decisionKey", decisionKey);
    List<DmnDecision> decisions = parseDecisions(dmnModelInstance);
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
