# Tasks

## Task Fields

Field | Description
--------- | -----------
project_id | Project ID task belongs to
team_id | Team ID task belongs to
floorplan_id | Floorplan ID task belongs to
name | Name of the task
priority | Priority of the task
pos_x | Horizontal pixels (from left of floorplan) of task pin's point
pos_y | Vertical pixels (from top of floorplan) of task pin's point
pos_z | Indicates layer of task
verified_at | Time when task was verified
fixed_at | Time when task was fixed
owner_user_id | User ID of task's owner
is_local | Indicates if task is positioned on floorplan
start_at | Time when task is to be started
*due_at (DEPRECATED)* | *Time when task is to be completed by*
due_date | Date when task is to be completed by
sequence_number | Unique sequential identifier of task on project
is_private | Indicates if task is private
user_ids | Array of User IDs that are following this task
tags | Array of strings of all tags on this task's bubbles

## Get Tasks

```http
GET /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/tasks HTTP/1.1
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
        "id": "dc381268-b8c2-4ad2-ad91-03e1ef99da55",
        "name": "Web List View",
        "priority": 1,
        "pos_x": 0,
        "pos_y": 0,
        "pos_z": 0,
        "verified_at": null,
        "fixed_at": null,
        "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
        "floorplan_id": null,
        "task_id": "85d48a03-c192-4963-89f3-571352e0a402",
        "owner_user_id": 1,
        "is_local": false,
        "start_at": null,
        "due_at": null,
        "sequence_number": 13,
        "is_private": false,
        "deleted_at": null,
        "user_ids": [],
        "tags": []
    },
    {
        "created_at": "2014-04-30T19:02:13.000Z",
        "updated_at": "2014-04-30T19:02:13.000Z",
        "device_created_at": "2014-04-30T19:02:13.000Z",
        "device_updated_at": "2014-04-30T19:02:13.000Z",
        "resolved_conflict": false,
        "id": "29ca4ad0-a413-48aa-b8b8-28242d3cc205",
        "name": "Panels are chipped.",
        "priority": 2,
        "pos_x": 652,
        "pos_y": 73,
        "pos_z": 0,
        "verified_at": null,
        "fixed_at": null,
        "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
        "floorplan_id": "d94f128b-d5a0-4325-95d8-32457af9ab3b",
        "task_id": "0bee6768-3948-4765-9087-dc86cabd41d6",
        "owner_user_id": 2,
        "is_local": true,
        "start_at": null,
        "due_at": null,
        "sequence_number": 14,
        "is_private": false,
        "deleted_at": null,
        "user_ids": [],
        "tags": []
    }
]
```

This endpoint retrieves all tasks.

### HTTP Request

`GET /projects/<Project ID>/tasks`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the project to retrieve

## Get Task

```http
GET /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/tasks/29ca4ad0-a413-48aa-b8b8-28242d3cc205 HTTP/1.1
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
    "id": "29ca4ad0-a413-48aa-b8b8-28242d3cc205",
    "name": "Panels are chipped.",
    "priority": 2,
    "pos_x": 652,
    "pos_y": 73,
    "pos_z": 0,
    "verified_at": null,
    "fixed_at": null,
    "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
    "floorplan_id": "d94f128b-d5a0-4325-95d8-32457af9ab3b",
    "task_id": "0bee6768-3948-4765-9087-dc86cabd41d6",
    "owner_user_id": 2,
    "is_local": true,
    "start_at": null,
    "due_at": null,
    "sequence_number": 14,
    "is_private": false,
    "deleted_at": null,
    "user_ids": [],
    "tags": []
}
```

This endpoint retrieves a specific task.

### HTTP Request

`GET /projects/<Project ID>/tasks/<Task ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the task's project
Task ID | The ID of the task to retrieve

## Post Task

```http
POST /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/tasks HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{
    "task": {
        "name": "Light socket under 2nd diffuser not getting power",
        "priority": 2,
        "pos_x": 1071,
        "pos_y": 457,
        "floorplan_id": "d94f128b-d5a0-4325-95d8-32457af9ab3b",
        "team_id": "3919a956-6f5b-4a25-abd8-eefa81378ef0",
        "owner_user_id": 2
    }
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
    "id": "75d68ca1-0fc1-456a-bd9d-8b23875ac540",
    "name": "Light socket under 2nd diffuser not getting power",
    "priority": 2,
    "pos_x": 1071,
    "pos_y": 457,
    "pos_z": 0,
    "verified_at": null,
    "fixed_at": null,
    "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
    "floorplan_id": "d94f128b-d5a0-4325-95d8-32457af9ab3b",
    "team_id": "3919a956-6f5b-4a25-abd8-eefa81378ef0",
    "owner_user_id": 2,
    "is_local": true,
    "start_at": null,
    "due_at": null,
    "sequence_number": 16,
    "is_private": false,
    "deleted_at": null,
    "user_ids": [],
    "tags": []
}
```

This endpoint creates a new task.

### HTTP Request

`POST /projects/<Project ID>/tasks`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the task's project

## Update Task

```http
PATCH /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/tasks/75d68ca1-0fc1-456a-bd9d-8b23875ac540 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{ "task": { "verified_at": "2014-04-30T19:02:14.000Z", "fixed_at": "2014-04-30T19:02:14.000Z" } }
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
    "id": "75d68ca1-0fc1-456a-bd9d-8b23875ac540",
    "name": "Light socket under 2nd diffuser not getting power",
    "priority": 2,
    "pos_x": 1071,
    "pos_y": 457,
    "pos_z": 0,
    "verified_at": "2014-04-30T19:02:14.000Z",
    "fixed_at": "2014-04-30T19:02:14.000Z",
    "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
    "floorplan_id": "d94f128b-d5a0-4325-95d8-32457af9ab3b",
    "team_id": "3919a956-6f5b-4a25-abd8-eefa81378ef0",
    "owner_user_id": 2,
    "is_local": true,
    "start_at": null,
    "due_at": null,
    "sequence_number": 16,
    "is_private": false,
    "deleted_at": null,
    "user_ids": [],
    "tags": []
}
```

This endpoint updates a specific task.

### HTTP Request

`PATCH /projects/<Project ID>/tasks/<Task ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the task's project
Task ID | The ID of the task to retrieve

## Delete Task

```http
DELETE /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/tasks/75d68ca1-0fc1-456a-bd9d-8b23875ac540 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 204 OK
Content-Type: application/json
```

This endpoint deletes the task.

### HTTP Request

`DELETE /projects/<Project ID>/tasks/<Task ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the task's project
Task ID | The ID of the task to retrieve