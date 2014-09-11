# MultiHyperlinks

## MultiHyperlink Fields

Field | Description
--------- | -----------
project_id | Project ID multi_hyperlink belongs to
sheet_id | Sheet ID multi_hyperlink belongs to
creator_user_id | User ID of the multi_hyperlink's creator
last_editor_user_id | User ID of the multi_hyperlink's last editor
pos_x | Horizontal pixels (from left of floorplan) of multi_hyperlink's center
pos_y | Vertical pixels (from top of floorplan) of multi_hyperlink's center


## Get MultiHyperlinks

```http
GET /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/multi_hyperlinks HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
    {
        "created_at": "2014-09-10T21:33:20.000Z",
        "updated_at": "2014-09-10T21:33:20.000Z",
        "device_created_at": "2014-09-10T21:33:20.000Z",
        "device_updated_at": "2014-09-10T21:33:20.000Z",
        "resolved_conflict": false,
        "id": "92371c34-4393-4a72-ab5e-5dd9b17c0f00",
        "project_id": "2135d73e-257c-495b-99db-71bf5221c31e",
        "sheet_id": "b905934f-30d4-42e9-aa4e-dfdc3d9e62a3",
        "creator_user_id": 1,
        "last_editor_user_id": 1,
        "pos_x": 966,
        "pos_y": 201,
        "deleted_at": null,
        "attachment_ids": []
    },
    {
        "created_at": "2014-09-10T21:37:32.000Z",
        "updated_at": "2014-09-10T21:46:31.000Z",
        "device_created_at": "2014-09-10T21:37:32.000Z",
        "device_updated_at": "2014-09-10T21:46:31.000Z",
        "resolved_conflict": false,
        "id": "4216e08f-5f28-4da7-b8fd-a9a2dce3d1ea",
        "project_id": "2135d73e-257c-495b-99db-71bf5221c31e",
        "sheet_id": "b905934f-30d4-42e9-aa4e-dfdc3d9e62a3",
        "creator_user_id": 1,
        "last_editor_user_id": 1,
        "pos_x": 1837,
        "pos_y": 568,
        "deleted_at": null,
        "attachment_ids": [
            "86639e3c-8849-4db4-8d3f-0647d58268ad",
            "14e3aff5-28ac-45a5-baae-3b9a809a3e41"
        ]
    }
]
```

This endpoint retrieves all multi_hyperlinks.

### HTTP Request

`GET /projects/<Project ID>/multi_hyperlinks`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the project to retrieve

## Post MultiHyperlink

```http
POST /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/sheet/a5056209-4430-4407-a300-5dfcc4114993/multi_hyperlinks HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{
    "multi_hyperlink": {
        "pos_x": 966,
        "pos_y": 201
    }
}
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "created_at": "2014-09-10T21:33:20.000Z",
    "updated_at": "2014-09-10T21:33:20.000Z",
    "device_created_at": "2014-09-10T21:33:20.000Z",
    "device_updated_at": "2014-09-10T21:33:20.000Z",
    "resolved_conflict": false,
    "id": "92371c34-4393-4a72-ab5e-5dd9b17c0f00",
    "project_id": "2135d73e-257c-495b-99db-71bf5221c31e",
    "sheet_id": "b905934f-30d4-42e9-aa4e-dfdc3d9e62a3",
    "creator_user_id": 1,
    "last_editor_user_id": 1,
    "pos_x": 966,
    "pos_y": 201,
    "deleted_at": null,
    "attachment_ids": []
}
```

This endpoint creates a new multi_hyperlink.

### HTTP Request

`POST /projects/<Project ID>/sheets/<Sheet ID>/multi_hyperlinks`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the multi_hyperlink's project
Sheet ID | The ID of the multi_hyperlink's sheet

## Update MultiHyperlink

```http
PATCH /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/multi_hyperlinks/92371c34-4393-4a72-ab5e-5dd9b17c0f00 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{
    "multi_hyperlink": {
        "pos_x": 1966,
        "pos_y": 1201
    }
}
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "created_at": "2014-09-10T21:33:20.000Z",
    "updated_at": "2014-09-10T21:33:20.000Z",
    "device_created_at": "2014-09-10T21:33:20.000Z",
    "device_updated_at": "2014-09-10T21:33:20.000Z",
    "resolved_conflict": false,
    "id": "92371c34-4393-4a72-ab5e-5dd9b17c0f00",
    "project_id": "2135d73e-257c-495b-99db-71bf5221c31e",
    "sheet_id": "b905934f-30d4-42e9-aa4e-dfdc3d9e62a3",
    "creator_user_id": 1,
    "last_editor_user_id": 1,
    "pos_x": 1966,
    "pos_y": 1201,
    "deleted_at": null,
    "attachment_ids": []
}
```

This endpoint updates a specific multi_hyperlink.

### HTTP Request

`PATCH /projects/<Project ID>/multi_hyperlinks/<MultiHyperlink ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the multi_hyperlink's project
MultiHyperlink ID | The ID of the multi_hyperlink to retrieve

## Delete MultiHyperlink

```http
DELETE /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/multi_hyperlinks/75d68ca1-0fc1-456a-bd9d-8b23875ac540 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 204 OK
Content-Type: application/json
```

This endpoint deletes a multi_hyperlink.

### HTTP Request

`DELETE /projects/<Project ID>/multi_hyperlinks/<MultiHyperlink ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the multi_hyperlink's project
MultiHyperlink ID | The ID of the multi_hyperlink to retrieve

## Post Attachment

```http
POST /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/multi_hyperlinks/92371c34-4393-4a72-ab5e-5dd9b17c0f00/attachments HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{
    "attachment": {
        "name": "attachment 1",
        "thumb_url": "http://example.com/attachment1-thumb.jpeg",
        "file_url": "http://example.com/attachment1.jpeg",
        "file_size": 736623
    }
}
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "created_at": "2014-09-11T18:06:35.747Z",
    "updated_at": "2014-09-11T18:06:35.747Z",
    "device_created_at": "2014-09-11T18:06:35.747Z",
    "device_updated_at": "2014-09-11T18:06:35.747Z",
    "resolved_conflict": false,
    "id": "941394d5-7143-40e7-a503-0cc3b0bd13f2",
    "project_id": "2135d73e-257c-495b-99db-71bf5221c31e",
    "creator_user_id": 1,
    "name": "attachment 1",
    "thumb_url": "http://example.com/attachment1-thumb.jpeg",
    "file_url": "http://example.com/attachment1.jpeg",
    "file_size": 736623,
    "deleted_at": null
}
```

This endpoint creates a new attachment and adds it to the multi_hyperlink.

### HTTP Request

`POST /projects/<Project ID>/multi_hyperlinks/<MultiHyperlink ID>/attachments`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the multi_hyperlink's project
MultiHyperlink ID | The ID of the multi_hyperlink to retrieve

<aside class="warning">
    thumb_url is required for attachments on MultiHyperlinks
</aside>

## Delete Attachment

```http
DELETE /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/multi_hyperlinks/75d68ca1-0fc1-456a-bd9d-8b23875ac540/attachments/941394d5-7143-40e7-a503-0cc3b0bd13f2 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 204 OK
Content-Type: application/json
```

This endpoint deletes an attachment from a multi_hyperlink.

### HTTP Request

`DELETE /projects/<Project ID>/multi_hyperlinks/<MultiHyperlink ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the multi_hyperlink's project
MultiHyperlink ID | The ID of the multi_hyperlink to retrieve
Attachment ID | The ID of the attachment to retrieve