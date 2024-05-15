---
title: OpenAPI in Camunda BPM Platform
---
This document will cover the implementation and usage of OpenAPI in the Camunda BPM platform. We'll cover:

1. The role of OpenAPI in the project
2. Locations where OpenAPI is implemented
3. How OpenAPI is used in the codebase.

# Role of OpenAPI

OpenAPI is used in the Camunda BPM platform to define and document RESTful APIs. It provides a standard, language-agnostic interface to RESTful APIs, allowing both humans and computers to understand the service without access to source code, documentation, or network traffic inspection.

# OpenAPI Implementation Locations

OpenAPI is implemented in the `engine-rest/engine-rest-openapi` directory. This directory contains the OpenAPI schema (`schema.json`), templates for various paths (`src/main/templates/paths/`), and tests (`src/test/java/org/camunda/bpm/engine/rest/openapi`).

<SwmSnippet path="/engine-rest/engine-rest-openapi/pom.xml" line="14">

---

# OpenAPI Usage in the Codebase

The `pom.xml` file in the `engine-rest/engine-rest-openapi` directory specifies properties related to OpenAPI. The `openapi.generator.version` property specifies the version of the OpenAPI generator used, and the `generated-file` property specifies the name of the generated OpenAPI file (`openapi.json`). These properties are used during the generation of the OpenAPI client.

```xml
  <properties>
    <generated-directory>${project.build.directory}/generated-sources/openapi-json</generated-directory>
    <generated-file>openapi.json</generated-file>

    <openapi.generator.version>4.2.3</openapi.generator.version>
    <!-- properties versions used by the openapi client -->
    <!-- update them during openapi.generator version update  -->
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
