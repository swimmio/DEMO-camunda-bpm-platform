---
title: Exploring the Interaction between the Model API and the XML Models
---
This document will cover how the model API interacts with the XML models in the DEMO-camunda-bpm-platform repo. We'll cover:

1. The structure of the model API
2. How the model API interacts with XML models.

# Structure of the Model API

The model API is written in Java and is part of the 'camunda-xml-model' module. This module is responsible for handling XML models in the Camunda platform.

<SwmSnippet path="/model-api/xml-model/src/main/java/org/camunda/bpm/model/xml/impl/instance/ModelElementInstanceImpl.java" line="42">

---

# Interaction with XML Models

The `ModelElementInstanceImpl` class is a key part of how the model API interacts with XML models. It represents an instance of a model element and contains methods for interacting with the underlying XML, such as getting and setting attribute values. This class is used extensively throughout the codebase whenever interaction with XML models is required.

```java
/**
 * Base class for implementing Model Elements.
 *
 * @author Daniel Meyer
 *
 */
public class ModelElementInstanceImpl implements ModelElementInstance {

  /** the containing model instance */
  protected final ModelInstanceImpl modelInstance;
  /** the wrapped DOM {@link DomElement} */
  private final DomElement domElement;
  /** the implementing model element type */
  private final ModelElementTypeImpl elementType;

  public static void registerType(ModelBuilder modelBuilder) {
    ModelElementTypeBuilder typeBuilder = modelBuilder.defineType(ModelElementInstance.class, "")
      .abstractType();

    typeBuilder.build();
  }
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
