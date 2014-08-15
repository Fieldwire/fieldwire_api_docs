# Floorplans

## Floorplan Fields

Field | Description
--------- | -----------
name | Name of the floorplan
is_auto_versioning | Indicates if the floorplan has automatic versioning
sheets | Array of sheets as described below

## Sheet Fields

Field | Description
--------- | -----------
project_id | Project ID floorplan belongs to
floorplan_id | Floorplan ID sheet belongs to
name | Name of the sheet
version | Version of the sheet
file_url | Url of the low resolution floorplan
thumb_url | Url of the floorplan thumb
is_tiled | Indicates if floorplan is tiled.
file_width | Width of the resized floorplan
file_height | Height of the resized floorplan
original_width | Width of the original floorplan
original_height | Height of the original floorplan
has_conflicts | Indicates if this version conflicts with the previous versions
has_errors | Indicates if this version had errors processing
tile_size | Tile size of the floorplan if tiled

## Get Floorplans

```http
GET /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/floorplans HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
    {
        "created_at": "2014-04-30T19:02:13.000Z",
        "updated_at": "2014-04-30T19:02:13.000Z",
        "id": "d94f128b-d5a0-4325-95d8-32457af9ab3b",
        "name": "Harrison Ceiling",
        "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
        "is_auto_versioning": false,
        "deleted_at": null,
        "sheets": [
            {
                "created_at": "2014-04-30T19:02:13.000Z",
                "updated_at": "2014-04-30T19:02:13.000Z",
                "id": "4debfdec-30b6-4777-81a9-bbe63b9e6b55",
                "name": "Harrison Ceiling.gif",
                "version": 1,
                "file_url": "Harrison Ceiling",
                "thumb_url": "Harrison Ceiling-thumb.jpeg",
                "is_tiled": false,
                "floorplan_id": "d94f128b-d5a0-4325-95d8-32457af9ab3b",
                "file_width": 2048,
                "file_height": 1324,
                "original_width": 2048,
                "original_height": 1324,
                "has_conflicts": false,
                "has_errors": false,
                "tile_size": null,
                "deleted_at": null
            }
        ]
    },
    {
        "created_at": "2014-04-30T19:02:13.000Z",
        "updated_at": "2014-04-30T19:02:13.000Z",
        "id": "272d5ecf-3821-4a32-9891-b215573383f2",
        "name": "Harrison Floor",
        "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
        "is_auto_versioning": false,
        "deleted_at": null,
        "sheets": [
            {
                "created_at": "2014-04-30T19:02:13.000Z",
                "updated_at": "2014-04-30T19:02:13.000Z",
                "id": "9c1d2a95-2216-4235-9cad-60448f9c954c",
                "name": "Harrison Floor.gif",
                "version": 1,
                "file_url": "Harrison Floor.jpeg",
                "thumb_url": "Harrison Floor-thumb.jpeg",
                "is_tiled": false,
                "floorplan_id": "272d5ecf-3821-4a32-9891-b215573383f2",
                "file_width": 2048,
                "file_height": 1324,
                "original_width": 2048,
                "original_height": 1324,
                "has_conflicts": false,
                "has_errors": false,
                "tile_size": null,
                "deleted_at": null
            }
        ]
    }
]
```

This endpoint retrieves all floorplans.

### HTTP Request

`GET /projects/<Project ID>/floorplans`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the project to retrieve

## Managing Floorplans

<aside class="warning">
    Fieldwire API does not currently support managing floorplans.
</aside>

<aside class="notice">
    <a href='https://console.fieldwire.net'>Log In</a> to manage floorplans.
</aside>
