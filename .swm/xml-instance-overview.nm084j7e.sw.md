---
title: XML Instance Overview
---
This document will cover the following aspects of XML Instance in the Camunda BPM Platform:

1. The role of XML Instance in the codebase
2. The places where XML Instance is implemented

<SwmSnippet path="/model-api/xml-model/src/main/java/org/camunda/bpm/model/xml/instance/ModelElementInstance.java" line="26">

---

# Role of XML Instance in the codebase

The `ModelElementInstance` interface in the `org.camunda.bpm.model.xml.instance` package represents an instance of a `ModelElementType`. It provides methods to manipulate the underlying DOM element, manage attributes, and handle child elements. This interface is central to the XML model as it provides the necessary operations to interact with the XML instances.

```java
/**
 * An instance of a {@link ModelElementType}
 *
 * @author Daniel Meyer
 *
 */
public interface ModelElementInstance {

  /**
   * Returns the represented DOM {@link DomElement}.
   *
   * @return the DOM element
   */
  DomElement getDomElement();

  /**
   * Returns the model instance which contains this type instance.
   *
   * @return the model instance
   */

```

---

</SwmSnippet>

<SwmSnippet path="/model-api/xml-model/src/main/java/org/camunda/bpm/model/xml/instance/ModelElementInstance.java" line="26">

---

# Implementation of XML Instance

The `ModelElementInstance` interface is implemented in various places across the codebase. For instance, it is used in `DomElement.java` to associate a `ModelElementInstance` with a DOM element. It is also used in `ModelInstance.java` to create new instances of a `ModelElementInstance`. Moreover, it is used in `ModelElementInstanceImpl.java` to provide the actual implementation of the `ModelElementInstance` interface.

```java
/**
 * An instance of a {@link ModelElementType}
 *
 * @author Daniel Meyer
 *
 */
public interface ModelElementInstance {

  /**
   * Returns the represented DOM {@link DomElement}.
   *
   * @return the DOM element
   */
  DomElement getDomElement();

  /**
   * Returns the model instance which contains this type instance.
   *
   * @return the model instance
   */

```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
