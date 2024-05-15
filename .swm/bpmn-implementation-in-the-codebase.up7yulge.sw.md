---
title: BPMN Implementation in the Codebase
---
This document will cover the implementation of BPMN in the DEMO-camunda-bpm-platform repository. We'll cover:

1. The role of BPMN Implementation in the codebase
2. The places where BPMN Implementation is used

<SwmSnippet path="/model-api/bpmn-model/src/main/java/org/camunda/bpm/model/bpmn/impl/BpmnModelConstants.java" line="27">

---

# Role of BPMN Implementation

The `BpmnModelConstants` class contains global constants that are used throughout the BPMN implementation. These constants include namespaces, schema locations, element names, and attribute names. They are used to ensure consistency and avoid hard-coding of strings in the codebase.

```java

  /** The XSI namespace */
  public static final String XSI_NS = "http://www.w3.org/2001/XMLSchema-instance";

  /** The BPMN 2.0 namespace */
  public static final String BPMN20_NS = "http://www.omg.org/spec/BPMN/20100524/MODEL";

  /** The BPMNDI namespace */
  public static final String BPMNDI_NS = "http://www.omg.org/spec/BPMN/20100524/DI";

  /** The DC namespace */
  public static final String DC_NS = "http://www.omg.org/spec/DD/20100524/DC";

  /** The DI namespace */
  public static final String DI_NS = "http://www.omg.org/spec/DD/20100524/DI";

  /** The location of the BPMN 2.0 XML schema. */
  public static final String BPMN_20_SCHEMA_LOCATION = "org/camunda/bpm/model/bpmn/schema/BPMN20.xsd";

  /** Xml Schema is the default type language */
  public static final String XML_SCHEMA_NS = "http://www.w3.org/2001/XMLSchema";
```

---

</SwmSnippet>

<SwmSnippet path="/model-api/bpmn-model/src/main/java/org/camunda/bpm/model/bpmn/impl/instance/BusinessRuleTaskImpl.java" line="82">

---

# Usage of BPMN Implementation

The `BPMN_ATTRIBUTE_IMPLEMENTATION` constant is used in the `BusinessRuleTaskImpl` class to set the default value of the `implementationAttribute`.

```java
    implementationAttribute = typeBuilder.stringAttribute(BPMN_ATTRIBUTE_IMPLEMENTATION)
      .defaultValue("##unspecified")
```

---

</SwmSnippet>

<SwmSnippet path="/model-api/bpmn-model/src/main/java/org/camunda/bpm/model/bpmn/impl/instance/UserTaskImpl.java" line="86">

---

The `BPMN_ATTRIBUTE_IMPLEMENTATION` constant is also used in the `UserTaskImpl` class to set the default value of the `implementationAttribute`.

```java
    implementationAttribute = typeBuilder.stringAttribute(BPMN_ATTRIBUTE_IMPLEMENTATION)
      .defaultValue("##unspecified")
```

---

</SwmSnippet>

<SwmSnippet path="/model-api/bpmn-model/src/main/java/org/camunda/bpm/model/bpmn/impl/instance/ServiceTaskImpl.java" line="63">

---

The `BPMN_ATTRIBUTE_IMPLEMENTATION` constant is used in the `ServiceTaskImpl` class to set the default value of the `implementationAttribute`.

```java
    implementationAttribute = typeBuilder.stringAttribute(BPMN_ATTRIBUTE_IMPLEMENTATION)
      .defaultValue("##WebService")
```

---

</SwmSnippet>

<SwmSnippet path="/model-api/bpmn-model/src/main/java/org/camunda/bpm/model/bpmn/impl/instance/ReceiveTaskImpl.java" line="56">

---

The `BPMN_ATTRIBUTE_IMPLEMENTATION` constant is used in the `ReceiveTaskImpl` class to set the default value of the `implementationAttribute`.

```java
    implementationAttribute = typeBuilder.stringAttribute(BPMN_ATTRIBUTE_IMPLEMENTATION)
      .defaultValue("##WebService")
```

---

</SwmSnippet>

<SwmSnippet path="/model-api/bpmn-model/src/main/java/org/camunda/bpm/model/bpmn/impl/instance/SendTaskImpl.java" line="65">

---

The `BPMN_ATTRIBUTE_IMPLEMENTATION` constant is used in the `SendTaskImpl` class to set the default value of the `implementationAttribute`.

```java
    implementationAttribute = typeBuilder.stringAttribute(BPMN_ATTRIBUTE_IMPLEMENTATION)
      .defaultValue("##WebService")
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
