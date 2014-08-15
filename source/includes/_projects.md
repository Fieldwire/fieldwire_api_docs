# Projects

## Project Fields

Field | Description
--------- | -----------
name | Name of the project
address | Address of the project
archived_at | The time when the project was archived
access_token | Token to be used in successive API calls for this project
is_email_notifications_enabled | If enabled, project members will receive an email notification whenever their tasks are updated

## Get Projects

```shell
curl "https://console.fieldwire.net/api/v2/projects" \
  -H "Authorization: Token api=[api token]>"
```

> The above command returns JSON structured like this:

```json
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

`GET https://console.fieldwire.net/api/v2/projects`

## Get Project

```shell
curl "https://console.fieldwire.net/api/v2/projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027"
  -H "Authorization: Token api=[api token]>,project=[project token]"
```

> The above command returns JSON structured like this:

```json
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

`GET https://console.fieldwire.net/api/v2/projects/<Project ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the project to retrieve

## Post Project

```shell
curl "https://console.fieldwire.net/api/v2/projects" \
  -X POST \
  -H "Authorization: Token api=[api token]>,project=[project token]" \
  -H "Content-type: application/json" \
  -d '{ "project": { "name": "Project 1" } }'
```

> The above command returns JSON structured like this:

```json
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

`POST https://console.fieldwire.net/api/v2/projects`

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

```shell
curl "https://console.fieldwire.net/api/v2/projects/b5c08097-74f1-4a8f-a9a8-52e16295f6a4" \
  -X PATCH \
  -H "Authorization: Token api=[api token]>,project=[project token]" \
  -H "Content-type: application/json" \
  -d '{ "Project": { "name": "Updated Project" } }'
```

> The above command returns JSON structured like this:

```json
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

`PATCH https://console.fieldwire.net/api/v2/projects/<Project ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the project

## Delete Project

```shell
curl "https://console.fieldwire.net/api/v2/projects/b5c08097-74f1-4a8f-a9a8-52e16295f6a4" \
  -X DELETE \
  -H "Authorization: Token api=[api token]>,project=[project token]" \
  -H "Content-type: application/json"
```

> The above command returns 204 No Content

This endpoint updates a specific Project.

### HTTP Request

`DELETE https://console.fieldwire.net/api/v2/projects/<Project ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the project