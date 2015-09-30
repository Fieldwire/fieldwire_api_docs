# Folders

## Folder Fields

Field | Description | Type | Non-null? | Editable? | Default
--------- | --------- | --------- | --------- | --------- | ---------
project_id | Project ID folder belongs to | UUID | x | |
name | Name of the folder | UUID | x | x |

## Get Folders

```http
GET /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/folders HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
    {
        "created_at": "2014-06-17T00:40:11.000Z",
        "updated_at": "2014-06-17T00:40:11.000Z",
        "device_created_at": "2014-06-17T00:40:11.000Z",
        "device_updated_at": "2014-06-17T00:40:11.000Z",
        "resolved_conflict": false,
        "id": "d426dce3-1b5f-446c-9ba2-7fd8e5781db5",
        "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
        "name": "Folder 1",
        "deleted_at": null
    },
    {
        "created_at": "2014-06-17T00:44:18.000Z",
        "updated_at": "2014-06-17T00:44:18.000Z",
        "device_created_at": "2014-06-17T00:44:18.000Z",
        "device_updated_at": "2014-06-17T00:44:18.000Z",
        "resolved_conflict": false,
        "id": "8c0c87d3-603a-4dd5-ac64-f11dd3ac2cf9",
        "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
        "name": "Folder 2",
        "deleted_at": null
    }
]
```

This endpoint retrieves all folders.

### HTTP Request

`GET /projects/<Project ID>/folders`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the project to retrieve

## Get Folder

```http
GET /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/folders/d426dce3-1b5f-446c-9ba2-7fd8e5781db5 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "created_at": "2014-06-17T00:40:11.000Z",
    "updated_at": "2014-06-17T00:40:11.000Z",
    "device_created_at": "2014-06-17T00:40:11.000Z",
    "device_updated_at": "2014-06-17T00:40:11.000Z",
    "resolved_conflict": false,
    "id": "d426dce3-1b5f-446c-9ba2-7fd8e5781db5",
    "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
    "name": "Folder 1",
    "deleted_at": null
}
```

This endpoint retrieves a specific team.

### HTTP Request

`GET /projects/<Project ID>/folders/<Folder ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the team's project
Folder ID | The ID of the team to retrieve

## Post Folder

```http
POST /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/folders HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{ "name": "folder 1" }
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "created_at": "2014-06-17T00:40:11.000Z",
    "updated_at": "2014-06-17T00:40:11.000Z",
    "device_created_at": "2014-06-17T00:40:11.000Z",
    "device_updated_at": "2014-06-17T00:40:11.000Z",
    "resolved_conflict": false,
    "id": "d426dce3-1b5f-446c-9ba2-7fd8e5781db5",
    "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
    "name": "Folder 1",
    "deleted_at": null
}
```

<aside class="notice">
    Folder names will be automatically titleized, e.g. "folder 1" becomes "Folder 1"
</aside>

This endpoint creates a new folder.

### HTTP Request

`POST /projects/<Project ID>/folders`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the folder's project

## Update Folder

```http
PATCH /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/folders/92371c34-4393-4a72-ab5e-5dd9b17c0f00 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{ "name": "updated folder" }
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "created_at": "2014-06-17T00:40:11.000Z",
    "updated_at": "2014-06-17T00:40:11.000Z",
    "device_created_at": "2014-06-17T00:40:11.000Z",
    "device_updated_at": "2014-06-17T00:40:11.000Z",
    "resolved_conflict": false,
    "id": "d426dce3-1b5f-446c-9ba2-7fd8e5781db5",
    "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
    "name": "updated folder",
    "deleted_at": null
}
```

This endpoint updates a specific folder.

### HTTP Request

`PATCH /projects/<Project ID>/folders/<Folder ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the folder's project
Folder ID | The ID of the folder to retrieve

## Delete Folder

```http
DELETE /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/folders/75d68ca1-0fc1-456a-bd9d-8b23875ac540 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 204 OK
Content-Type: application/json
```

This endpoint deletes a folder.

### HTTP Request

`DELETE /projects/<Project ID>/folders/<Folder ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the folder's project
Folder ID | The ID of the folder to retrieve
