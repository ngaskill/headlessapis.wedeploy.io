---
title: "Documents"
description: "Documents Endpoint documentation"
order: 1
---

## Model

The following fields are currently supported for this model:

* **contentUrl**: The documents's content URL.
* **dateCreated**: The documents's creation date.
* **dateModified**: The date the document was last modified.
* **description**: The documents's description.
* **encodingFormat**: The document's encoding format (e.g: application/pdf).
* **fileExtension**: The documents's file extension (e.g: pdf).
* **keywords**: The keywords associated to this document.
* **sizeInBytes**: The documents's size in bytes.
* **title**: The documents's title.

This model also contains these links:

* **creator**:  The creator of this document.
* **category**: The categories associated with this document.
* **folder**: The folder where this document is located.

This model may also contain an **adaptedMedia** field,
with a **total** field, with the number of adaptedMedia elements and
an array of adaptedMedia elements, where each of them contains the
following fields:

* **contentUrl**: The URL of the adaptive media element.
* **height**: The height in pixels.
* **resolutionName**: The name of the resolution.
* **sizeInBytes**: The size in bytes.
* **width**: The width in pixels.

## Example

This API supports [pagination](/docs/general/pagination.html). 

In the following requests to this endpoint, `{{contentSpaceId}}` is the ID of the content space that the document belongs to.

In the response, the `_embedded` section contains the `Liferay:Document` key. This key contains the list of documents:

```bash
//display-name{request}
curl --request GET \
  --url http://localhost:8080/o/api/documents-repository/{{contentSpaceId}}/document?page=1&per_page=1
```

```json
//display-name{response}
{
    "total": 1,
    "count": 1,
    "_links": {
        "self": {
            "href": "http://localhost:8080/o/api/documents-repository/20127/document?page=1&per_page=1"
        },
        "first": {
            "href": "http://localhost:8080/o/api/documents-repository/20127/document?page=1&per_page=1"
        },
        "last": {
            "href": "http://localhost:8080/o/api/documents-repository/20127/document?page=1&per_page=1"
        },
        "collection": {
            "href": "http://localhost:8080/o/api/documents-repository/20127/document"
        }
    },
    "_embedded": {
        "Liferay:Document": [
            {
                "sizeInBytes": 35189,
                "contentUrl": "http://localhost:8080/documents/20127/0/feliz-2019.jpeg/bf054c54-1c20-ba7b-c07f-9c740dc273e1?t=1546533330994",
                "dateCreated": "2019-01-03T16:35Z",
                "dateModified": "2019-01-03T16:35Z",
                "encodingFormat": "image/jpeg",
                "fileExtension": "jpeg",
                "title": "feliz-2019.jpeg",
                "keywords": [],
                "_links": {
                    "self": {
                        "href": "http://localhost:8080/o/api/document/38943"
                    },
                    "folder": {
                        "href": "http://localhost:8080/o/api/folder/0"
                    },
                    "creator": {
                        "href": "http://localhost:8080/o/api/user-account/20140"
                    },
                    "category": {
                        "href": "http://localhost:8080/o/api/document/38943/categories"
                    }
                },
                "_embedded": {
                    "adaptedMedia": {
                        "total": 2,
                        "_embedded": [
                            {
                                "height": 512,
                                "sizeInBytes": 22606,
                                "width": 512,
                                "contentUrl": "http://localhost:8080/o/adaptive-media/image/38943/Preview-1000x0/feliz-2019.jpeg",
                                "resolutionName": "Preview-1000x0"
                            },
                            {
                                "height": 300,
                                "sizeInBytes": 12598,
                                "width": 300,
                                "contentUrl": "http://localhost:8080/o/adaptive-media/image/38943/Thumbnail-300x300/feliz-2019.jpeg",
                                "resolutionName": "Thumbnail-300x300"
                            }
                        ]
                    }
                }
            }
        ]
    }
}
```

When navigating through a list of entities, the `self` rel contains the link to each entity. 

You can find more examples [here](/docs/content-space/documentsRepository/documents/examples.html).
