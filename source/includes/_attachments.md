# Attachments

## Attachment Fields

Field | Description | Type | Non-null? | Editable? | Default
--------- | --------- | --------- | --------- | --------- | ---------
project_id | Project ID attachment belongs to | UUID | x | |
name | Name of the attachment | String | x | x |
creator_user_id | User ID of the attachment's creator | Integer | x | | _generated_
thumb_url | Url of the attachment thumb (optional) | String | | x |
file_url | Url of the attachment | String | x | x |
file_size | Size of the attachment | Integer | | x |
kind | Kind of attachment ("file", "photo") | String | x | x | file
is_dynamic | Indicates if resource at file_url can change | Boolean | x | x | False
floorplan_ids | Floorplan IDs that hyperlink to this attachment | Array, integers | | |
multi_hyperlink_ids | MultiHyperlink IDs that link to this attachment | Array, integers | |

## Get Attachments

```http
GET /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/attachments HTTP/1.1
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
        "creator_user_id": 1,
        "name": "attachment 1",
        "thumb_url": null,
        "file_url": "http://example.com/attachment1.jpeg",
        "file_size": 736623,
        "deleted_at": null,
        "floorplan_ids": [],
        "multi_hyperlink_ids": []
    },
    {
        "created_at": "2014-06-17T00:44:18.000Z",
        "updated_at": "2014-06-17T00:44:18.000Z",
        "device_created_at": "2014-06-17T00:44:18.000Z",
        "device_updated_at": "2014-06-17T00:44:18.000Z",
        "resolved_conflict": false,
        "id": "8c0c87d3-603a-4dd5-ac64-f11dd3ac2cf9",
        "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
        "creator_user_id": 1,
        "name": "attachment 2",
        "thumb_url": null,
        "file_url": "http://example.com/attachment2.jpeg",
        "file_size": 736623,
        "deleted_at": null,
        "floorplan_ids": [],
        "multi_hyperlink_ids": []
    }
]
```

This endpoint retrieves all attachments.

### HTTP Request

`GET /projects/<Project ID>/attachments`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the project to retrieve

## Get Attachment

```http
GET /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/attachments/d426dce3-1b5f-446c-9ba2-7fd8e5781db5 HTTP/1.1
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
    "creator_user_id": 1,
    "name": "attachment 1",
    "thumb_url": null,
    "file_url": "http://example.com/attachment1.jpeg",
    "file_size": 736623,
    "deleted_at": null,
    "floorplan_ids": [],
    "multi_hyperlink_ids": []
}
```

This endpoint retrieves a specific attachment.

### HTTP Request

`GET /projects/<Project ID>/attachments/<Attachment ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the attachment's project
Attachment ID | The ID of the attachment to retrieve

## Post Attachment

<aside class="notice">
    Attachments can also be created through [hyperlinks](#post-hyperlink) or [multi-hyperlinks](#post-attachment)
</aside>

```http
POST /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/attachments HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{
    "name": "attachment 1",
    "thumb_url": null,
    "file_url": "http://example.com/attachment1.jpeg",
    "file_size": 736623
}
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
    "creator_user_id": 1,
    "name": "attachment 1",
    "thumb_url": null,
    "file_url": "http://example.com/attachment1.jpeg",
    "file_size": 736623,
    "deleted_at": null,
    "floorplan_ids": [],
    "multi_hyperlink_ids": []
}
```

This endpoint creates a new attachment.

### HTTP Request

`POST /projects/<Project ID>/attachments`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the attachment's project

## Update Attachment

```http
PATCH /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/attachments/92371c34-4393-4a72-ab5e-5dd9b17c0f00 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{
    "name": "updated attachment"
}
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
    "creator_user_id": 1,
    "name": "updated attachment",
    "thumb_url": null,
    "file_url": "http://example.com/attachment1.jpeg",
    "file_size": 736623,
    "deleted_at": null,
    "floorplan_ids": [],
    "multi_hyperlink_ids": []
}
```

This endpoint updates a specific attachment.

### HTTP Request

`PATCH /projects/<Project ID>/attachments/<Attachment ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the attachment's project
Attachment ID | The ID of the attachment to retrieve

## Delete Attachment

```http
DELETE /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/attachments/75d68ca1-0fc1-456a-bd9d-8b23875ac540 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 204 OK
Content-Type: application/json
```

This endpoint deletes a attachment.

### HTTP Request

`DELETE /projects/<Project ID>/attachments/<Attachment ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the attachment's project
Attachment ID | The ID of the attachment to retrieve
