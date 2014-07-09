# TaskCheckItems

## TaskCheckItem Fields

Field | Description
--------- | -----------
project_id | Project ID the task_check_item belongs to
task_id | Task ID the task_check_item belongs to
name | Name of task_check_item
checked | true = yes, false = no, null = not set
creator_user_id | User ID of the task_check_item's creator
last_editor_user_id | User ID of the task_check_item's last editor

## Get TaskCheckItems

```shell
curl "https://console.fieldwire.net/api/v1/projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/task_check_items" \
  -H "Authorization: Token api=[api token]>,project=[project token]"
```

> The above command returns JSON structured like this:

```json
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

`GET https://console.fieldwire.net/api/v1/projects/<Project ID>/task_check_items`

`GET https://console.fieldwire.net/api/v1/projects/<Project ID>/tasks/<Task ID>/task_check_items`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the project to retrieve
Task ID | The ID of the task to retrieve

## Get TaskCheckItem

```shell
curl "https://console.fieldwire.net/api/v1/projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/task_check_items/29ca4ad0-a413-48aa-b8b8-28242d3cc205" \
  -H "Authorization: Token api=[api token]>,project=[project token]"
```

> The above command returns JSON structured like this:

```json
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

`GET https://console.fieldwire.net/api/v1/projects/<Project ID>/task_check_items/<TaskCheckItem ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the task_check_item's project
TaskCheckItem ID | The ID of the task_check_item to retrieve

## Post TaskCheckItem

```shell
curl "https://console.fieldwire.net/api/v1/projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/tasks/75b86f78-0a94-42ea-9d58-a0f8fb5ed4bb/task_check_items" \
  -X POST \
  -H "Authorization: Token api=[api token]>,project=[project token]" \
  -H "Content-type: application/json" \
  -d '{ "task_check_item": { "name": "Step 1: Fix" }}'
```

> The above command returns JSON structured like this:

```json
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

`POST https://console.fieldwire.net/api/v1/projects/<Project ID>/tasks/<Task ID>/task_check_items`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the task_check_item's project
Task ID | The ID of the task_check_item's task

## Batch TaskCheckItem

```shell
curl "https://console.fieldwire.net/api/v1/projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/tasks/75b86f78-0a94-42ea-9d58-a0f8fb5ed4bb/task_check_items/batch" \
  -X POST \
  -H "Authorization: Token api=[api token]>,project=[project token]" \
  -H "Content-type: application/json" \
  -d '{ "template_checklist_id" : "aba2c9a1-da23-4e6d-a9b0-c20b8497a942" }'
```

> The above command returns JSON structured like this:

```json
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

`POST https://console.fieldwire.net/api/v1/projects/<Project ID>/tasks/<Task ID>/task_check_items/batch`

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

```shell
curl "https://console.fieldwire.net/api/v1/projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/task_check_items/75d68ca1-0fc1-456a-bd9d-8b23875ac540" \
  -X PATCH \
  -H "Authorization: Token api=[api token]>,project=[project token]" \
  -H "Content-type: application/json" \
  -d '{ "task_check_item": { "checked": true }'
```

> The above command returns JSON structured like this:

```json
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

`PATCH https://console.fieldwire.net/api/v1/projects/<Project ID>/task_check_items/<TaskCheckItem ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the task_check_item's project
TaskCheckItem ID | The ID of the task_check_item to retrieve

## Delete TaskCheckItem

```shell
curl "https://console.fieldwire.net/api/v1/projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/task_check_items/75d68ca1-0fc1-456a-bd9d-8b23875ac540" \
  -X DELETE \
  -H "Authorization: Token api=[api token]>,project=[project token]" \
  -H "Content-type: application/json"
```

> The above command returns 204 No Content

This endpoint updates a specific task_check_item.

### HTTP Request

`DELETE https://console.fieldwire.net/api/v1/projects/<Project ID>/task_check_items/<TaskCheckItem ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the task_check_item's project
TaskCheckItem ID | The ID of the task_check_item to retrieve