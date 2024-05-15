---
title: Overview of the Main Directory in the Camunda BPM Platform
---
This document will cover the following aspects of 'Main' in the context of the DEMO-camunda-bpm-platform repo:

1. The role and functionality of 'Main' in the codebase.
2. The places where 'Main' is implemented and used.

# Role and Functionality of Main

In the context of this codebase, 'Main' refers to the main directory of the engine-rest module. This directory contains the primary Java classes and resources that are integral to the operation of the Camunda BPM platform. The classes in this directory define the REST API endpoints and services, and implement the core functionalities of the platform.

<SwmSnippet path="/engine-rest/engine-rest/src/main/java/org/camunda/bpm/engine/rest/impl/DefaultProcessEngineRestServiceImpl.java" line="57">

---

# Implementation and Usage of Main

The 'Main' directory contains the 'DefaultProcessEngineRestServiceImpl' class, which is a central part of the Camunda BPM platform. This class defines the REST API endpoints for various services such as process definition, task management, identity, execution, and more. Each service is implemented as a method in this class.

```java
@Path(DefaultProcessEngineRestServiceImpl.PATH)
public class DefaultProcessEngineRestServiceImpl extends AbstractProcessEngineRestServiceImpl {

  public static final String PATH = "";

  @Path(ProcessDefinitionRestService.PATH)
  public ProcessDefinitionRestService getProcessDefinitionService() {
    return super.getProcessDefinitionService(null);
  }

  @Path(ProcessInstanceRestService.PATH)
  public ProcessInstanceRestService getProcessInstanceService() {
    return super.getProcessInstanceService(null);
  }

  @Path(ExecutionRestService.PATH)
  public ExecutionRestService getExecutionService() {
    return super.getExecutionService(null);
  }

  @Path(TaskRestService.PATH)
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
