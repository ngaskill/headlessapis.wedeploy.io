---
title: Workflow Logs
description: Workflow Logs Endpoint documentation
weight: 2
---

## Model

The following fields are currently supported for this model: 

* **dateCreated**: The workflow log's creation date.
* **commentLog**: The workflow log's comments.
* **previousState**: The workflow log's state prior to the current state.
* **state**: The workflow log's current state. 
* **type**: The workflow log's type (e.g.: `TASK_ASSIGNMENT`, `TASK_COMPLETION`, `TASK_UPDATE`).

This model also offers the following links: 

* **auditPerson**: 
* **person**: The person currently assigned to the workflow task.
* **previousPerson**: The person assigned to the workflow task prior to the current assignee.
* **task**: The workflow log's workflow task.

## Example

Here's an example of a request to this endpoint: 

```bash
curl --request GET \
  --url http://localhost:8080/o/api/p/workflow-tasks/36564/workflow-logs \
  --header 'Accept: application/hal+json'
```

In a JSON-HAL formatted response, the `_embedded` section contains the `WorkflowLog` key. This key contains the workflow log: 

```json
{
    "total": 1,
    "count": 1,
    "_links": {
        "self": {
            "href": "http://localhost:8080/o/api/p/workflow-tasks/51632/workflow-logs?page=1&per_page=30"
        },
        "first": {
            "href": "http://localhost:8080/o/api/p/workflow-tasks/51632/workflow-logs?page=1&per_page=30"
        },
        "last": {
            "href": "http://localhost:8080/o/api/p/workflow-tasks/51632/workflow-logs?page=1&per_page=30"
        },
        "collection": {
            "href": "http://localhost:8080/o/api/p/workflow-tasks/51632/workflow-logs"
        }
    },
    "_embedded": {
        "WorkflowLog": [
            {
                "dateCreated": "2018-12-03T14:19Z",
                "commentLog": "Assigned initial task.",
                "state": "review",
                "type": "TASK_ASSIGNMENT",
                "_links": {
                    "self": {
                        "href": "http://localhost:8080/o/api/p/workflow-logs/51641"
                    },
                    "auditPerson": {
                        "href": "http://localhost:8080/o/api/p/user-account/20139"
                    },
                    "person": {
                        "href": "http://localhost:8080/o/api/p/user-account/0"
                    },
                    "previousPerson": {
                        "href": "http://localhost:8080/o/api/p/user-account/0"
                    },
                    "task": {
                        "href": "http://localhost:8080/o/api/p/workflow-tasks/51632"
                    }
                }
            }
        ]
    }
}
```

When navigating through a list of entities, the `self` rel contains the link to each entity. 

You can find more examples [here](/docs/my-user-account/workflow-tasks/workflow-logs/examples.html).
