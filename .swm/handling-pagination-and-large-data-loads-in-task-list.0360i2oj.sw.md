---
title: Handling Pagination and Large Data Loads in Task List
---
This document will cover the process of handling pagination or loading large number of tasks in the tasklist, which includes:

1. Understanding the pagination size and how it's used
2. How the FetchAndLockBuilder interface is used to fetch and lock tasks
3. How the TaskCountByCandidateGroupResult interface is used to get the task count for a specific group
4. How the TaskReport interface is used to get the number of tasks per group
5. How the ExternalTaskService interface is used to fetch and lock tasks
6. How the TaskManager class is used to find tasks by query criteria and find task count by query criteria.

<SwmSnippet path="/webapps/frontend/ui/tasklist/client/scripts/controller/cam-tasklist-view-ctrl.js" line="66">

---

# Understanding the pagination size and how it's used

The `paginationSize` variable is set to 2000, which means that the tasklist will load 2000 tasks at a time. The `pages` variable is calculated by dividing the total count of tasks by the `paginationSize`, which gives the total number of pages required to display all tasks.

```javascript
          var paginationSize = 2000;

          var pages = Math.ceil(count / paginationSize);
```

---

</SwmSnippet>

<SwmSnippet path="/engine/src/main/java/org/camunda/bpm/engine/externaltask/FetchAndLockBuilder.java" line="22">

---

# How the FetchAndLockBuilder interface is used to fetch and lock tasks

The `FetchAndLockBuilder` interface is used to fetch and lock tasks. It provides methods to configure the workerId, the maximum number of tasks to fetch (`maxTasks`), and whether to consider priority during the fetch and lock operation (`usePriority`).

```java
public interface FetchAndLockBuilder {

  /**
   * Configures the workerId that will be used during the Fetch and Lock operation.
   *
   * @param workerId the given workerId
   * @return the builder
   */
  FetchAndLockBuilder workerId(String workerId);

  /**
   * Configures the max tasks fetching that will be used during the Fetch and Lock operation.
   *
   * @param maxTasks the given number of max tasks
   * @return the builder
   */
  FetchAndLockBuilder maxTasks(int maxTasks);

  /**
   * Configures fetching to consider (or not) priority during the Fetch and Lock operation.
   *
```

---

</SwmSnippet>

<SwmSnippet path="/engine/src/main/java/org/camunda/bpm/engine/task/TaskCountByCandidateGroupResult.java" line="24">

---

# How the TaskCountByCandidateGroupResult interface is used to get the task count for a specific group

The `TaskCountByCandidateGroupResult` interface provides a method `getTaskCount()` to get the number of tasks for a specific group.

```java
public interface TaskCountByCandidateGroupResult {

  /** The number of tasks for a specific group */
  int getTaskCount();

  /** The group which as the number of tasks */
  String getGroupName();

}
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
