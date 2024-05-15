---
title: Process Engine Overview
---
This document will cover the functionality and usage of the Process Engine in the Camunda BPM platform. We'll cover:

1. The role of the Process Engine
2. How the Process Engine is implemented in the codebase.

# Role of the Process Engine

The Process Engine in Camunda is a core component responsible for executing BPMN 2.0 processes. It provides a set of services that are used to manage and control process execution.

<SwmSnippet path="/engine-cdi/core/src/main/java/org/camunda/bpm/engine/cdi/impl/NamedProcessEngineServicesProducer.java" line="54">

---

# Process Engine Implementation

The Process Engine is implemented as a producer method that is responsible for creating and providing instances of the Process Engine. It uses the `@ProcessEngineName` annotation to determine which Process Engine to inject.

```java
  @Produces @ProcessEngineName("")
  public ProcessEngine processEngine(InjectionPoint ip) {

    ProcessEngineName annotation = ip.getAnnotated().getAnnotation(ProcessEngineName.class);
    String processEngineName = annotation.value();
    if(processEngineName == null || processEngineName.length() == 0) {
     throw new ProcessEngineException("Cannot determine which process engine to inject: @ProcessEngineName must specify the name of a process engine.");
    }
    try {
      ProcessEngineService processEngineService = BpmPlatform.getProcessEngineService();
      return processEngineService.getProcessEngine(processEngineName);
    }catch (Exception e) {
      throw new ProcessEngineException("Cannot find process engine named '"+processEngineName+"' specified using @ProcessEngineName: "+e.getMessage(), e);
    }

  }
```

---

</SwmSnippet>

<SwmSnippet path="/engine-cdi/core/src/main/java/org/camunda/bpm/engine/cdi/impl/NamedProcessEngineServicesProducer.java" line="71">

---

The Process Engine provides a set of services such as `RuntimeService`, `TaskService`, `RepositoryService`, `FormService`, `HistoryService`, `IdentityService`, `ManagementService`, `AuthorizationService`, `FilterService`, and `ExternalTaskService`. These services are produced using the `@ProcessEngineName` annotation and the `processEngine` method.

```java
  @Produces @ProcessEngineName("") public RuntimeService runtimeService(InjectionPoint ip) { return processEngine(ip).getRuntimeService(); }

  @Produces @ProcessEngineName("") public TaskService taskService(InjectionPoint ip) { return processEngine(ip).getTaskService(); }

  @Produces @ProcessEngineName("") public RepositoryService repositoryService(InjectionPoint ip) { return processEngine(ip).getRepositoryService(); }

  @Produces @ProcessEngineName("") public FormService formService(InjectionPoint ip) { return processEngine(ip).getFormService(); }

  @Produces @ProcessEngineName("") public HistoryService historyService(InjectionPoint ip) { return processEngine(ip).getHistoryService(); }

  @Produces @ProcessEngineName("") public IdentityService identityService(InjectionPoint ip) { return processEngine(ip).getIdentityService(); }

  @Produces @ProcessEngineName("") public ManagementService managementService(InjectionPoint ip) { return processEngine(ip).getManagementService(); }

  @Produces @ProcessEngineName("") public AuthorizationService authorizationService(InjectionPoint ip) { return processEngine(ip).getAuthorizationService(); }

  @Produces @ProcessEngineName("") public FilterService filterService(InjectionPoint ip) { return processEngine(ip).getFilterService(); }

  @Produces @ProcessEngineName("") public ExternalTaskService externalTaskService(InjectionPoint ip) { return processEngine(ip).getExternalTaskService(); }
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
