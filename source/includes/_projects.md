# Projects

## Project Fields

Field | Description | Type | Required? | Editable? | Default
--------- | --------- | --------- | --------- | --------- | ---------
name | Name of the project | String | x | x |
address | Address of the project | String | | x |
archived_at | The time when the project was archived | DateTime | | x |
access_token | Token to be used in successive API calls for this project | String | x | | _generated_
is_email_notifications_enabled | If enabled, project members will receive an email notification whenever their tasks are updated | Boolean | x | x | true
currency | Currency of project (ISO) | String | x | x | USD
man_power_units | Manpower units of project ("man-hours", "man-days", "man-months") | String | x | x | man-hours
time_zone | Timezone of project | DateTime | x | x | Pacific Time (US & Canada)
prompt_effort_on_complete | Prompt users to enter manpower and cost when completing tasks | Boolean | x | x | false
logo_url | Url of project's logo | String | | x |

## Get Projects

```http
GET /projects HTTP/1.1
Authorization: Token api=[api token]
Content-Type: application/json
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
    {
        "created_at": "2014-08-15T00:38:29.683Z",
        "updated_at": "2014-08-15T00:38:30.059Z",
        "device_created_at": "2014-08-15T00:38:29.683Z",
        "device_updated_at": "2014-08-15T00:38:29.683Z",
        "resolved_conflict": false,
        "id": "b5c08097-74f1-4a8f-a9a8-52e16295f6a4",
        "name": "Project 1",
        "address": null,
        "archived_at": null,
        "access_token": "e9f50ef0906fce7fa59faa726f66c28a",
        "is_email_notifications_enabled": false,
        "deleted_at": null
    },
    {
        "created_at": "2014-08-15T00:42:36.679Z",
        "updated_at": "2014-08-15T01:24:21.385Z",
        "device_created_at": "2014-08-15T00:42:36.679Z",
        "device_updated_at": "2014-08-15T01:24:21.369Z",
        "resolved_conflict": false,
        "id": "37b9103e-e3eb-438f-8c38-5f2736a952dd",
        "name": "Project 2",
        "address": null,
        "archived_at": null,
        "access_token": "0b6e211576551a82ac1846777cef64d0",
        "is_email_notifications_enabled": false,
        "deleted_at": null
    }
]
```

This endpoint retrieves all projects created by the api token.

### HTTP Request

`GET /projects`

## Get Project

```http
GET /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "created_at": "2014-04-30T19:02:10.000Z",
    "updated_at": "2014-04-30T19:02:10.000Z",
    "device_created_at": "2014-04-30T19:02:10.000Z",
    "device_updated_at": "2014-04-30T19:02:10.000Z",
    "resolved_conflict": false,
    "id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
    "name": "Sample project",
    "address": null,
    "archived_at": null,
    "deleted_at": null
}
```

This endpoint retrieves a specific project.

### HTTP Request

`GET /projects/<Project ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the project to retrieve activity for

## Get Project Activity

```http
GET /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/activity HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "users": "2014-08-15T19:42:24.359Z",
    "teams": "2014-08-15T00:42:36.722Z",
    "floorplans": "2014-08-15T01:28:17.107Z",
    "tasks": null,
    "bubbles": null,
    "hyperlinks": null,
    "markups": null,
    "attachments": null,
    "task_check_items": null,
    "template_checklists": null,
    "automatic_hyperlinks": null,
    "bubble_markups": null
}
```

This endpoint retrieves a specific project.

### HTTP Request

`GET /projects/<Project ID>/activity`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the project to retrieve

## Post Project

```http
POST /projects HTTP/1.1
Authorization: Token api=[api token]>
Content-type: application/json

{ "name": "Project 1" }
```

> The above command returns:

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "created_at": "2014-08-15T00:38:29.683Z",
    "updated_at": "2014-08-15T00:38:30.059Z",
    "device_created_at": "2014-08-15T00:38:29.683Z",
    "device_updated_at": "2014-08-15T00:38:29.683Z",
    "resolved_conflict": false,
    "id": "b5c08097-74f1-4a8f-a9a8-52e16295f6a4",
    "name": "Project 1",
    "address": null,
    "archived_at": null,
    "access_token": "e9f50ef0906fce7fa59faa726f66c28a",
    "is_email_notifications_enabled": false,
    "deleted_at": null
}
```

This endpoint creates a new Project.

### HTTP Request

`POST /projects`

## Cloning Projects

Cloning projects: when creating a project you can automatically re-invite members and/or re-create teams (categories) from an existing project by passing the 'source' parameter

> Clone project request

```json
{
    "project" : {
        "name": "Cloned Project"
    },
    "source" : {
        "id": "<Project ID to clone>",
        "copy_users": true,
        "copy_teams": true
    }
}
```



## Update Project

```http
PATCH /projects/b5c08097-74f1-4a8f-a9a8-52e16295f6a4 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{ "name": "Updated Project" }
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "created_at": "2014-08-15T00:38:29.683Z",
    "updated_at": "2014-08-15T00:38:30.059Z",
    "device_created_at": "2014-08-15T00:38:29.683Z",
    "device_updated_at": "2014-08-15T00:38:29.683Z",
    "resolved_conflict": false,
    "id": "b5c08097-74f1-4a8f-a9a8-52e16295f6a4",
    "name": "Updated Project",
    "address": null,
    "archived_at": null,
    "access_token": "e9f50ef0906fce7fa59faa726f66c28a",
    "is_email_notifications_enabled": false,
    "deleted_at": null
}
```

This endpoint updates a specific Project.

### HTTP Request

`PATCH /projects/<Project ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the project

## Delete Project

```http
DELETE /projects/b5c08097-74f1-4a8f-a9a8-52e16295f6a4 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 204 OK
Content-Type: application/json
```

This endpoint deletes the project.

### HTTP Request

`DELETE /projects/<Project ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the project