# Task Check Items

## TaskCheckItem Fields

Field | Description
--------- | -----------
project_id | Project ID the task_check_item belongs to
task_id | Task ID the task_check_item belongs to
name | Name of task_check_item
checked | Status of task_check_item (true = yes, false = no, null = not set)
creator_user_id | User ID of the task_check_item's creator
last_editor_user_id | User ID of the task_check_item's last editor

## Get TaskCheckItems

```http
GET /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/task_check_items HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
    {
        "created_at": "2014-07-02T02:22:44.000Z",
        "updated_at": "2014-07-02T02:22:44.000Z",
        "device_created_at": "2014-07-02T02:22:44.000Z",
        "device_updated_at": "2014-07-02T02:22:44.000Z",
        "resolved_conflict": false,
        "id": "65ed52b4-52ac-42d8-9cd3-deeb2e4f196e",
        "project_id": "ae786b3e-4773-4840-a22e-a20027f00787",
        "task_id": "a5299a37-fe29-4f38-8aca-488680048a85",
        "creator_user_id": 1,
        "last_editor_user_id": 1,
        "name": "First",
        "checked": null,
        "deleted_at": null
    },
    {
        "created_at": "2014-07-02T02:22:44.000Z",
        "updated_at": "2014-07-02T02:22:44.000Z",
        "device_created_at": "2014-07-02T02:22:44.000Z",
        "device_updated_at": "2014-07-02T02:22:44.000Z",
        "resolved_conflict": false,
        "id": "9d2ccc75-d432-4a26-ae99-90b4f70c112c",
        "project_id": "ae786b3e-4773-4840-a22e-a20027f00787",
        "task_id": "a5299a37-fe29-4f38-8aca-488680048a85",
        "creator_user_id": 1,
        "last_editor_user_id": 1,
        "name": "Second",
        "checked": null,
        "deleted_at": null
    }
]
```

This endpoint retrieves all task_check_items.

### HTTP Requests

`GET /projects/<Project ID>/task_check_items`

`GET /projects/<Project ID>/tasks/<Task ID>/task_check_items`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the project to retrieve
Task ID | The ID of the task to retrieve

## Get TaskCheckItem

```http
GET /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/task_check_items/29ca4ad0-a413-48aa-b8b8-28242d3cc205 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "created_at": "2014-07-02T02:22:44.000Z",
    "updated_at": "2014-07-02T02:22:44.000Z",
    "device_created_at": "2014-07-02T02:22:44.000Z",
    "device_updated_at": "2014-07-02T02:22:44.000Z",
    "resolved_conflict": false,
    "id": "65ed52b4-52ac-42d8-9cd3-deeb2e4f196e",
    "project_id": "ae786b3e-4773-4840-a22e-a20027f00787",
    "task_id": "a5299a37-fe29-4f38-8aca-488680048a85",
    "creator_user_id": 1,
    "last_editor_user_id": 1,
    "name": "First",
    "checked": null,
    "deleted_at": null
}
```

This endpoint retrieves a specific task_check_item.

### HTTP Request

`GET /projects/<Project ID>/task_check_items/<TaskCheckItem ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the task_check_item's project
TaskCheckItem ID | The ID of the task_check_item to retrieve

## Post TaskCheckItem

```http
POST /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/tasks/75b86f78-0a94-42ea-9d58-a0f8fb5ed4bb/task_check_items HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{
    "name": "Step 1: Fix"
}
```

> The above command returns:

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "created_at": "2014-07-02T02:22:44.000Z",
    "updated_at": "2014-07-02T02:22:44.000Z",
    "device_created_at": "2014-07-02T02:22:44.000Z",
    "device_updated_at": "2014-07-02T02:22:44.000Z",
    "resolved_conflict": false,
    "id": "65ed52b4-52ac-42d8-9cd3-deeb2e4f196e",
    "project_id": "ae786b3e-4773-4840-a22e-a20027f00787",
    "task_id": "a5299a37-fe29-4f38-8aca-488680048a85",
    "creator_user_id": 1,
    "last_editor_user_id": 1,
    "name": "First",
    "checked": null,
    "deleted_at": null
}
```

This endpoint creates a new task_check_item.

### HTTP Request

`POST /projects/<Project ID>/tasks/<Task ID>/task_check_items`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the task_check_item's project
Task ID | The ID of the task_check_item's task

## Batch TaskCheckItem

```http
POST /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/tasks/75b86f78-0a94-42ea-9d58-a0f8fb5ed4bb/task_check_items/batch HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{ "template_checklist_id" : "aba2c9a1-da23-4e6d-a9b0-c20b8497a942" }
```

> The above command returns:

```http
HTTP/1.1 201 Created
Content-Type: application/json

[
    {
        "created_at": "2014-07-02T02:22:44.000Z",
        "updated_at": "2014-07-02T02:22:44.000Z",
        "device_created_at": "2014-07-02T02:22:44.000Z",
        "device_updated_at": "2014-07-02T02:22:44.000Z",
        "resolved_conflict": false,
        "id": "65ed52b4-52ac-42d8-9cd3-deeb2e4f196e",
        "project_id": "ae786b3e-4773-4840-a22e-a20027f00787",
        "task_id": "a5299a37-fe29-4f38-8aca-488680048a85",
        "creator_user_id": 1,
        "last_editor_user_id": 1,
        "name": "First",
        "checked": null,
        "deleted_at": null
    },
    {
        "created_at": "2014-07-02T02:22:44.000Z",
        "updated_at": "2014-07-02T02:22:44.000Z",
        "device_created_at": "2014-07-02T02:22:44.000Z",
        "device_updated_at": "2014-07-02T02:22:44.000Z",
        "resolved_conflict": false,
        "id": "9d2ccc75-d432-4a26-ae99-90b4f70c112c",
        "project_id": "ae786b3e-4773-4840-a22e-a20027f00787",
        "task_id": "a5299a37-fe29-4f38-8aca-488680048a85",
        "creator_user_id": 1,
        "last_editor_user_id": 1,
        "name": "Second",
        "checked": null,
        "deleted_at": null
    }
]
```

This endpoint creates new task_check_items from a template_checklist.

### HTTP Request

`POST /projects/<Project ID>/tasks/<Task ID>/task_check_items/batch`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the task_check_item's project
Task ID | The ID of the task_check_item's task

### Body Parameters

Parameter | Description
--------- | -----------
TemplateChecklist ID | The ID of the template checklist to create items from

## Update TaskCheckItem

```http
PATCH /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/task_check_items/75d68ca1-0fc1-456a-bd9d-8b23875ac540 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{ "checked": true }
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "created_at": "2014-07-02T02:22:44.000Z",
    "updated_at": "2014-07-02T02:22:44.000Z",
    "device_created_at": "2014-07-02T02:22:44.000Z",
    "device_updated_at": "2014-07-02T02:22:44.000Z",
    "resolved_conflict": false,
    "id": "65ed52b4-52ac-42d8-9cd3-deeb2e4f196e",
    "project_id": "ae786b3e-4773-4840-a22e-a20027f00787",
    "task_id": "a5299a37-fe29-4f38-8aca-488680048a85",
    "creator_user_id": 1,
    "last_editor_user_id": 1,
    "name": "First",
    "checked": true,
    "deleted_at": null
}
```

This endpoint updates a specific task_check_item.

### HTTP Request

`PATCH /projects/<Project ID>/task_check_items/<TaskCheckItem ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the task_check_item's project
TaskCheckItem ID | The ID of the task_check_item to retrieve