---
title: Role of OpenAPI in API Documentation
---
This document will cover the process of supporting the documentation of APIs with OpenAPI in the DEMO-camunda-bpm-platform repo. The main points covered are:

1. How OpenAPI documentation is generated.
2. The structure and organization of the OpenAPI documentation.
3. The review process for changes in the OpenAPI documentation.

# OpenAPI Documentation Generation

The DEMO-camunda-bpm-platform repo uses a project that generates a single `openapi.json` file containing the OpenAPI documentation of the Engine Rest API. This is aligned with the OpenAPI specification version 3.0.2.

# Structure and Organization of OpenAPI Documentation

The OpenAPI documentation is organized into endpoints definitions of the Rest API. Each resource has its own folder under `/paths` (e.g. `/process-instance`, `/deployment`). The path of the endpoint is resolved to a folder structure. The endpoints' paths are automatically resolved from the folder structure. Dynamic endpoints are structured with brakes like `process-instance/{id}/variables/{varName}/data`, then the path parameters (`id` and `varName`) should always be included in the endpoint definition and marked as `required`.

# Review Process for OpenAPI Documentation

When changes are made to the macros, it's important to compare the last build `openapi.json` version with the one to review to ensure that the endpoints are complete after the new changes. The path of the endpoints should be double-checked as they are not easy to see if they are not checked additionally. It's also crucial to check for correct parameters, requests, and responses, and for compliance with the Java endpoints.

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
