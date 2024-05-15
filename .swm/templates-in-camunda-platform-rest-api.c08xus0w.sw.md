---
title: Templates in Camunda Platform REST API
---
This document will cover the role and usage of Templates in the DEMO-camunda-bpm-platform project. We'll cover:

1. The role of Templates in the project
2. The implementation of Templates in different parts of the codebase.

# Role of Templates

In the context of the DEMO-camunda-bpm-platform project, Templates are used to generate parts of the REST API documentation. They are written in FreeMarker, a template engine that provides a simple and flexible way to generate text output based on data and templates. The Templates in this project are used to generate the OpenAPI specification for the Camunda Platform REST API.

<SwmSnippet path="/engine-rest/engine-rest-openapi/src/main/templates/main.ftl" line="1">

---

# Implementation of Templates

This is the main template file (`main.ftl`). It imports utility functions from `utils.ftl` and defines the structure of the OpenAPI specification. It uses other templates from the `paths` and `models` directories to generate the specification for each endpoint and data model.

```ftl
<#import "/lib/utils.ftl" as lib>

<#assign docsUrl = "https://docs.camunda.org/manual/${docsVersion}">
{
  "openapi": "3.0.2",
  "info": {
    "title": "Camunda Platform REST API",
    "description": "OpenApi Spec for Camunda Platform REST API.",
    "version": "${cambpmVersion}",
    "license": {
      "name": "Apache License 2.0",
      "url": "http://www.apache.org/licenses/LICENSE-2.0.html"
    }
  },
  "externalDocs": {
    "description": "Find out more about Camunda Rest API",
    "url": "${docsUrl}/reference/rest/overview/"
  },
  "servers": [

  <@lib.server
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
