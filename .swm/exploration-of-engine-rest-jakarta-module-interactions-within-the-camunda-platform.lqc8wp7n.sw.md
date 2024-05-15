---
title: >-
  Exploration of engine-rest-jakarta module interactions within the Camunda
  Platform
---
This document will cover the interaction between the `engine-rest-jakarta` module and other components in the Camunda Platform. We'll cover:

1. The role of the `engine-rest-jakarta` module
2. How `engine-rest-jakarta` interacts with `camunda-engine-rest-core` module
3. The interaction of `engine-rest-jakarta` with other components in the Camunda Platform.

# The role of the `engine-rest-jakarta` module

The `engine-rest-jakarta` module is a Jakarta JAX-RS-based REST API for Camunda Platform. It provides a way for other components to interact with the Camunda Platform using RESTful services.

# Interaction with `camunda-engine-rest-core` module

The `engine-rest-jakarta` module copies and transforms the `camunda-engine-rest-core` module. It contains only implementations for classes where there are breaking changes either in the updated dependencies or due to JakartaEE.

# Interaction with other components in the Camunda Platform

The `engine-rest-jakarta` module interacts with other components in the Camunda Platform such as the Camunda Engine, which is responsible for executing BPMN 2.0 processes. The REST API provided by `engine-rest-jakarta` allows remote access to these running processes. It also interacts with the Spring, CDI Integration, which allows developers to write Java Applications that interact with running processes.

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
