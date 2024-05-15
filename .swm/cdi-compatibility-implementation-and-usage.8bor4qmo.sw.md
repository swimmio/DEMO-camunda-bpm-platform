---
title: CDI Compatibility Implementation and Usage
---
This document will cover the topic of CDI Compatibility in the Camunda BPM platform. We'll cover:

1. The implementation of CDI Compatibility
2. The usage of CDI Compatibility in the codebase.

<SwmSnippet path="/engine-cdi/core/src/main/java/org/camunda/bpm/engine/cdi/compat/FoxTaskForm.java" line="17">

---

# Implementation of CDI Compatibility

The `FoxTaskForm` class is an example of CDI Compatibility implementation. It extends `TaskForm` and is annotated with `@ConversationScoped`, `@Named("fox.taskForm")`, and `@Typed({FoxTaskForm.class})`.

```java
package org.camunda.bpm.engine.cdi.compat;

import javax.enterprise.context.ConversationScoped;
import javax.enterprise.inject.Typed;
import javax.inject.Named;

import org.camunda.bpm.engine.cdi.jsf.TaskForm;

@ConversationScoped
@Named("fox.taskForm")
@Typed({FoxTaskForm.class})
public class FoxTaskForm extends TaskForm {

  private static final long serialVersionUID = 9042602064970870095L;
}
```

---

</SwmSnippet>

<SwmSnippet path="/engine-cdi/core/src/main/java/org/camunda/bpm/engine/cdi/compat/CamundaTaskForm.java" line="17">

---

# Usage of CDI Compatibility

The `CamundaTaskForm` class is another example of CDI Compatibility usage. Similar to `FoxTaskForm`, it extends `TaskForm` and is annotated with `@ConversationScoped`, `@Named("camunda.taskForm")`, and `@Typed({CamundaTaskForm.class})`.

```java
package org.camunda.bpm.engine.cdi.compat;

import javax.enterprise.context.ConversationScoped;
import javax.enterprise.inject.Typed;
import javax.inject.Named;

import org.camunda.bpm.engine.cdi.jsf.TaskForm;

@ConversationScoped
@Named("camunda.taskForm")
@Typed({CamundaTaskForm.class})
public class CamundaTaskForm extends TaskForm {

  private static final long serialVersionUID = 9042602064970870095L;
}
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
