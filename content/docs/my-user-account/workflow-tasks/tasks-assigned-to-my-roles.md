---
title: Tasks Assigned To My Roles
description: Tasks Assigned To My Roles Endpoint documentation
weight: 4
---

## Model

The following fields are currently supported for this model: 

* **completed**: Whether the workflow task is complete.
* **dateCompleted**: The workflow task's completion date.
* **dateCreated**: The workflow task's creation date.
* **dueDate**: The workflow task's expiration date.
* **definitionName**: 
* **description**:
* **name**:

This model also contains the following links:

* **logs**: The workflow task's `WorkflowLog` list. You can read more about this [here](/docs/my-user-account/workflow-tasks/workflow-logs/index.html).

This model also has information about the object in the workflow task:

* **object**: The object in the workflow task.
  * **identifier**: The object's URL.
  * **resourceType**: The object's type (e.g., `Comment` or `BlogPosting`).

## Example

Here's an example of a request to this endpoint: 

```bash
curl --request GET \
  --url http://localhost:8080/o/api/p/r/workflow-tasks/assigned-to-my-roles \
  --header 'Accept: application/hal+json'
```

In a JSON-HAL formatted response, the `_embedded` section contains the `WorkflowTask` key. This key contains the workflow task: 

```json
{
   "total": 1,
   "count": 1,
   "_links": {
       "self": {
           "href": "http://localhost:8080/o/api/p/r/workflow-tasks/assigned-to-my-roles?page=1&per_page=30"
       },
       "first": {
           "href": "http://localhost:8080/o/api/p/r/workflow-tasks/assigned-to-my-roles?page=1&per_page=30"
       },
       "last": {
           "href": "http://localhost:8080/o/api/p/r/workflow-tasks/assigned-to-my-roles?page=1&per_page=30"
       },
       "collection": {
           "href": "http://localhost:8080/o/api/p/r/workflow-tasks/assigned-to-my-roles"
       }
   },
   "_embedded": {
       "WorkflowTask": [
           {
               "completed": false,
               "dateCreated": "2018-12-03T11:39Z",
               "definitionName": "Single Approver",
               "name": "review",
               "_links": {
                   "self": {
                       "href": "http://localhost:8080/o/api/p/workflow-tasks/36678"
                   },
                   "logs": {
                       "href": "http://localhost:8080/o/api/p/workflow-tasks/36678/workflow-logs"
                   }
               },
               "_embedded": {
                   "object": {
                       "identifier": "http://localhost:8080/o/api/p/blog-posting/36667",
                       "resourceType": "BlogPosting"
                   }
               }
           }
       ]
   }
}
```

When navigating through a list of entities, the `self` rel contains the link to each entity. 

You can find more examples [here](/docs/my-user-account/workflow-tasks/examples.html). 
