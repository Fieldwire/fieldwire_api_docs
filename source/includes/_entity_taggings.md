# EntityTaggings

## EntityTagging Fields

Field | Description | Type | Non-null? | Editable? | Default
--------- | --------- | --------- | --------- | --------- | ---------
project_id | Project ID entity_tagging belongs to | UUID | x | |
entity_tag_id | EntityTag ID entity_tagging belongs to | UUID | x | x |
entity_id | Entity ID entity_tagging belongs to | UUID | x | x |
entity_type | One of 'Attachment', 'Floorplan', 'Task', 'Bubble' | String | x | x |
creator_user_id | User ID of the entity_tagging's creator | Integer | x | | _generated_
last_editor_user_id | User ID of the entity_tagging's last editor | Integer | x | | _generated_

<aside class="warning">
    Entity Tagging (entity_tag_id, entity_id) combinations are unique per project
</aside>

## Get EntityTaggings

```http
GET /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/entity_taggings HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
    {
        "id": "050b6db6-1d01-46cb-a573-16355a40f189",
        "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
        "creator_user_id": 2,
        "last_editor_user_id": 2,
        "created_at": "2018-04-03T22:57:57.868Z",
        "updated_at": "2018-04-03T22:57:57.870Z",
        "device_created_at": "2018-04-03T22:57:57.868Z",
        "device_updated_at": "2018-04-03T22:57:57.868Z",
        "resolved_conflict": false,
        "deleted_at": null,
        "entity_tag_id": "70ce3ccf-548a-49ff-9630-2978195d6d98",
        "entity_id": "b627cf06-7e5f-43ef-a7d7-03c2e4507f10",
        "entity_type": "Bubble"
    },
    {
        "id": "afc706e3-e9e8-4c34-953f-7eb3cecd9af6",
        "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
        "creator_user_id": 2,
        "last_editor_user_id": 2,
        "created_at": "2018-04-03T22:57:58.103Z",
        "updated_at": "2018-04-03T22:57:58.106Z",
        "device_created_at": "2018-04-03T22:57:58.102Z",
        "device_updated_at": "2018-04-03T22:57:58.102Z",
        "resolved_conflict": false,
        "deleted_at": null,
        "entity_tag_id": "ba19cc8b-bee2-47f8-8895-afccd9b6aa5a",
        "entity_id": "5f968667-24ae-44bb-bef9-de026d6f06ff",
        "entity_type": "Bubble"
    }
]
```

This endpoint retrieves all entity_taggings.

### HTTP Request

`GET /projects/<Project ID>/entity_taggings`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the project to retrieve

## Get EntityTagging

```http
GET /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/entity_taggings/050b6db6-1d01-46cb-a573-16355a40f189 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "id": "050b6db6-1d01-46cb-a573-16355a40f189",
    "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
    "creator_user_id": 2,
    "last_editor_user_id": 2,
    "created_at": "2018-04-03T22:57:57.868Z",
    "updated_at": "2018-04-03T22:57:57.870Z",
    "device_created_at": "2018-04-03T22:57:57.868Z",
    "device_updated_at": "2018-04-03T22:57:57.868Z",
    "resolved_conflict": false,
    "deleted_at": null,
    "entity_tag_id": "70ce3ccf-548a-49ff-9630-2978195d6d98",
    "entity_id": "b627cf06-7e5f-43ef-a7d7-03c2e4507f10",
    "entity_type": "Bubble"
}
```

This endpoint retrieves a specific entity_tagging.

### HTTP Request

`GET /projects/<Project ID>/entity_taggings/<EntityTagging ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the entity_tagging's project
EntityTagging ID | The ID of the entity_tagging to retrieve

## Post EntityTagging

```http
POST /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/entity_taggings HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{
    "entity_tag_id": "70ce3ccf-548a-49ff-9630-2978195d6d98",
    "entity_id": "b627cf06-7e5f-43ef-a7d7-03c2e4507f10",
    "entity_type": "Bubble"
}
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "id": "050b6db6-1d01-46cb-a573-16355a40f189",
    "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
    "creator_user_id": 2,
    "last_editor_user_id": 2,
    "created_at": "2018-04-03T22:57:57.868Z",
    "updated_at": "2018-04-03T22:57:57.870Z",
    "device_created_at": "2018-04-03T22:57:57.868Z",
    "device_updated_at": "2018-04-03T22:57:57.868Z",
    "resolved_conflict": false,
    "deleted_at": null,
    "entity_tag_id": "70ce3ccf-548a-49ff-9630-2978195d6d98",
    "entity_id": "b627cf06-7e5f-43ef-a7d7-03c2e4507f10",
    "entity_type": "Bubble"
}
```

> or if (entity_tag_id,entity_id) exists:

```http
HTTP/1.1 409 CONFLICT
Content-Type: application/json

{
    "id": "050b6db6-1d01-46cb-a573-16355a40f189",
    "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
    "creator_user_id": 2,
    "last_editor_user_id": 2,
    "created_at": "2018-04-03T22:57:57.868Z",
    "updated_at": "2018-04-03T22:57:57.870Z",
    "device_created_at": "2018-04-03T22:57:57.868Z",
    "device_updated_at": "2018-04-03T22:57:57.868Z",
    "resolved_conflict": false,
    "deleted_at": null,
    "entity_tag_id": "70ce3ccf-548a-49ff-9630-2978195d6d98",
    "entity_id": "b627cf06-7e5f-43ef-a7d7-03c2e4507f10",
    "entity_type": "Bubble"
}
```

This endpoint creates a new entity_tagging.

### HTTP Request

`POST /projects/<Project ID>/entity_taggings`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the entity_tagging's project


## Delete EntityTagging

```http
DELETE /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/entity_taggings/050b6db6-1d01-46cb-a573-16355a40f189 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 204 OK
Content-Type: application/json
```

This endpoint deletes a entity_tagging.

### HTTP Request

`DELETE /projects/<Project ID>/entity_taggings/<EntityTagging ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the entity_tagging's project
EntityTagging ID | The ID of the entity_tagging to retrieve