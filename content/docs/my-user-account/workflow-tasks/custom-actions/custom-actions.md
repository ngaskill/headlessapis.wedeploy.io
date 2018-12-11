---
title: Custom Actions
description: Workflow Tasks Custom Actions documentation
weight: 2
---

## Workflow Tasks Custom Actions

The responses in `json HAL` format will contain inside the `_embedded` section, the workflow task under the key `WorkflowTask`.

```json
{
    "completed": false,
    "dateCreated": "2018-12-03T14:19Z",
    "definitionName": "Single Approver",
    "name": "review",
    "_links": {
        "self": {
            "href": "http://localhost:8080/o/api/p/workflow-tasks/51632"
        },
        "logs": {
            "href": "http://localhost:8080/o/api/p/workflow-tasks/51632/workflow-logs"
        }
    },
    "_embedded": {
        "object": {
            "identifier": "http://localhost:8080/o/api/p/blog-posting/51621",
            "resourceType": "BlogPosting"
        }
    }
}
```

When navigating through a list of entities, the `self` rel contains the link to each entity. 

### Assign a Workflow Task to Me

You don't need additional attributes to perform this action. Here's an example of the request: 

```bash
curl --request POST \
  --url http://localhost:8080/o/api/c/workflow-tasks/42499/assign-to-me \
  --header 'Accept: application/hal+json' \
  --header 'Content-Type: application/json' \
  --data '{}'
```

### Assign a Workflow Task to a User

To perform this action, you need the `assigneeId` attribute: 

* **assigneeId**: The ID of the user to assign the workflow task to (e.g., `http://localhost:8080/o/api/p/user-account/20139`).

Here's an example of the request: 

```bash
curl --request POST \
  --url http://localhost:8080/o/api/c/workflow-tasks/42499/assign-to-user \
  --header 'Accept: application/hal+json' \
  --header 'Content-Type: application/json' \
  --data '{"assigneeId": ""}'
```

### Change a Workflow Task's Transition

To perform this action, you need the `transition` attribute:

* **transition**: The name of the transition you want to change in the workflow task (e.g., `approve`, `reject`). If the transition is empty, the custom actions use workflow definition's default transition.

Here's an example of the request: 

```bash
curl --request POST \
  --url http://localhost:8080/o/api/c/workflow-tasks/36633/change-transition \
  --header 'Accept: application/hal+json' \
  --header 'Content-Type: application/json' \
  --data '{"transition": ""}'
```

### Add/Update a Workflow Task's Due Date

To perform this action, you need these attributes:

* **dueDate**: The workflow task's due date.
* **comment** (_Optional_): An additional comment for the workflow log.

Here's an example of the request: 

```bash
curl --request POST \
  --url http://localhost:8080/o/api/c/workflow-tasks/36704/update-due-date \
  --header 'Content-Type: application/json' \
  --data '{"dueDate": "2018-12-31T23:59Z", "comment": "This is a comment"}'
```

When navigating through a list of entities, the `self` rel contains the link to each entity. 

You can find more examples [here](/docs/my-user-account/workflow-tasks/custom-actions/examples.html). 
