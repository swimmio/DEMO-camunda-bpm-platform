---
title: BPMN Instance in Codebase
---
This document will cover the functionality and usage of BPMN Instance in the DEMO-camunda-bpm-platform codebase. We'll cover:

1. The role of BPMN Instance in the codebase
2. Where BPMN Instance is implemented

# Role of BPMN Instance

BPMN Instance in the DEMO-camunda-bpm-platform codebase is a crucial part of the BPMN model. It represents an instance of a BPMN model element, which could be any element defined in the BPMN 2.0 specification. This includes tasks, events, gateways, and so on. The BPMN Instance provides a way to interact with these elements programmatically, allowing for manipulation and inspection of BPMN processes.

<SwmSnippet path="/model-api/bpmn-model/src/main/java/org/camunda/bpm/model/bpmn/instance/BpmnModelElementInstance.java" line="17">

---

# Implementation of BPMN Instance

The `BpmnModelElementInstance` is a key part of the BPMN Instance implementation. It provides the base for all BPMN elements in the model.

```java
package org.camunda.bpm.model.bpmn.instance;

import org.camunda.bpm.model.bpmn.builder.AbstractBaseElementBuilder;
```

---

</SwmSnippet>

<SwmSnippet path="/model-api/bpmn-model/src/main/java/org/camunda/bpm/model/bpmn/instance/Task.java" line="17">

---

The `Task` class is an example of a BPMN Instance. It represents a task element in a BPMN process.

```java
package org.camunda.bpm.model.bpmn.instance;

import org.camunda.bpm.model.bpmn.instance.bpmndi.BpmnShape;
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
