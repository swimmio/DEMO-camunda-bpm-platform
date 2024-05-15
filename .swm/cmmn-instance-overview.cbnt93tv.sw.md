---
title: CMMN Instance Overview
---
This document will cover the following aspects of CMMN Instance in the DEMO-camunda-bpm-platform repo:

1. The role and usage of CMMN Instance in the codebase
2. The places where CMMN Instance is implemented.

<SwmSnippet path="/model-api/cmmn-model/src/main/java/org/camunda/bpm/model/cmmn/instance/CmmnElement.java" line="21">

---

# Role and Usage of CMMN Instance

`CmmnElement` is an interface that represents a CMMN Instance. It extends `CmmnModelElementInstance` and provides methods to get and set the ID, description, documentations, and extension elements of a CMMN Instance.

```java
/**
 * @author Roman Smirnov
 *
 */
public interface CmmnElement extends CmmnModelElementInstance {

  String getId();

  void setId(String id);

  @Deprecated
  String getDescription();

  @Deprecated
  void setDescription(String description);

  Collection<Documentation> getDocumentations();

  ExtensionElements getExtensionElements();

  void setExtensionElements(ExtensionElements extensionElements);
```

---

</SwmSnippet>

<SwmSnippet path="/engine/src/main/java/org/camunda/bpm/engine/impl/cmmn/handler/ItemHandler.java" line="79">

---

# Implementation of CMMN Instance

`ItemHandler` is an abstract class that extends `CmmnElementHandler` and handles a `CmmnElement`. It provides methods to create and initialize a `CmmnActivity` from a `CmmnElement`.

```java
public abstract class ItemHandler extends CmmnElementHandler<CmmnElement, CmmnActivity> {

  public static final String PROPERTY_AUTO_COMPLETE = "autoComplete";
  public static final String PROPERTY_REQUIRED_RULE = "requiredRule";
  public static final String PROPERTY_MANUAL_ACTIVATION_RULE = "manualActivationRule";
  public static final String PROPERTY_REPETITION_RULE = "repetitionRule";
  public static final String PROPERTY_IS_BLOCKING = "isBlocking";
  public static final String PROPERTY_DISCRETIONARY = "discretionary";
  public static final String PROPERTY_ACTIVITY_TYPE = "activityType";
  public static final String PROPERTY_ACTIVITY_DESCRIPTION = "description";

  protected static final String PARENT_COMPLETE = "parentComplete";

  public static List<String> TASK_OR_STAGE_CREATE_EVENTS = Arrays.asList(
      CaseExecutionListener.CREATE
    );

  public static List<String> TASK_OR_STAGE_UPDATE_EVENTS = Arrays.asList(
      CaseExecutionListener.ENABLE,
      CaseExecutionListener.DISABLE,
      CaseExecutionListener.RE_ENABLE,
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
