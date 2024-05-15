---
title: CDI Annotations in Camunda BPM Platform
---
This document will cover the usage and implementation of CDI Annotations in the Camunda BPM platform. We'll cover:

1. What CDI Annotations are and where they are implemented.
2. How CDI Annotations are used in the codebase.

# CDI Annotations and their Implementation

CDI (Contexts and Dependency Injection) Annotations are used in the Camunda BPM platform to facilitate dependency injection and manage lifecycle contexts. They are implemented in various parts of the codebase, particularly within the `org.camunda.bpm.engine.cdi.annotation` package.

<SwmSnippet path="/engine-cdi/core/src/main/java/org/camunda/bpm/engine/cdi/annotation/TaskId.java" line="17">

---

# Usage of CDI Annotations in the Codebase

For instance, the `TaskId` annotation is a CDI Annotation used to inject the Task ID into CDI managed beans.

```java
package org.camunda.bpm.engine.cdi.annotation;

import java.lang.annotation.ElementType;
```

---

</SwmSnippet>

<SwmSnippet path="/engine-cdi/core/src/main/java/org/camunda/bpm/engine/cdi/annotation/StartProcess.java" line="17">

---

Similarly, the `StartProcess` annotation is another CDI Annotation used to start a process instance in a CDI environment.

```java
package org.camunda.bpm.engine.cdi.annotation;

import java.lang.annotation.ElementType;
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
