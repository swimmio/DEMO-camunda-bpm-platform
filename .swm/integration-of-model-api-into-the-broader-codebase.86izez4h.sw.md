---
title: Integration of model-api into the Broader Codebase
---
This document will cover the interaction of the model-api with the broader Camunda engine and its embedding into the larger codebase. We'll cover:

1. The role of the model-api in the Camunda engine
2. How the model-api is embedded into the larger codebase

# Role of the model-api in the Camunda engine

The model-api is a crucial part of the Camunda engine. It provides the XML model API written in Java, which is used to define and manipulate the BPMN models. This is evident from the `camunda-xml-model` document.

<SwmSnippet path="/model-api/bpmn-model/src/main/java/org/camunda/bpm/model/bpmn/Bpmn.java" line="261">

---

# Embedding of the model-api into the larger codebase

The `Bpmn` class in the model-api provides access to the Camunda BPMN model API. It includes methods for reading a `BpmnModelInstance` from a file or an input stream, and for writing a `BpmnModelInstance` to a file or an output stream. This class is used throughout the codebase, indicating how the model-api is embedded into the larger codebase.

```java
/**
 * <p>Provides access to the camunda BPMN model api.</p>
 *
 * @author Daniel Meyer
 *
 */
public class Bpmn {

  /** the singleton instance of {@link Bpmn}. If you want to customize the behavior of Bpmn,
   * replace this instance with an instance of a custom subclass of {@link Bpmn}. */
  public static Bpmn INSTANCE = new Bpmn();

  /** the parser used by the Bpmn implementation. */
  private BpmnParser bpmnParser = new BpmnParser();
  private final ModelBuilder bpmnModelBuilder;

  /** The {@link Model}
   */
  private Model bpmnModel;

  /**
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
