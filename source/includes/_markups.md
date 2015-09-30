# Markups

## Markup Fields

Field | Description | Type | Non-null? | Editable? | Default
--------- | --------- | --------- | --------- | --------- | ---------
project_id | Project ID markup belongs to | UUID | x | |
sheet_id | Sheet ID markup belongs to | UUID | x | |
name | Name of the markup | String | x | x |
creator_user_id | User ID of the markup's creator | Integer | x | | _generated_
last_editor_user_id | User ID of the markup's last editor | Integer | x | | _generated_
data | [GeoJSON of markup](#markup-data) | JSON | x | x |

## Get Markups

```http
GET /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/markups HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
    {
        "created_at": "2014-06-16T18:55:17.000Z",
        "updated_at": "2014-06-16T18:56:01.000Z",
        "device_created_at": "2014-06-16T18:55:17.000Z",
        "device_updated_at": "2014-06-16T18:56:02.000Z",
        "resolved_conflict": false,
        "id": "692fb74a-9c65-4a65-8e72-57f8dac0147c",
        "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
        "sheet_id": "a93f75ad-a90c-4f7c-8b4a-1432bdddc8f1",
        "creator_user_id": 1,
        "last_editor_user_id": 1,
        "data": {
            "type": "Feature",
            "properties": {
                "style": "text",
                "description": "line 1\nline 2\nline 3",
                "fontSize": 32
            },
            "geometry": {
                "type": "Polygon",
                "coordinates": [[1661,394],[1991,394],[1991,614],[1661,614]]
            }
        },
        "deleted_at": null
    },
    {
        "created_at": "2014-06-16T18:53:31.000Z",
        "updated_at": "2014-06-16T18:56:35.000Z",
        "device_created_at": "2014-06-16T18:53:31.000Z",
        "device_updated_at": "2014-06-16T18:56:35.000Z",
        "resolved_conflict": false,
        "id": "44a63a50-281b-4b7c-9889-cf9a48bc65f3",
        "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
        "sheet_id": "a93f75ad-a90c-4f7c-8b4a-1432bdddc8f1",
        "creator_user_id": 1,
        "last_editor_user_id": 1,
        "data": {
            "type": "Feature",
            "properties": {
                "style": "cloud",
                "arcRadius": 16
            },
            "geometry": {
                "type": "Polygon",
                "coordinates": [[1661,394],[1991,394],[1991,614],[1661,614]]
            }
        },
        "deleted_at": null
    }
]
```

This endpoint retrieves all markups.

### HTTP Request

`GET /projects/<Project ID>/markups`

`GET /projects/<Project ID>/sheets/<Sheet ID>/markups`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the markup's project
Sheet ID | The ID of the markup's sheet

## Get Markup

```http
GET /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/markups/692fb74a-9c65-4a65-8e72-57f8dac0147c HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "created_at": "2014-06-16T18:55:17.000Z",
    "updated_at": "2014-06-16T18:56:01.000Z",
    "device_created_at": "2014-06-16T18:55:17.000Z",
    "device_updated_at": "2014-06-16T18:56:02.000Z",
    "resolved_conflict": false,
    "id": "692fb74a-9c65-4a65-8e72-57f8dac0147c",
    "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
    "sheet_id": "a93f75ad-a90c-4f7c-8b4a-1432bdddc8f1",
    "creator_user_id": 1,
    "last_editor_user_id": 1,
    "data": {
        "type": "Feature",
        "properties": {
            "style": "text",
            "description": "line 1\nline 2\nline 3",
            "fontSize": 32
        },
        "geometry": {
            "type": "Polygon",
            "coordinates": [[1661,394],[1991,394],[1991,614],[1661,614]]
        }
    },
    "deleted_at": null
}
```

This endpoint retrieves a specific markup.

### HTTP Request

`GET /projects/<Project ID>/markups/<Markup ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the markup's project
Markup ID | The ID of the markup to retrieve

## Post Markup

```http
POST /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/sheets/75b86f78-0a94-42ea-9d58-a0f8fb5ed4bb/markups HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{
    "data": {
        "type": "Feature",
        "properties": {
            "style": "text",
            "description": "line 1\nline 2\nline 3",
            "fontSize": 32
        },
        "geometry": {
            "type": "Polygon",
            "coordinates": [[1661,394],[1991,394],[1991,614],[1661,614]]
        }
    }
}
```

> The above command returns:

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "created_at": "2014-06-16T18:55:17.000Z",
    "updated_at": "2014-06-16T18:56:01.000Z",
    "device_created_at": "2014-06-16T18:55:17.000Z",
    "device_updated_at": "2014-06-16T18:56:02.000Z",
    "resolved_conflict": false,
    "id": "692fb74a-9c65-4a65-8e72-57f8dac0147c",
    "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
    "sheet_id": "a93f75ad-a90c-4f7c-8b4a-1432bdddc8f1",
    "creator_user_id": 1,
    "last_editor_user_id": 1,
    "data": {
        "type": "Feature",
        "properties": {
            "style": "text",
            "description": "line 1\nline 2\nline 3",
            "fontSize": 32
        },
        "geometry": {
            "type": "Polygon",
            "coordinates": [[1661,394],[1991,394],[1991,614],[1661,614]]
        }
    },
    "deleted_at": null
}
```

This endpoint creates a new markup.

### HTTP Request

`POST /projects/<Project ID>/sheets/<Sheet ID>/markups`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the markup's project
Sheet ID | The ID of the markup's sheet

## Update Markup

```http
PATCH /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/markups/75d68ca1-0fc1-456a-bd9d-8b23875ac540 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{
    "data": {
        "type": "Feature",
        "properties": {
            "style": "text",
            "description": "updated description",
            "fontSize": 32
        },
        "geometry": {
            "type": "Polygon",
            "coordinates": [[1661,394],[1991,394],[1991,614],[1661,614]]
        }
    }
}
````

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "created_at": "2014-06-16T18:55:17.000Z",
    "updated_at": "2014-06-16T18:56:01.000Z",
    "device_created_at": "2014-06-16T18:55:17.000Z",
    "device_updated_at": "2014-06-16T18:56:02.000Z",
    "resolved_conflict": false,
    "id": "692fb74a-9c65-4a65-8e72-57f8dac0147c",
    "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
    "sheet_id": "a93f75ad-a90c-4f7c-8b4a-1432bdddc8f1",
    "creator_user_id": 1,
    "last_editor_user_id": 1,
    "data": {
        "type": "Feature",
        "properties": {
            "style": "text",
            "description": "updated description",
            "fontSize": 32
        },
        "geometry": {
            "type": "Polygon",
            "coordinates": [[1661,394],[1991,394],[1991,614],[1661,614]]
        }
    },
    "deleted_at": null
}
```

This endpoint updates a specific markup.

### HTTP Request

`PATCH /projects/<Project ID>/markups/<Markup ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the markup's project
Markup ID | The ID of the markup to retrieve

## Delete Markup

```http
DELETE /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/markups/75d68ca1-0fc1-456a-bd9d-8b23875ac540 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 204 OK
Content-Type: application/json
```

This endpoint delete a specific markup.

### HTTP Request

`DELETE /projects/<Project ID>/markups/<Markup ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the markup's project
Markup ID | The ID of the markup to retrieve
