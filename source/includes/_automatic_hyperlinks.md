# Automatic Hyperlinks

## Automatic Hyperlinks Fields

Field | Description | Type | Required? | Editable? | Default
--------- | --------- | --------- | --------- | --------- | ---------
project_id | Project ID automatic hyperlink belongs to | UUID | x | |
sheet_id | Sheet ID automatic hyperlink belongs to to | UUID | x | |
pos_x | Horizontal pixels (from left of floorplan) of automatic hyperlink's center to | Integer | x | | _generated_
pos_y | Vertical pixels (from top of floorplan) of automatic hyperlink's center to | Integer | x | | _generated_
radius | Radius in pixels of automatic hyperlink to | Integer | x | | _generated_
floorplan_id | ID of linked floorplan to | UUID | | x |

## Get Automatic Hyperlinks

```http
GET /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/automatic_hyperlinks HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
    {
        "created_at": "2014-07-17T00:50:53.000Z",
        "updated_at": "2014-07-17T00:50:53.000Z",
        "id": "07be953c-7d08-408a-8fc5-1e266fed8363",
        "project_id": "aa0635ec-f95c-4458-8f56-e82af3d3634f",
        "sheet_id": "5c007e3c-9a1a-42ad-9cdc-4e71e035c0ea",
        "pos_x": 885,
        "pos_y": 922,
        "floorplan_id": "88273c0f-4341-442b-b2f2-539bfe01b872",
        "radius": 14,
        "deleted_at": null
    },
    {
        "created_at": "2014-07-17T00:52:14.000Z",
        "updated_at": "2014-07-17T00:52:14.000Z",
        "id": "f1376368-d677-45d9-a77a-67963618cdcd",
        "project_id": "aa0635ec-f95c-4458-8f56-e82af3d3634f",
        "sheet_id": "05e5aec4-b6c8-4320-9258-b8743de41869",
        "pos_x": 1883,
        "pos_y": 119,
        "floorplan_id": "a7aab36c-0a2f-479e-a903-a8cd8c964db8",
        "radius": 25,
        "deleted_at": null
    }
]
```

This endpoint retrieves all automatic hyperlinks.

### HTTP Request

`GET /projects/<Project ID>/automatic_hyperlinks`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the project to retrieve

## Get AutomaticHyperlink

```http
GET /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/automatic_hyperlinks/fa1fe4df-39ad-42e6-b11a-af7f2b97cf75 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "created_at": "2014-07-17T00:50:53.000Z",
    "updated_at": "2014-07-17T00:50:53.000Z",
    "id": "fa1fe4df-39ad-42e6-b11a-af7f2b97cf75w",
    "project_id": "aa0635ec-f95c-4458-8f56-e82af3d3634f",
    "sheet_id": "5c007e3c-9a1a-42ad-9cdc-4e71e035c0ea",
    "pos_x": 885,
    "pos_y": 922,
    "floorplan_id": "88273c0f-4341-442b-b2f2-539bfe01b872",
    "radius": 14,
    "deleted_at": null
}
```

This endpoint retrieves a specific automatic_hyperlink.

### HTTP Request

`GET /projects/<Project ID>/automatic_hyperlinks/<AutomaticHyperlink ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the automatic_hyperlink's project
AutomaticHyperlink ID | The ID of the automatic_hyperlink to retrieve

## Managing Automatic Hyperlinks

<aside class="warning">
    Fieldwire API creates automatic hyperlinks based off plan PDF data and naming
</aside>
