---
title: Task Assignment and Display Handling in Tasklist
---
This document will cover the process of assigning and displaying tasks to users in the DEMO-camunda-bpm-platform. We'll cover:

1. How tasks are assigned to users
2. How assigned tasks are displayed to users.

<SwmSnippet path="/engine/src/main/java/org/camunda/bpm/engine/task/TaskQuery.java" line="41">

---

# Assigning Tasks to Users

The `TaskQuery` interface provides methods for querying tasks. The `taskId` method is used to select tasks with a given task id, while the `taskAssignee` and `taskAssigneeIn` methods are used to select tasks assigned to a specific user or users respectively. These methods are used in various parts of the codebase to assign tasks to users.

```java
  TaskQuery taskId(String taskId);

  /**
   * Only select tasks with the given task ids.
   */
  TaskQuery taskIdIn(String... taskIds);

  /**
   * Only select tasks with the given name.
   * The query will match the names of tasks in a case-insensitive way.
   */
  TaskQuery taskName(String name);

  /**
   * Only select tasks with a name not matching the given name/
   * The query will match the names of tasks in a case-insensitive way.
   */
  TaskQuery taskNameNotEqual(String name);

  /**
   * Only select tasks with a name matching the parameter.
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
