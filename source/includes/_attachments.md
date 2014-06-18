# Attachments

## Attachment Fields

Field | Description
--------- | -----------
project_id | Project ID attachment belongs to
name | Name of the attachment
creator_user_id | User ID of the attachment's creator
thumb_url | Url of the attachment thumb (optional)
file_url | Url of the attachment
file_size | Size of the attachment

## Get Attachments

```shell
curl "https://console.fieldwire.net/api/v1/projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/attachments" \
  -H "Authorization: Token api=[api token]>,project=[project token]"
```

> The above command returns JSON structured like this:

```json
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
        "creator_user_id": 1,
        "name": "attachment 2",
        "thumb_url": null,
        "file_url": "http://example.com/attachment2.jpeg",
        "file_size": 736623,
        "deleted_at": null
    }
]
```

This endpoint retrieves all attachments.

### HTTP Request

`GET https://console.fieldwire.net/api/v1/projects/<Project ID>/attachments`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the project to retrieve

## Managing Attachments

<aside class="warning">
    Fieldwire API does not currently support managing attachments.
</aside>

<aside class="notice">
    <a href='https://console.fieldwire.net'>Log In</a> to manage attachments.
</aside>
