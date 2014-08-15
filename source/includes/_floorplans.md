# Floorplans (Plans)

## Floorplan Fields

Field | Description
--------- | -----------
name | Name of the floorplan
is_auto_versioning | Indicates if the floorplan has automatic versioning
sheets | [Sheets](#sheets)

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
                "created_at": "2014-08-15T22:23:18.995Z",
                "updated_at": "2014-08-15T22:24:08.743Z",
                "id": "9f5ab19a-5813-47a9-a767-7319a4171c52",
                "name": "plan1.png",
                "file_name": "plan1.png",
                "version": 1,
                "file_url": "plan1.jpeg",
                "thumb_url": "plan-thumb.jpeg",
                "is_tiled": true,
                "floorplan_id": "9af615e2-c091-4235-ae8a-b94c73b8e4ca",
                "file_width": 2364,
                "file_height": 1689,
                "original_width": 4662,
                "original_height": 3330,
                "has_conflicts": false,
                "has_errors": false,
                "tile_size": 493,
                "name_crop_url": null,
                "user_id": 95,
                "page_number": null,
                "project_id": "37b9103e-e3eb-438f-8c38-5f2736a952dd",
                "android_file_url": "plan1-android.jpeg",
                "android_file_width": 2048,
                "android_file_height": 1463,
                "sheet_upload_id": null,
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
                "created_at": "2014-08-15T22:23:18.995Z",
                "updated_at": "2014-08-15T22:24:08.743Z",
                "id": "9f5ab19a-5813-47a9-a767-7319a4171c52",
                "name": "plan2.png",
                "file_name": "plan2.png",
                "version": 1,
                "file_url": "plan2.jpeg",
                "thumb_url": "plan-thumb.jpeg",
                "is_tiled": true,
                "floorplan_id": "9af615e2-c091-4235-ae8a-b94c73b8e4ca",
                "file_width": 2364,
                "file_height": 1689,
                "original_width": 4662,
                "original_height": 3330,
                "has_conflicts": false,
                "has_errors": false,
                "tile_size": 493,
                "name_crop_url": null,
                "user_id": 95,
                "page_number": null,
                "project_id": "37b9103e-e3eb-438f-8c38-5f2736a952dd",
                "android_file_url": "plan2-android.jpeg",
                "android_file_width": 2048,
                "android_file_height": 1463,
                "sheet_upload_id": null,
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

## Post Floorplan

```http
POST /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/floorplans HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{ "sheets": [ { "name": "A1.12.png", "original_url": "https://example.com/A1.12.png" } ] }
```

> The above command returns:

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "created_at": "2014-08-15T22:23:18.934Z",
    "updated_at": "2014-08-15T22:23:18.934Z",
    "id": "9af615e2-c091-4235-ae8a-b94c73b8e4ca",
    "name": "A1.12",
    "project_id": "37b9103e-e3eb-438f-8c38-5f2736a952dd",
    "is_auto_versioning": false,
    "deleted_at": null,
    "sheets": []
}
```

<aside class="notice">
    By default only processed sheets are returned, therefore when the floorplan is first created it will be returned with 0 sheets.
</aside>

This endpoint creates a new floorplan.

### HTTP Request

`POST /projects/<Project ID>/floorplans`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the floorplan's project

### Sheet Parameters

Parameter | Description
--------- | -----------
name | Sheet file name
original_url | Public url of sheet

## Update Floorplan

```http
PATCH /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/floorplans HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{ "floorplan": { "name": "Updated name" } }
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "created_at": "2014-08-15T22:23:18.934Z",
    "updated_at": "2014-08-15T22:50:45.777Z",
    "id": "9af615e2-c091-4235-ae8a-b94c73b8e4ca",
    "name": "Updated name",
    "project_id": "37b9103e-e3eb-438f-8c38-5f2736a952dd",
    "is_auto_versioning": false,
    "deleted_at": null,
    "sheets": []
}
```

This endpoint updates a floorplan.

### HTTP Request

`PATCH /projects/<Project ID>/floorplans/<Floorplan ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the floorplan's project
Floorplan ID | The ID of the floorplan

## Add Sheet

```http
PATCH /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/floorplans/75d68ca1-0fc1-456a-bd9d-8b23875ac540 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{ "sheets": [ { "name": "A1.12-V2.png", "original_url": "https://example.com/A1.12-V2.png" } ] }
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "created_at": "2014-08-15T22:23:18.934Z",
    "updated_at": "2014-08-15T22:24:08.746Z",
    "id": "9af615e2-c091-4235-ae8a-b94c73b8e4ca",
    "name": "A1.12",
    "project_id": "37b9103e-e3eb-438f-8c38-5f2736a952dd",
    "is_auto_versioning": false,
    "deleted_at": null,
    "sheets": [
        {
            "created_at": "2014-08-15T22:23:18.995Z",
            "updated_at": "2014-08-15T22:24:08.743Z",
            "id": "9f5ab19a-5813-47a9-a767-7319a4171c52",
            "name": "A1.12.png",
            "file_name": "A1.12.png",
            "version": 1,
            "file_url": "plan.jpeg",
            "thumb_url": "plan-thumb.jpeg",
            "is_tiled": true,
            "floorplan_id": "9af615e2-c091-4235-ae8a-b94c73b8e4ca",
            "file_width": 2364,
            "file_height": 1689,
            "original_width": 4662,
            "original_height": 3330,
            "has_conflicts": false,
            "has_errors": false,
            "tile_size": 493,
            "name_crop_url": null,
            "user_id": 95,
            "page_number": null,
            "project_id": "37b9103e-e3eb-438f-8c38-5f2736a952dd",
            "android_file_url": "plan-android.jpeg",
            "android_file_width": 2048,
            "android_file_height": 1463,
            "sheet_upload_id": null,
            "deleted_at": null
        }
    ]
}
```

<aside class="notice">
    By default only processed sheets are returned, therefore when the floorplan is updated only existing sheets are returned
</aside>


This endpoint adds a new sheet version to the floorplan.

### HTTP Request

`PATCH /projects/<Project ID>/floorplans/<Floorplan ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the floorplan's project
Floorplan ID | The ID of the floorplan

### Sheet Parameters

Parameter | Description
--------- | -----------
name | Sheet file name
original_url | Public url of sheet

## Rotate Sheet

```http
PUT /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/floorplans/9af615e2-c091-4235-ae8a-b94c73b8e4ca/rotate HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{ "rotate_degrees": 180 }
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "created_at": "2014-08-15T22:23:18.934Z",
    "updated_at": "2014-08-15T22:50:45.777Z",
    "id": "9af615e2-c091-4235-ae8a-b94c73b8e4ca",
    "name": "Updated name",
    "project_id": "37b9103e-e3eb-438f-8c38-5f2736a952dd",
    "is_auto_versioning": false,
    "deleted_at": null,
    "sheets": []
}
```

<aside class="notice">
    By default only processed sheets are returned, therefore when the floorplan is updated only existing sheets are returned
</aside>

This endpoint creates a new rotated sheet based off of the current sheet version of the floorplan.

<aside class="notice">
    Valid rotations: 90, 180, 270
</aside>

### HTTP Request

`PUT /projects/<Project ID>/floorplans/<Floorplan ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the floorplan's project
Floorplan ID | The ID of the floorplan

## Delete Floorplan

```http
DELETE /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/floorplans/75d68ca1-0fc1-456a-bd9d-8b23875ac540 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 204 OK
Content-Type: application/json
```

This endpoint deletes a floorplan.

### HTTP Request

`DELETE /projects/<Project ID>/floorplans/<Floorplan ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the floorplan's project
Floorplan ID | The ID of the floorplan to retrieve