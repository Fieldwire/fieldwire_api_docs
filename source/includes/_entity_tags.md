# EntityTags

## EntityTag Fields

Field | Description | Type | Non-null? | Editable? | Default
--------- | --------- | --------- | --------- | --------- | ---------
project_id | Project ID entity_tag belongs to | UUID | x | |
name | Name of the entity_tag | String | x | x |
creator_user_id | User ID of the entity_tag's creator | x | |
last_editor_user_id | User ID of the entity_tag's last editor | x | |

<aside class="warning">
    Entity Tag names are unique per project
</aside>

## Get EntityTags

```http
GET /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/entity_tags HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
    {
        "id": "70ce3ccf-548a-49ff-9630-2978195d6d98",
        "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
        "creator_user_id": 2,
        "last_editor_user_id": 2,
        "created_at": "2018-04-03T22:57:57.760Z",
        "updated_at": "2018-04-03T22:57:57.762Z",
        "device_created_at": "2018-04-03T22:57:57.760Z",
        "device_updated_at": "2018-04-03T22:57:57.760Z",
        "resolved_conflict": false,
        "deleted_at": null,
        "name": "punch"
    },
    {
        "id": "ba19cc8b-bee2-47f8-8895-afccd9b6aa5a",
        "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
        "creator_user_id": 2,
        "last_editor_user_id": 2,
        "created_at": "2018-04-03T22:57:58.060Z",
        "updated_at": "2018-04-03T22:57:58.061Z",
        "device_created_at": "2018-04-03T22:57:58.059Z",
        "device_updated_at": "2018-04-03T22:57:58.059Z",
        "resolved_conflict": false,
        "deleted_at": null,
        "name": "change_order"
    }
]
```

This endpoint retrieves all entity_tags.

### HTTP Request

`GET /projects/<Project ID>/entity_tags`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the project to retrieve

## Get EntityTag

```http
GET /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/entity_tags/70ce3ccf-548a-49ff-9630-2978195d6d98 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "id": "70ce3ccf-548a-49ff-9630-2978195d6d98",
    "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
    "creator_user_id": 2,
    "last_editor_user_id": 2,
    "created_at": "2018-04-03T22:57:57.760Z",
    "updated_at": "2018-04-03T22:57:57.762Z",
    "device_created_at": "2018-04-03T22:57:57.760Z",
    "device_updated_at": "2018-04-03T22:57:57.760Z",
    "resolved_conflict": false,
    "deleted_at": null,
    "name": "punch"
}
```

This endpoint retrieves a specific entity_tag.

### HTTP Request

`GET /projects/<Project ID>/entity_tags/<EntityTag ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the entity_tag's project
EntityTag ID | The ID of the entity_tag to retrieve

## Post EntityTag

```http
POST /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/entity_tags HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{
    "name": "punch"
}
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "id": "70ce3ccf-548a-49ff-9630-2978195d6d98",
    "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
    "creator_user_id": 2,
    "last_editor_user_id": 2,
    "created_at": "2018-04-03T22:57:57.760Z",
    "updated_at": "2018-04-03T22:57:57.762Z",
    "device_created_at": "2018-04-03T22:57:57.760Z",
    "device_updated_at": "2018-04-03T22:57:57.760Z",
    "resolved_conflict": false,
    "deleted_at": null,
    "name": "punch"
}
```

This endpoint creates a new entity_tag.

### HTTP Request

`POST /projects/<Project ID>/entity_tags`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the entity_tag's project

## Update EntityTag

```http
PATCH /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/entity_tags/70ce3ccf-548a-49ff-9630-2978195d6d98 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{ "name": "updated" }
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "id": "70ce3ccf-548a-49ff-9630-2978195d6d98",
    "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
    "creator_user_id": 2,
    "last_editor_user_id": 2,
    "created_at": "2018-04-03T22:57:57.760Z",
    "updated_at": "2018-04-03T22:57:57.762Z",
    "device_created_at": "2018-04-03T22:57:57.760Z",
    "device_updated_at": "2018-04-03T22:57:57.760Z",
    "resolved_conflict": false,
    "deleted_at": null,
    "name": "updated"
}
```

This endpoint updates a specific entity_tag.

### HTTP Request

`PATCH /projects/<Project ID>/entity_tags/<EntityTag ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the entity_tag's project
EntityTag ID | The ID of the entity_tag to retrieve

## Delete EntityTag

```http
DELETE /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/entity_tags/75d68ca1-0fc1-456a-bd9d-8b23875ac540 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 204 OK
Content-Type: application/json
```

This endpoint deletes a entity_tag.

### HTTP Request

`DELETE /projects/<Project ID>/entity_tags/<EntityTag ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the entity_tag's project
EntityTag ID | The ID of the entity_tag to retrieve