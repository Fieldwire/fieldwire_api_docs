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

```shell
curl "https://console.fieldwire.net/api/v2/projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/hyperlinks" \
  -H "Authorization: Token api=[api token]>,project=[project token]"
```

> The above command returns JSON structured like this:

```json
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

`GET https://console.fieldwire.net/api/v2/projects/<Project ID>/hyperlinks`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the project to retrieve

## Managing Hyperlinks

<aside class="warning">
    Fieldwire API does not currently support managing hyperlinks.
</aside>

<aside class="notice">
    <a href='https://console.fieldwire.net'>Log In</a> to manage hyperlinks.
</aside>
