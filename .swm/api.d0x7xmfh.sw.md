---
title: API
---
This document will cover the usage of the Camunda Platform REST API, including:

1. An overview of what the API offers
2. Details on where to find the list of endpoints
3. How to use the API via Swagger and Postman

<SwmSnippet path="/engine-rest/engine-rest-openapi/src/main/templates/main.ftl" line="6">

---

# Overview of the API

The Camunda Platform REST API is defined in this file. It provides a wide range of functionalities, including process engine operations, task management, and more. The API is described using the OpenAPI specification, and its documentation can be found at the URL specified in the `externalDocs` field.

```ftl
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
```

---

</SwmSnippet>

<SwmSnippet path="/engine-rest/engine-rest-openapi/src/main/templates/main.ftl" line="91">

---

# List of Endpoints

The list of available endpoints is defined in the `paths` field. Each endpoint corresponds to a specific functionality provided by the API.

```ftl
  "paths": {

    <#list endpoints as path, methods>
        "${path}": {
            <#list methods as method>
                <#import "/paths${path}/${method}.ftl" as endpoint>
                "${method}":
                <@endpoint.endpoint_macro docsUrl=docsUrl/><#sep>,
            </#list>
        }<#sep>,
    </#list>

  },
```

---

</SwmSnippet>

<SwmSnippet path="/engine-rest/engine-rest-openapi/src/main/templates/main.ftl" line="3">

---

# Using the API via Swagger

The API is available via Swagger. The specification path is defined in this file, which is used to generate the OpenAPI specification.

```ftl
<#assign docsUrl = "https://docs.camunda.org/manual/${docsVersion}">
{
```

---

</SwmSnippet>

# Using the API via Postman

The API is also available via Postman. However, the collection is not explicitly defined in the codebase. It can be generated from the OpenAPI specification using Postman's import feature.

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
