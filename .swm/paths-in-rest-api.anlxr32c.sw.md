---
title: Paths in REST API
---
This document will cover the concept of Paths in the context of the Camunda Platform. We'll cover:

1. The role of Paths in the codebase
2. The implementation of Paths in different directories.

# Role of Paths

In the context of the Camunda Platform, Paths are used to define the routes for the REST API. Each path corresponds to a specific endpoint of the API, and the associated `.ftl` file contains the template for the response of that endpoint.

# Implementation of Paths

Paths are implemented in various directories within the `engine-rest/engine-rest-openapi/src/main/templates/paths` directory. Each subdirectory corresponds to a different category of the API, such as `user`, `engine`, `history`, etc. Within each of these directories, there are further `.ftl` files or subdirectories that correspond to specific operations or endpoints.

<SwmSnippet path="/engine-rest/engine-rest-openapi/src/main/templates/paths/user/get.ftl" line="1">

---

## Example: User Paths

This is an example of a User Path. The `get.ftl` file defines the response for the GET request to the user endpoint.

```ftl
<#macro endpoint_macro docsUrl="">
{

  <@lib.endpointInfo
      id = "getUsers"
      tag = "User"
      summary = "Get List"
      desc = "Query for a list of users using a list of parameters.
              The size of the result set can be retrieved by using the Get User Count method.
              [Get User Count](${docsUrl}/reference/rest/user/get-query-count/) method." />
```

---

</SwmSnippet>

<SwmSnippet path="/engine-rest/engine-rest-openapi/src/main/templates/paths/engine/get.ftl" line="1">

---

## Example: Engine Paths

This is an example of an Engine Path. The `get.ftl` file defines the response for the GET request to the engine endpoint.

```ftl
<#macro endpoint_macro docsUrl="">
{
  <@lib.endpointInfo
      id = "getProcessEngineNames"
      tag = "Engine"
      summary = "Get List"
      desc = "Retrieves the names of all process engines available on your platform.
              **Note**: You cannot prepend `/engine/{name}` to this method." />

  "responses" : {
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
