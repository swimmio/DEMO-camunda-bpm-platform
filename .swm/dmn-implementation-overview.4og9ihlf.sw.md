---
title: DMN Implementation Overview
---
This document will cover the DMN Implementation in the Camunda BPM platform. We'll cover:

1. What DMN Implementation does
2. How DMN Implementation is used in the codebase
3. Code snippets related to DMN Implementation

<SwmSnippet path="/model-api/dmn-model/src/main/java/org/camunda/bpm/model/dmn/impl/DmnParser.java" line="52">

---

# DMN Implementation in Action

The `DmnParser` class is a key part of the DMN Implementation. It initializes the schema factory and adds schemas for different DMN versions. This is where the DMN Implementation begins its work.

```java
  public DmnParser() {
    this.schemaFactory = SchemaFactory.newInstance(W3C_XML_SCHEMA);
    addSchema(DMN15_NS, createSchema(DMN_15_SCHEMA_LOCATION, DmnParser.class.getClassLoader()));
    addSchema(DMN14_NS, createSchema(DMN_14_SCHEMA_LOCATION, DmnParser.class.getClassLoader()));
    addSchema(DMN13_NS, createSchema(DMN_13_SCHEMA_LOCATION, DmnParser.class.getClassLoader()));
    addSchema(DMN12_NS, createSchema(DMN_12_SCHEMA_LOCATION, DmnParser.class.getClassLoader()));
    addSchema(DMN11_NS, createSchema(DMN_11_SCHEMA_LOCATION, DmnParser.class.getClassLoader()));
    addSchema(DMN11_ALTERNATIVE_NS, createSchema(DMN_11_ALTERNATIVE_SCHEMA_LOCATION, DmnParser.class.getClassLoader()));
  }
```

---

</SwmSnippet>

<SwmSnippet path="/model-api/dmn-model/src/main/java/org/camunda/bpm/model/dmn/impl/DmnModelConstants.java" line="19">

---

# DMN Model Constants

The `DmnModelConstants` class defines constants that are used throughout the DMN Implementation. These constants include DMN namespaces, schema locations, and DMN element names. They are used in various parts of the codebase to ensure consistency and readability.

```java
public final class DmnModelConstants {

  /** The DMN 1.1 namespace */
  public static final String DMN11_NS = "http://www.omg.org/spec/DMN/20151101/dmn.xsd";
  public static final String DMN12_NS = "http://www.omg.org/spec/DMN/20180521/MODEL/";
  public static final String DMN13_NS = "https://www.omg.org/spec/DMN/20191111/MODEL/";
  public static final String DMN14_NS = "https://www.omg.org/spec/DMN/20211108/MODEL/";
  public static final String DMN15_NS = "https://www.omg.org/spec/DMN/20230324/MODEL/";
  public static final String LATEST_DMN_NS = DMN13_NS;

  /**
   * The DMN 1.1 namespace URL release with Camunda 7.4.0
   */
  public static final String DMN11_ALTERNATIVE_NS = "http://www.omg.org/spec/DMN/20151101/dmn11.xsd";

  /**
   * The DMN 1.3 namespace URL release with Camunda 7.13.0
   */
  public static final String DMN13_ALTERNATIVE_NS = "https://www.omg.org/spec/DMN/20191111/DMN13.xsd";

  /** The location of the DMN 1.1 XML schema. */
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
