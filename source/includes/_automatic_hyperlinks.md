# Automatic Hyperlinks

## Automatic Hyperlinks Fields

Field | Description
--------- | -----------
project_id | Project ID automatic hyperlink belongs to
sheet_id | Sheet ID automatic hyperlink belongs to
pos_x | Horizontal pixels (from left of floorplan) of automatic hyperlink's center
pos_y | Vertical pixels (from top of floorplan) of automatic hyperlink's center
radius | Radius in pixels of automatic hyperlink
floorplan_id | ID of linked floorplan

## Get Automatic Hyperlinks

```shell
curl "https://console.fieldwire.net/api/v2/projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/automatic_hyperlinks" \
  -H "Authorization: Token api=[api token]>,project=[project token]"
```

> The above command returns JSON structured like this:

```json
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

`GET https://console.fieldwire.net/api/v2/projects/<Project ID>/automatic_hyperlinks`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the project to retrieve

## Managing Automatic Hyperlinks

<aside class="warning">
    Fieldwire API creates automatic hyperlinks based off plan PDF data and naming
</aside>
