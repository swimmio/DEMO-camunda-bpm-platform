---
title: CDI Implementation in Camunda BPM Platform
---
This document will cover the implementation of CDI (Contexts and Dependency Injection) in the Camunda BPM platform. We'll cover:

1. The role of CDI in the platform
2. The key classes and methods involved in CDI implementation.

# Role of CDI in Camunda BPM platform

CDI (Contexts and Dependency Injection) is a standard dependency injection framework included in Java EE 6 and higher. It allows you to manage the lifecycle of stateful components via domain-specific contexts and to inject components (services, repositories, etc.) into client objects in a type-safe way. In the context of the Camunda BPM platform, CDI is used to manage and inject process-related components.

<SwmSnippet path="/engine-cdi/core/src/main/java/org/camunda/bpm/engine/cdi/impl/event/CdiEventListener.java" line="26">

---

# Key Classes and Methods in CDI Implementation

The `CdiEventListener` class is a key part of the CDI implementation. It extends `AbstractCdiEventListener` and overrides the `fireEvent` method to publish events using the CDI event infrastructure. The `getBeanManager` method is used to retrieve the CDI BeanManager.

```java
/**
 * Generic {@link ExecutionListener} publishing events using the CDI event
 * infrastructure.
 *
 * @author Daniel Meyer
 */
public class CdiEventListener extends AbstractCdiEventListener {

  private static final long serialVersionUID = 1L;

  @Override
  protected void fireEvent(BusinessProcessEvent event, Annotation[] qualifiers) {
    getBeanManager().fireEvent(event, qualifiers);
  }

  protected BeanManager getBeanManager() {
    BeanManager bm = BeanManagerLookup.getBeanManager();
    if (bm == null) {
      throw new ProcessEngineException("No cdi bean manager available, cannot publish event.");
    }
    return bm;
```

---

</SwmSnippet>

<SwmSnippet path="/engine-cdi/core/src/main/java/org/camunda/bpm/engine/cdi/impl/CdiProcessApplicationElResolver.java" line="30">

---

The `CdiProcessApplicationElResolver` class is another important part of the CDI implementation. It implements the `ProcessApplicationElResolver` interface and provides methods like `getPrecedence` and `getElResolver` for resolving expressions in the context of a process application.

```java
public class CdiProcessApplicationElResolver implements ProcessApplicationElResolver {

  @Override
  public Integer getPrecedence() {
    return ProcessApplicationElResolver.CDI_RESOLVER;
  }

  @Override
  public ELResolver getElResolver(AbstractProcessApplication processApplication) {
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
