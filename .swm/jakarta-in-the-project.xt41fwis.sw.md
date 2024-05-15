---
title: Jakarta in the Project
---
This document will cover the following aspects of Jakarta in the context of the DEMO-camunda-bpm-platform project:

1. The role of Jakarta in the project.
2. Where Jakarta is implemented in the codebase.

# Role of Jakarta

Jakarta, specifically the `jakarta.jakartaee-bom` artifact in the `jakarta.platform` group, is a key dependency in the `engine-rest-jakarta` module of the project. It provides the necessary libraries and specifications for the Jakarta EE platform, which is a set of specifications that enable development of enterprise applications.

<SwmSnippet path="/engine-rest/engine-rest-jakarta/pom.xml" line="143">

---

# Implementation of Jakarta

The `jakarta.jakartaee-bom` artifact is declared as a dependency in the `pom.xml` file of the `engine-rest-jakarta` module. The version of the Jakarta EE specifications used is determined by the `${version.jakarta-ee-spec}` property.

```xml
    <dependency>
      <groupId>jakarta.platform</groupId>
      <artifactId>jakarta.jakartaee-bom</artifactId>
      <version>${version.jakarta-ee-spec}</version>
      <type>pom</type>
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
