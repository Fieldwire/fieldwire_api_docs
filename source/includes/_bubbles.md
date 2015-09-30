# Bubbles

## Bubble Fields

Field | Description | Type | Non-null? | Editable? | Default
--------- | --------- | --------- | --------- | --------- | ---------
task_id | Task ID the bubble belongs to | UUID | x | |
content | Text content of bubble | String | | x |
kind | Enumeration of bubble (see below) | Integer | x | x | 1
file_url | Url of photo or attachment | String | | x |
flattened_file_url | Url of photo with annotation | String | | x |
thumb_url | Url of photo thumb | String | | x |
user_id | User ID that created bubble | Integer | x | | _generated_
tags | Array of strings of all tags on this bubble's bubbles | Array, string | x | x | [ ]

## Bubble Kinds

Kind | Description
--------- | -----------
1 | Text (has content)
2 | Log (has content)
10 | Photo (has file_url and thumb_url)
11 | Photo with annotations (has flattened_file_url, file_url and thumb_url)
12 | Drawing with annotations (has flattened_file_url, file_url and thumb_url)
20 | Attachment (has content and file_url)

## Get Bubbles

```http
GET /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/bubbles HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
    {
        "created_at": "2014-04-30T19:02:13.000Z",
        "updated_at": "2014-04-30T19:02:13.000Z",
        "device_created_at": "2014-04-30T19:02:13.000Z",
        "device_updated_at": "2014-04-30T19:02:13.000Z",
        "resolved_conflict": false,
        "id": "1cddce9f-a0be-4021-a005-c0195ba2442d",
        "content": "#rfi_41",
        "annotations": null,
        "kind": 1,
        "file_url": null,
        "flattened_file_url": null,
        "thumb_url": null,
        "task_id": "75b86f78-0a94-42ea-9d58-a0f8fb5ed4bb",
        "user_id": 2,
        "deleted_at": null,
        "tags": [
            "rfi_41"
        ]
    },
    {
        "created_at": "2014-04-30T19:02:14.000Z",
        "updated_at": "2014-04-30T19:02:14.000Z",
        "device_created_at": "2014-04-30T19:02:14.000Z",
        "device_updated_at": "2014-04-30T19:02:14.000Z",
        "resolved_conflict": false,
        "id": "aa2a8c87-7bfd-484d-ba40-aa16a9006219",
        "content": null,
        "annotations": null,
        "kind": 11,
        "file_url": "5f4d0626dd16584e1e661601661724ce.jpeg",
        "flattened_file_url": null,
        "thumb_url": "973e7fc42967f2e582ca7ddfba2dfe16.jpeg",
        "task_id": "75b86f78-0a94-42ea-9d58-a0f8fb5ed4bb",
        "user_id": 2,
        "deleted_at": null,
        "tags": []
    }
]
```

This endpoint retrieves all bubbles.

### HTTP Requests

`GET /projects/<Project ID>/bubbles`

`GET /projects/<Project ID>/tasks/<Task ID>/bubbles`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the project to retrieve
Task ID | The ID of the task to retrieve

## Get Bubble

```http
GET /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/bubbles/29ca4ad0-a413-48aa-b8b8-28242d3cc205 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "created_at": "2014-04-30T19:02:13.000Z",
    "updated_at": "2014-04-30T19:02:13.000Z",
    "device_created_at": "2014-04-30T19:02:13.000Z",
    "device_updated_at": "2014-04-30T19:02:13.000Z",
    "resolved_conflict": false,
    "id": "1cddce9f-a0be-4021-a005-c0195ba2442d",
    "content": "#rfi_41",
    "annotations": null,
    "kind": 1,
    "file_url": null,
    "flattened_file_url": null,
    "thumb_url": null,
    "task_id": "75b86f78-0a94-42ea-9d58-a0f8fb5ed4bb",
    "user_id": 2,
    "deleted_at": null,
    "tags": [
        "rfi_41"
    ]
}
```

This endpoint retrieves a specific bubble.

### HTTP Request

`GET /projects/<Project ID>/bubbles/<Bubble ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the bubble's project
Bubble ID | The ID of the bubble to retrieve

## Post Bubble

```http
POST /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/tasks/75b86f78-0a94-42ea-9d58-a0f8fb5ed4bb/bubbles HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{
    "content": "Check the spec for specific details on soffit install",
    "kind": 1,
    "user_id": 3
}
```

> The above command returns:

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "created_at": "2014-04-30T19:02:14.000Z",
    "updated_at": "2014-04-30T19:02:14.000Z",
    "device_created_at": "2014-04-30T19:02:14.000Z",
    "device_updated_at": "2014-04-30T19:02:14.000Z",
    "resolved_conflict": false,
    "id": "c743a741-a3e9-4c62-bfe1-03a38425cb49",
    "content": "Check the spec for specific details on soffit install",
    "annotations": null,
    "kind": 1,
    "file_url": null,
    "flattened_file_url": null,
    "thumb_url": null,
    "task_id": "75b86f78-0a94-42ea-9d58-a0f8fb5ed4bb",
    "user_id": 3,
    "deleted_at": null,
    "tags": []
}
```

This endpoint creates a new bubble.

### HTTP Request

`POST /projects/<Project ID>/tasks/<Task ID>/bubbles`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the bubble's project
Task ID | The ID of the bubble's task

## Update Bubble

```http
PATCH /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/bubbles/75d68ca1-0fc1-456a-bd9d-8b23875ac540 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{ "content": "Spec not available. Check with foreman." }
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "created_at": "2014-04-30T19:02:14.000Z",
    "updated_at": "2014-04-30T19:02:14.000Z",
    "device_created_at": "2014-04-30T19:02:14.000Z",
    "device_updated_at": "2014-04-30T19:02:14.000Z",
    "resolved_conflict": false,
    "id": "c743a741-a3e9-4c62-bfe1-03a38425cb49",
    "content": "Spec not available. Check with foreman.",
    "annotations": null,
    "kind": 1,
    "file_url": null,
    "flattened_file_url": null,
    "thumb_url": null,
    "task_id": "75b86f78-0a94-42ea-9d58-a0f8fb5ed4bb",
    "user_id": 3,
    "deleted_at": null,
    "tags": []
}
```

This endpoint updates a specific bubble.

### HTTP Request

`PATCH /projects/<Project ID>/bubbles/<Bubble ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the bubble's project
Bubble ID | The ID of the bubble to retrieve

## Delete Bubble

```http
DELETE /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/bubbles/75d68ca1-0fc1-456a-bd9d-8b23875ac540 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 204 OK
Content-Type: application/json
```

This endpoint deletes the bubble.

### HTTP Request

`DELETE /projects/<Project ID>/bubbles/<Bubble ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the bubble's project
Bubble ID | The ID of the bubble to retrieve