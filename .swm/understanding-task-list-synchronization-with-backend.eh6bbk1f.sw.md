---
title: Understanding Task List Synchronization with Backend
---
This document will cover the process of updating and synchronizing the task list with the backend in the DEMO-camunda-bpm-platform repo. The main topics we'll cover are:

1. How the task list is updated in the codebase.
2. How the task list is synchronized with the backend.

<SwmSnippet path="/webapps/frontend/ui/tasklist/client/scripts/task/directives/cam-tasklist-task-meta.js" line="123">

---

# Updating the Task List

The `updateTask` function in `cam-tasklist-task-meta.js` is responsible for updating a task. It prepares the task data, removing unnecessary properties, and then calls the `Task.update` function to send the updated task data to the backend.

```javascript
        function updateTask() {
          var toSend = $scope.task;

          delete toSend._embedded;
          delete toSend._links;

          toSend.due = fixDate(toSend.due);
          toSend.followUp = fixDate(toSend.followUp);

          Task.update(toSend, function(err) {
            reload();
            if (err) {
              return errorHandler('TASK_UPDATE_ERROR', err);
            }
          });
        }
```

---

</SwmSnippet>

<SwmSnippet path="/engine/src/main/java/org/camunda/bpm/engine/impl/history/producer/DefaultHistoryEventProducer.java" line="711">

---

# Synchronizing the Task List with the Backend

The `createActivityInstanceUpdateEvt` function in `DefaultHistoryEventProducer.java` is responsible for synchronizing the task list with the backend. It creates a new `HistoricActivityInstanceEventEntity` and initializes it with the updated task data. If the task has been assigned, it also updates the task assignment.

```java
  @Override
  public HistoryEvent createActivityInstanceUpdateEvt(DelegateExecution execution, DelegateTask task) {
    final ExecutionEntity executionEntity = (ExecutionEntity) execution;

    // create event instance
    HistoricActivityInstanceEventEntity evt = loadActivityInstanceEventEntity(executionEntity);

    // initialize event
    initActivityInstanceEvent(evt, executionEntity, HistoryEventTypes.ACTIVITY_INSTANCE_UPDATE);

    // update task assignment
    if(task != null) {
      evt.setTaskId(task.getId());
      evt.setTaskAssignee(task.getAssignee());
    }

    return evt;
  }
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBREVNTy1jYW11bmRhLWJwbS1wbGF0Zm9ybSUzQSUzQXN3aW1taW8=" repo-name="DEMO-camunda-bpm-platform"><sup>Powered by [Swimm](/)</sup></SwmMeta>
