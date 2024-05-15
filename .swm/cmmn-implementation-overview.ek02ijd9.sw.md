---
title: CMMN Implementation Overview
---
This document will cover the implementation of CMMN (Case Management Model and Notation) in the DEMO-camunda-bpm-platform repository. We'll cover:

1. The role of the CMMN_ATTRIBUTE_IMPLEMENTATION_TYPE constant
2. The use of CMMN_ATTRIBUTE_IMPLEMENTATION_TYPE in various classes
3. The role of the CmmnModelConstants class
4. The use of CmmnModelConstants in various classes
5. The role and usage of various classes like TaskImpl, StageImpl, PlanItemImpl, CaseImpl, HumanTaskImpl, ExpressionImpl, and Cmmn.

<SwmSnippet path="/model-api/cmmn-model/src/main/java/org/camunda/bpm/model/cmmn/impl/CmmnModelConstants.java" line="212">

---

# CMMN_ATTRIBUTE_IMPLEMENTATION_TYPE

`CMMN_ATTRIBUTE_IMPLEMENTATION_TYPE` is a constant defined in the `CmmnModelConstants` class. It represents the attribute 'implementationType' in the CMMN model.

```java
  public static final String CMMN_ATTRIBUTE_IMPLEMENTATION_TYPE = "implementationType";
```

---

</SwmSnippet>

<SwmSnippet path="/model-api/cmmn-model/src/main/java/org/camunda/bpm/model/cmmn/impl/CmmnModelConstants.java" line="23">

---

# CmmnModelConstants

`CmmnModelConstants` is a class that contains constants for various elements and attributes in the CMMN model. It includes namespaces, schema locations, and attribute names.

```java
public class CmmnModelConstants {

  /** The CMMN 1.0 namespace */
  public static final String CMMN10_NS = "http://www.omg.org/spec/CMMN/20131201/MODEL";

  /** The CMMN 1.1 namespace */
  public static final String CMMN11_NS = "http://www.omg.org/spec/CMMN/20151109/MODEL";

  /** The location of the CMMN 1.0 XML schema. */
  public static final String CMMN_10_SCHEMA_LOCATION = "org/camunda/bpm/model/cmmn/schema/cmmn10/CMMN10.xsd";

  /** The location of the CMMN 1.1 XML schema. */
  public static final String CMMN_11_SCHEMA_LOCATION = "org/camunda/bpm/model/cmmn/schema/cmmn11/CMMN11.xsd";

  /** Xml Schema is the default type language */
  public static final String XML_SCHEMA_NS = "http://www.w3.org/2001/XMLSchema";

  public static final String XPATH_NS = "http://www.w3.org/1999/XPath";

  /** Camunda namespace */
  public static final String CAMUNDA_NS = "http://camunda.org/schema/1.0/cmmn";
```

---

</SwmSnippet>

<SwmSnippet path="/model-api/cmmn-model/src/main/java/org/camunda/bpm/model/cmmn/impl/instance/TaskImpl.java" line="43">

---

# TaskImpl

`TaskImpl` is a class that represents a task in the CMMN model. It extends `PlanItemDefinitionImpl` and implements `Task`. It defines attributes and child elements specific to a task.

```java
public class TaskImpl extends PlanItemDefinitionImpl implements Task {

  protected static Attribute<Boolean> isBlockingAttribute;

  // cmmn 1.0
  @Deprecated
  protected static ChildElementCollection<InputsCaseParameter> inputsCollection;
  @Deprecated
  protected static ChildElementCollection<OutputsCaseParameter> outputsCollection;

  // cmmn 1.1
  protected static ChildElementCollection<InputCaseParameter> inputParameterCollection;
  protected static ChildElementCollection<OutputCaseParameter> outputParameterCollection;

  public TaskImpl(ModelTypeInstanceContext instanceContext) {
    super(instanceContext);
  }

  public boolean isBlocking() {
    return isBlockingAttribute.getValue(this);
  }
```

---

</SwmSnippet>

<SwmSnippet path="/model-api/cmmn-model/src/main/java/org/camunda/bpm/model/cmmn/impl/instance/StageImpl.java" line="50">

---

# StageImpl

`StageImpl` is a class that represents a stage in the CMMN model. It extends `PlanFragmentImpl` and implements `Stage`. It defines attributes and child elements specific to a stage.

```java
public class StageImpl extends PlanFragmentImpl implements Stage {

  protected static Attribute<Boolean> autoCompleteAttribute;
  protected static ChildElement<PlanningTable> planningTableChild;
  protected static ChildElementCollection<PlanItemDefinition> planItemDefinitionCollection;

  // cmmn 1.0
  @Deprecated
  protected static AttributeReferenceCollection<Sentry> exitCriteriaRefCollection;

  // cmmn 1.1
  protected static ChildElementCollection<ExitCriterion> exitCriterionCollection;

  public StageImpl(ModelTypeInstanceContext instanceContext) {
    super(instanceContext);
  }

  public boolean isAutoComplete() {
    return autoCompleteAttribute.getValue(this);
  }

```

---

</SwmSnippet>

<SwmSnippet path="/model-api/cmmn-model/src/main/java/org/camunda/bpm/model/cmmn/impl/instance/PlanItemImpl.java" line="54">

---

# PlanItemImpl

`PlanItemImpl` is a class that represents a plan item in the CMMN model. It extends `CmmnElementImpl` and implements `PlanItem`. It defines attributes and child elements specific to a plan item.

```java
public class PlanItemImpl extends CmmnElementImpl implements PlanItem {

  protected static Attribute<String> nameAttribute;
  protected static AttributeReference<PlanItemDefinition> planItemDefinitionRefAttribute;
  protected static ChildElement<ItemControl> itemControlChild;

  // cmmn 1.0
  @Deprecated
  protected static AttributeReferenceCollection<Sentry> entryCriteriaRefCollection;
  @Deprecated
  protected static AttributeReferenceCollection<Sentry> exitCriteriaRefCollection;

  // cmmn 1.1
  protected static ChildElementCollection<EntryCriterion> entryCriterionCollection;
  protected static ChildElementCollection<ExitCriterion> exitCriterionCollection;

  public PlanItemImpl(ModelTypeInstanceContext instanceContext) {
    super(instanceContext);
  }

  public String getName() {
```

---

</SwmSnippet>

<SwmSnippet path="/model-api/cmmn-model/src/main/java/org/camunda/bpm/model/cmmn/impl/instance/CaseImpl.java" line="44">

---

# CaseImpl

`CaseImpl` is a class that represents a case in the CMMN model. It extends `CmmnElementImpl` and implements `Case`. It defines attributes and child elements specific to a case.

```java
public class CaseImpl extends CmmnElementImpl implements Case {

  protected static Attribute<String> nameAttribute;
  protected static Attribute<String> camundaHistoryTimeToLive;

  protected static ChildElement<CaseFileModel> caseFileModelChild;
  protected static ChildElement<CasePlanModel> casePlanModelChild;
  protected static ChildElementCollection<InputCaseParameter> inputCollection;
  protected static ChildElementCollection<OutputCaseParameter> outputCollection;

  // cmmn 1.0
  @Deprecated
  protected static ChildElementCollection<CaseRole> caseRolesCollection;

  // cmmn 1.1
  protected static ChildElement<CaseRoles> caseRolesChild;

  public CaseImpl(ModelTypeInstanceContext instanceContext) {
    super(instanceContext);
  }

```

---

</SwmSnippet>

<SwmSnippet path="/model-api/cmmn-model/src/main/java/org/camunda/bpm/model/cmmn/impl/instance/HumanTaskImpl.java" line="53">

---

# HumanTaskImpl

`HumanTaskImpl` is a class that represents a human task in the CMMN model. It extends `TaskImpl` and implements `HumanTask`. It defines attributes and child elements specific to a human task.

```java
public class HumanTaskImpl extends TaskImpl implements HumanTask {

  protected static AttributeReference<Role> performerRefAttribute;

  // cmmn 1.0
  @Deprecated
  protected static ChildElementCollection<PlanningTable> planningTableCollection;

  // cmmn 1.1
  protected static ChildElement<PlanningTable> planningTableChild;

  /** camunda extensions */
  protected static Attribute<String> camundaAssigneeAttribute;
  protected static Attribute<String> camundaCandidateGroupsAttribute;
  protected static Attribute<String> camundaCandidateUsersAttribute;
  protected static Attribute<String> camundaDueDateAttribute;
  protected static Attribute<String> camundaFollowUpDateAttribute;
  protected static Attribute<String> camundaFormKeyAttribute;
  protected static Attribute<String> camundaPriorityAttribute;

  public HumanTaskImpl(ModelTypeInstanceContext instanceContext) {
```

---

</SwmSnippet>

<SwmSnippet path="/model-api/cmmn-model/src/main/java/org/camunda/bpm/model/cmmn/impl/instance/ExpressionImpl.java" line="38">

---

# ExpressionImpl

`ExpressionImpl` is a class that represents an expression in the CMMN model. It extends `CmmnElementImpl` and implements `Expression`. It defines attributes and child elements specific to an expression.

```java
public class ExpressionImpl extends CmmnElementImpl implements Expression {

  protected static Attribute<String> languageAttribute;

  // cmmn 1.0
  @Deprecated
  protected static ChildElement<Body> bodyChild;

  public ExpressionImpl(ModelTypeInstanceContext instanceContext) {
    super(instanceContext);
  }

  public String getText() {
    if (isCmmn11()) {
      return getTextContent();
    }
    else {
      return getBody();
    }
  }

```

---

</SwmSnippet>

<SwmSnippet path="/model-api/cmmn-model/src/main/java/org/camunda/bpm/model/cmmn/Cmmn.java" line="139">

---

# Cmmn

`Cmmn` is a class that provides methods for reading, writing, and validating CMMN model instances. It also registers known types of the CMMN model.

```java
public class Cmmn {

  /** the singleton instance of {@link Cmmn}. If you want to customize the behavior of Cmmn,
   * replace this instance with an instance of a custom subclass of {@link Cmmn}. */
  public static Cmmn INSTANCE = new Cmmn();

  /** the parser used by the Cmmn implementation. */
  private CmmnParser cmmnParser = new CmmnParser();
  private final ModelBuilder cmmnModelBuilder;

  /** The {@link Model}
   */
  private Model cmmnModel;

  /**
   * Allows reading a {@link CmmnModelInstance} from a File.
   *
   * @param file the {@link File} to read the {@link CmmnModelInstance} from
   * @return the model read
   * @throws CmmnModelException if the model cannot be read
   */
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
