# Sheets

## Sheet Fields

Field | Description
--------- | -----------
project_id | Project ID floorplan belongs to
floorplan_id | Floorplan ID sheet belongs to
name | Name of the sheet
file_name | File name of sheet
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
name_crop_url | Url of plan corner (used to identify plan name)
user_id | User ID of sheet creator
page_number | Page number of sheet if created from multi-page PDF
android_file_url | Url of the low resolution floorplan (used on Android devices with max resolution 2048)
android_file_width | Width of the android file_url
android_file_height | Height of the android file_url
sheet_upload_id | ID of the Sheet Upload that created this sheet
inches_per_pixel | User calibrated conversion from pixels to inches
version_name | User defined name of sheet version
description | User defined description of sheets


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