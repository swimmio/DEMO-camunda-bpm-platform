---
title: BPMN Model Overview
---
This document will cover the following aspects of the BPMN Model in the DEMO-camunda-bpm-platform repo:

1. The structure and usage of the BPMN Model
2. The implementation of the BPMN Model in the codebase.

<SwmSnippet path="/model-api/bpmn-model/src/main/java/org/camunda/bpm/model/bpmn/Bpmn.java" line="261">

---

# Structure and Usage of the BPMN Model

The `Bpmn` class provides access to the Camunda BPMN model API. It includes methods for reading a `BpmnModelInstance` from a file or an input stream, writing a `BpmnModelInstance` to a file or an output stream, validating a `BpmnModelInstance`, and creating an empty `BpmnModelInstance` or a process. The `Bpmn` class also contains a `Model` instance, which is used to represent the BPMN model.

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

<SwmSnippet path="/model-api/bpmn-model/src/main/java/org/camunda/bpm/model/bpmn/impl/BpmnModelConstants.java" line="19">

---

# Implementation of the BPMN Model in the Codebase

The `BpmnModelConstants` class defines constants used in the BPMN 2.0 Language (DI + Semantic). These constants include namespaces, schema locations, and element names. This class is used throughout the codebase to ensure consistency when working with the BPMN model.

```java
/**
 * Constants used in the BPMN 2.0 Language (DI + Semantic)
 *
 * @author Daniel Meyer
 * @author Falko Menge
 *
 */
public final class BpmnModelConstants {

  /** The XSI namespace */
  public static final String XSI_NS = "http://www.w3.org/2001/XMLSchema-instance";

  /** The BPMN 2.0 namespace */
  public static final String BPMN20_NS = "http://www.omg.org/spec/BPMN/20100524/MODEL";

  /** The BPMNDI namespace */
  public static final String BPMNDI_NS = "http://www.omg.org/spec/BPMN/20100524/DI";

  /** The DC namespace */
  public static final String DC_NS = "http://www.omg.org/spec/DD/20100524/DC";

```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
