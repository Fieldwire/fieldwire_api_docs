# Sheets

## Sheet Fields

Field | Description | Type | Non-null? | Editable? | Default
--------- | --------- | --------- | --------- | --------- | ---------
project_id | Project ID sheet belongs to | UUID | x | |
floorplan_id | Floorplan ID sheet belongs to| UUID | x | |
name | Name of the sheet | String | x | | _generated_
file_name | File name of sheet | String | x | | _generated_
version | Version of the sheet | Integer | x | x | _generated_
file_url | Url of the low resolution floorplan | String | | | _generated_
thumb_url | Url of the floorplan thumb | String | | | _generated_
is_tiled | Indicates if floorplan is tiled. | Boolean | | | _generated_
file_width | Width of the resized floorplan | Integer | | | _generated_
file_height | Height of the resized floorplan | Integer | | | _generated_
original_width | Width of the original floorplan | Integer | | | _generated_
original_height | Height of the original floorplan | Integer | | | _generated_
has_conflicts | Indicates if this version conflicts with the previous versions | Boolean | x | x | _generated_
has_errors | Indicates if this version had errors processing | Boolean | x | | _generated_
tile_size | Tile size of the floorplan if tiled | Integer | | | _generated_
name_crop_url | Url of plan corner (used to identify plan name) | String | | | _generated_
user_id | User ID of sheet creator | Integer | | | _generated_
page_number | Page number of sheet if created from multi-page PDF | Integer | | | _generated_
android_file_url | Url of the low resolution floorplan (used on Android devices with max resolution 2048) | String | | | _generated_
android_file_width | Width of the android file_url | Integer | | | _generated_
android_file_height | Height of the android file_url | Integer | | | _generated_
sheet_upload_id | ID of the Sheet Upload that created this sheet | UUID | x | |
inches_per_pixel | User calibrated conversion from pixels to inches | Integer | | x |
version_description | User defined name of sheet version | String | | x | _generated_
version_notes | User defined notes of sheet version | String | | x | _generated_
tiles_package_url | Url of zip archive containing all tiles | String | | | _generated_

## Get Sheets

```http
GET /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/sheets HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
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
  },
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
```

This endpoint retrieves all sheets.

### HTTP Request

`GET /projects/<Project ID>/sheets`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the project to retrieve

## Resolve Conflict

```http
PATCH /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/sheets/9f5ab19a-5813-47a9-a767-7319a4171c52 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{ "sheet": { "has_conflicts": false } }
```

> The above command returns:

```http
HTTP/1.1 204 OK
Content-Type: application/json

```

This endpoint resolves a sheet conflict. Any tasks, markups, and hyperlinks will automatically be positioned and migrated to the resolved sheet.

### HTTP Request

`PATCH /projects/<Project ID>/sheets/<Sheet ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the sheet's project
Sheet ID | The ID of the sheet

## Delete Sheet

```http
DELETE /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/sheets/75d68ca1-0fc1-456a-bd9d-8b23875ac540 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 204 OK
Content-Type: application/json
```

This endpoint deletes a sheet.

### HTTP Request

`DELETE /projects/<Project ID>/sheets/<Sheet ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the sheet's project
Sheet ID | The ID of the sheet to retrieve