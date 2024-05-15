---
title: CmmnModelElementInstanceImpl
---
This document will cover the `CmmnModelElementInstanceImpl` class. We'll cover:

1. What `CmmnModelElementInstanceImpl` is and its purpose.
2. The variables and functions defined in `CmmnModelElementInstanceImpl`.
3. An example of how to use `CmmnModelElementInstanceImpl` in `CamundaInImpl`.

```mermaid
graph TD;
 CmmnModelElementInstance --> CmmnModelElementInstanceImpl:::currentBaseStyle
CmmnModelElementInstanceImpl --> CmmnElementImpl
CmmnElementImpl --> ArtifactImpl
ArtifactImpl --> 1[...]
CmmnElementImpl --> OnPartImpl
OnPartImpl --> 2[...]
CmmnElementImpl --> PlanItemControlImpl
PlanItemControlImpl --> 3[...]
CmmnElementImpl --> 4[...]
CmmnModelElementInstanceImpl --> DefinitionsImpl
CmmnModelElementInstanceImpl --> ExtensionElementsImpl
CmmnModelElementInstanceImpl --> 5[...]

 classDef currentBaseStyle color:#000000,fill:#7CB9F4
```

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
