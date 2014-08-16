# Hyperlinks

## Hyperlink Fields

Field | Description
--------- | -----------
project_id | Project ID hyperlink belongs to
sheet_id | Sheet ID hyperlink belongs to
creator_user_id | User ID of the hyperlink's creator
last_editor_user_id | User ID of the hyperlink's last editor
description | Hyperlink description that appears on floorplan
pos_x | Horizontal pixels (from left of floorplan) of hyperlink's center
pos_y | Vertical pixels (from top of floorplan) of hyperlink's center
floorplan_id | ID of linked floorplan
attachment_id | ID of linked attachment

<aside class="notice">
    Hyperlinks can link to either floorplans or attachments but not both
</aside>

<aside class="notice">
    Hyperlink cannot link to the same floorplan as it's sheet's floorplan
</aside>

## Get Hyperlinks

```http
GET /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/hyperlinks HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
    {
        "created_at": "2014-06-16T18:55:07.000Z",
        "updated_at": "2014-06-16T19:01:03.000Z",
        "device_created_at": "2014-06-16T18:55:07.000Z",
        "device_updated_at": "2014-06-16T19:01:03.000Z",
        "resolved_conflict": false,
        "id": "6757d318-d81d-463e-a8e4-9ae001112e59",
        "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
        "sheet_id": "a93f75ad-a90c-4f7c-8b4a-1432bdddc8f1",
        "creator_user_id": 1,
        "last_editor_user_id": 1,
        "description": "Hyperlink #1",
        "pos_x": 1246,
        "pos_y": 108,
        "floorplan_id": null,
        "attachment_id": "2bd071a9-81a0-4ada-8ecf-ababb78f4ac3",
        "deleted_at": null
    },
    {
        "created_at": "2014-06-16T23:41:49.000Z",
        "updated_at": "2014-06-16T23:41:49.000Z",
        "device_created_at": "2014-06-16T23:41:49.000Z",
        "device_updated_at": "2014-06-16T23:41:49.000Z",
        "resolved_conflict": false,
        "id": "84055918-9efb-4c2d-bd9c-33e10e896665",
        "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
        "sheet_id": "a5056209-4430-4407-a300-5dfcc4114993",
        "creator_user_id": 1,
        "last_editor_user_id": 1,
        "description": "Hyperlink #2",
        "pos_x": 215,
        "pos_y": 118,
        "floorplan_id": "20b57726-31ed-40f4-a608-ef29bc74b657",
        "attachment_id": null,
        "deleted_at": null
    }
]
```

This endpoint retrieves all hyperlinks.

### HTTP Request

`GET /projects/<Project ID>/hyperlinks`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the project to retrieve

## Post Hyperlink

```http
POST /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/sheet/a5056209-4430-4407-a300-5dfcc4114993/hyperlinks HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{
    "hyperlink": {
        "description": "Hyperlink #1",
        "pos_x": 215,
        "pos_y": 118,
        "floorplan_id": "20b57726-31ed-40f4-a608-ef29bc74b657"
    }
}
```
> or

```json
{
    "hyperlink": {
        "description": "Hyperlink #1",
        "pos_x": 215,
        "pos_y": 118,
        "attachment_id": "2bd071a9-81a0-4ada-8ecf-ababb78f4ac3"
    }
}
```

> or

```json
{
    "hyperlink": {
        "description": "Hyperlink #1",
        "pos_x": 215,
        "pos_y": 118,
        "attachment": {
            "name": "attachment 1",
            "thumb_url": "http://example.com/attachment1-thumb.jpeg",
            "file_url": "http://example.com/attachment1.jpeg",
            "file_size": 736623
        }
    }
}
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "created_at": "2014-06-16T18:55:07.000Z",
    "updated_at": "2014-06-16T19:01:03.000Z",
    "device_created_at": "2014-06-16T18:55:07.000Z",
    "device_updated_at": "2014-06-16T19:01:03.000Z",
    "resolved_conflict": false,
    "id": "6757d318-d81d-463e-a8e4-9ae001112e59",
    "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
    "sheet_id": "a93f75ad-a90c-4f7c-8b4a-1432bdddc8f1",
    "creator_user_id": 1,
    "last_editor_user_id": 1,
    "description": "Hyperlink #1",
    "pos_x": 1246,
    "pos_y": 108,
    "floorplan_id": null,
    "attachment_id": "2bd071a9-81a0-4ada-8ecf-ababb78f4ac3",
    "deleted_at": null
}
```

This endpoint creates a new hyperlink.

Hyperlinks can be created linking to an existing floorplan or attachment, or alternatively you can create an [attachment](#attachment-fields) as part of the same request.

### HTTP Request

`POST /projects/<Project ID>/sheets/<Sheet ID>/hyperlinks`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the hyperlink's project
Sheet ID | The ID of the hyperlink's sheet

### Attachment Parameters

Parameter | Description
--------- | -----------
name | Name of attachment (usually file name)
file_url | Url of attachment
thumb_url | Url of attachment thumb (optional)
file_size | Size of attachment (max 5MB)


## Update Hyperlink

```http
PATCH /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/hyperlinks/6757d318-d81d-463e-a8e4-9ae001112e59 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{ "hyperlink": { "description": "Updated description" } }
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "created_at": "2014-06-16T18:55:07.000Z",
    "updated_at": "2014-06-16T19:01:03.000Z",
    "device_created_at": "2014-06-16T18:55:07.000Z",
    "device_updated_at": "2014-06-16T19:01:03.000Z",
    "resolved_conflict": false,
    "id": "6757d318-d81d-463e-a8e4-9ae001112e59",
    "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
    "sheet_id": "a93f75ad-a90c-4f7c-8b4a-1432bdddc8f1",
    "creator_user_id": 1,
    "last_editor_user_id": 1,
    "description": "Updated description",
    "pos_x": 1246,
    "pos_y": 108,
    "floorplan_id": null,
    "attachment_id": "2bd071a9-81a0-4ada-8ecf-ababb78f4ac3",
    "deleted_at": null
}
```

This endpoint updates a specific hyperlink.

Attachments can also be created during updates as describe in [Post Hyperlink](#post-hyperlink)

### HTTP Request

`PATCH /projects/<Project ID>/hyperlinks/<Hyperlink ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the hyperlink's project
Hyperlink ID | The ID of the hyperlink to retrieve

## Delete Hyperlink

```http
DELETE /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/hyperlinks/75d68ca1-0fc1-456a-bd9d-8b23875ac540 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 204 OK
Content-Type: application/json
```

This endpoint deletes a hyperlink.

### HTTP Request

`DELETE /projects/<Project ID>/hyperlinks/<Hyperlink ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the hyperlink's project
Hyperlink ID | The ID of the hyperlink to retrieve