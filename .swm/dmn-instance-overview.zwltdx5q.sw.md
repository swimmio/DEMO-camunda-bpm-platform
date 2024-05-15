---
title: DMN Instance Overview
---
This document will cover the following aspects of DMN Instance in the Camunda BPM platform:

1. The role of DMN Instance in the codebase
2. The places where DMN Instance is implemented

<SwmSnippet path="/model-api/dmn-model/src/main/java/org/camunda/bpm/model/dmn/instance/DmnElement.java" line="19">

---

# Role of DMN Instance in the codebase

`DmnElement` is an interface that extends `DmnModelElementInstance`. It provides methods to get and set the ID, label, description, and extension elements of a DMN element. This interface is a fundamental part of the DMN model API, as it provides the basic structure for all DMN elements.

```java
public interface DmnElement extends DmnModelElementInstance {

  String getId();

  void setId(String id);

  String getLabel();

  void setLabel(String label);

  Description getDescription();

  void setDescription(Description description);

  ExtensionElements getExtensionElements();

  void setExtensionElements(ExtensionElements extensionElements);

}
```

---

</SwmSnippet>

<SwmSnippet path="/model-api/dmn-model/src/main/java/org/camunda/bpm/model/dmn/impl/instance/DmnElementImpl.java" line="34">

---

# Implementation of DMN Instance

`DmnElementImpl` is an abstract class that implements the `DmnElement` interface. It provides the implementation for the methods declared in `DmnElement`. This class is extended by other classes in the codebase to provide specific implementations for different types of DMN elements.

```java
public abstract class DmnElementImpl extends DmnModelElementInstanceImpl implements DmnElement {

  protected static Attribute<String> idAttribute;
  protected static Attribute<String> labelAttribute;

  protected static ChildElement<Description> descriptionChild;
  protected static ChildElement<ExtensionElements> extensionElementsChild;

  public DmnElementImpl (ModelTypeInstanceContext instanceContext) {
    super(instanceContext);
  }

  public String getId() {
    return idAttribute.getValue(this);
  }

  public void setId(String id) {
    idAttribute.setValue(this, id);
  }

  public String getLabel() {
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
