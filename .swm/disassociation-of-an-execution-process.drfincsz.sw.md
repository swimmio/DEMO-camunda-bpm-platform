---
title: Disassociation of an Execution Process
---
This document will cover the process of disassociating an execution in the Camunda BPM platform. The steps include:

1. Initiating the disassociation
2. Setting the execution
3. Getting the execution
4. Getting the scoped association
5. Determining the broadest active context
6. Getting available scoped association classes.

```mermaid
graph TD;
  disAssociate::engine-cdi/core/src/main/java/org/camunda/bpm/engine/cdi/impl/context/DefaultContextAssociationManager.java:::mainFlowStyle --> setExecution::engine-cdi/core/src/main/java/org/camunda/bpm/engine/cdi/impl/context/DefaultContextAssociationManager.java
  disAssociate::engine-cdi/core/src/main/java/org/camunda/bpm/engine/cdi/impl/context/DefaultContextAssociationManager.java:::mainFlowStyle --> absc8[...]
  setExecution::engine-cdi/core/src/main/java/org/camunda/bpm/engine/cdi/impl/context/DefaultContextAssociationManager.java:::mainFlowStyle --> getExecution::engine-cdi/core/src/main/java/org/camunda/bpm/engine/cdi/impl/context/DefaultContextAssociationManager.java
  setExecution::engine-cdi/core/src/main/java/org/camunda/bpm/engine/cdi/impl/context/DefaultContextAssociationManager.java:::mainFlowStyle --> nvwz6[...]
  getExecution::engine-cdi/core/src/main/java/org/camunda/bpm/engine/cdi/impl/context/DefaultContextAssociationManager.java:::mainFlowStyle --> getScopedAssociation::engine-cdi/core/src/main/java/org/camunda/bpm/engine/cdi/impl/context/DefaultContextAssociationManager.java
  getExecution::engine-cdi/core/src/main/java/org/camunda/bpm/engine/cdi/impl/context/DefaultContextAssociationManager.java:::mainFlowStyle --> fyxh3[...]
  getScopedAssociation::engine-cdi/core/src/main/java/org/camunda/bpm/engine/cdi/impl/context/DefaultContextAssociationManager.java:::mainFlowStyle --> getBroadestActiveContext::engine-cdi/core/src/main/java/org/camunda/bpm/engine/cdi/impl/context/DefaultContextAssociationManager.java
  getScopedAssociation::engine-cdi/core/src/main/java/org/camunda/bpm/engine/cdi/impl/context/DefaultContextAssociationManager.java:::mainFlowStyle --> p62xx[...]
  getBroadestActiveContext::engine-cdi/core/src/main/java/org/camunda/bpm/engine/cdi/impl/context/DefaultContextAssociationManager.java:::mainFlowStyle --> getAvailableScopedAssociationClasses::engine-cdi/core/src/main/java/org/camunda/bpm/engine/cdi/impl/context/DefaultContextAssociationManager.java
  getBroadestActiveContext::engine-cdi/core/src/main/java/org/camunda/bpm/engine/cdi/impl/context/DefaultContextAssociationManager.java:::mainFlowStyle --> 76uz0[...]
  getAvailableScopedAssociationClasses::engine-cdi/core/src/main/java/org/camunda/bpm/engine/cdi/impl/context/DefaultContextAssociationManager.java:::mainFlowStyle --> add::webapps/frontend/camunda-commons-ui/lib/util/notifications.js
  add::webapps/frontend/camunda-commons-ui/lib/util/notifications.js:::mainFlowStyle --> ...

 classDef mainFlowStyle color:#000000,fill:#7CB9F4
```

<SwmSnippet path="/engine-cdi/core/src/main/java/org/camunda/bpm/engine/cdi/impl/context/DefaultContextAssociationManager.java" line="98">

---

# Initiating the disassociation

The `disAssociate` function initiates the disassociation process. It calls the `setExecution` function to set the execution that will be disassociated.

```java
  @Override
  public void setExecution(Execution execution) {
    if(execution == null) {
      throw new ProcessEngineCdiException("Cannot associate with execution: null");
    }
    ensureCommandContextNotActive();

    ScopedAssociation scopedAssociation = getScopedAssociation();
    Execution associatedExecution = scopedAssociation.getExecution();
    if(associatedExecution!=null && !associatedExecution.getId().equals(execution.getId())) {
      throw new ProcessEngineCdiException("Cannot associate "+execution+", already associated with "+associatedExecution+". Disassociate first!");
    }

    if (log.isLoggable(Level.FINE)) {
      log.fine("Associating "+execution+" (@"
                + scopedAssociation.getClass().getAnnotations()[0].annotationType().getSimpleName() + ")");
    }
    scopedAssociation.setExecution(execution);
  }
```

---

</SwmSnippet>

<SwmSnippet path="/engine-cdi/core/src/main/java/org/camunda/bpm/engine/cdi/impl/context/DefaultContextAssociationManager.java" line="98">

---

# Setting the execution

The `setExecution` function sets the execution that will be disassociated. It checks if the execution is null and if the command context is active. It then gets the scoped association and checks if an execution is already associated. If an execution is already associated, it throws an exception. Otherwise, it associates the execution.

```java
  @Override
  public void setExecution(Execution execution) {
    if(execution == null) {
      throw new ProcessEngineCdiException("Cannot associate with execution: null");
    }
    ensureCommandContextNotActive();

    ScopedAssociation scopedAssociation = getScopedAssociation();
    Execution associatedExecution = scopedAssociation.getExecution();
    if(associatedExecution!=null && !associatedExecution.getId().equals(execution.getId())) {
      throw new ProcessEngineCdiException("Cannot associate "+execution+", already associated with "+associatedExecution+". Disassociate first!");
    }

    if (log.isLoggable(Level.FINE)) {
      log.fine("Associating "+execution+" (@"
                + scopedAssociation.getClass().getAnnotations()[0].annotationType().getSimpleName() + ")");
    }
    scopedAssociation.setExecution(execution);
  }
```

---

</SwmSnippet>

<SwmSnippet path="/engine-cdi/core/src/main/java/org/camunda/bpm/engine/cdi/impl/context/DefaultContextAssociationManager.java" line="144">

---

# Getting the execution

The `getExecution` function retrieves the execution from the context. If the execution is not null, it returns the execution. Otherwise, it gets the execution from the scoped association.

```java
  @Override
  public Execution getExecution() {
    ExecutionEntity execution = getExecutionFromContext();
    if(execution != null) {
      return execution;
    } else {
      return getScopedAssociation().getExecution();
    }
  }
```

---

</SwmSnippet>

<SwmSnippet path="/engine-cdi/core/src/main/java/org/camunda/bpm/engine/cdi/impl/context/DefaultContextAssociationManager.java" line="94">

---

# Getting the scoped association

The `getScopedAssociation` function retrieves the scoped association by looking up the broadest active context.

```java
  protected ScopedAssociation getScopedAssociation() {
    return ProgrammaticBeanLookup.lookup(getBroadestActiveContext(), beanManager);
  }
```

---

</SwmSnippet>

<SwmSnippet path="/engine-cdi/core/src/main/java/org/camunda/bpm/engine/cdi/impl/context/DefaultContextAssociationManager.java" line="64">

---

# Determining the broadest active context

The `getBroadestActiveContext` function determines the broadest active context by iterating over the available scoped association classes. It checks if the context is active and returns the scope type if it is. If no active context is found, it throws an exception.

```java
  protected Class< ? extends ScopedAssociation> getBroadestActiveContext() {
    for (Class< ? extends ScopedAssociation> scopeType : getAvailableScopedAssociationClasses()) {
      Annotation scopeAnnotation = scopeType.getAnnotations().length > 0 ? scopeType.getAnnotations()[0] : null;
      if (scopeAnnotation == null || !beanManager.isScope(scopeAnnotation.annotationType())) {
        throw new ProcessEngineException("ScopedAssociation must carry exactly one annotation and it must be a @Scope annotation");
      }
      try {
        beanManager.getContext(scopeAnnotation.annotationType());
        return scopeType;
      } catch (ContextNotActiveException e) {
        log.finest("Context " + scopeAnnotation.annotationType() + " not active.");
      }
    }
    throw new ProcessEngineException("Could not determine an active context to associate the current process instance / task instance with.");
  }
```

---

</SwmSnippet>

<SwmSnippet path="/engine-cdi/core/src/main/java/org/camunda/bpm/engine/cdi/impl/context/DefaultContextAssociationManager.java" line="80">

---

# Getting available scoped association classes

The `getAvailableScopedAssociationClasses` function returns a list of available scoped association classes. It adds the `ConversationScopedAssociation` class and the `RequestScopedAssociation` class to the list.

```java
  /**
   * Override to add different / additional contexts.
   *
   * @returns a list of {@link Scope}-types, which are used in the given order
   *          to resolve the broadest active context (@link
   *          #getBroadestActiveContext()})
   */
  protected List<Class< ? extends ScopedAssociation>> getAvailableScopedAssociationClasses() {
    ArrayList<Class< ? extends ScopedAssociation>> scopeTypes = new ArrayList<Class< ? extends ScopedAssociation>>();
    scopeTypes.add(ConversationScopedAssociation.class);
    scopeTypes.add(RequestScopedAssociation.class);
    return scopeTypes;
  }
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
