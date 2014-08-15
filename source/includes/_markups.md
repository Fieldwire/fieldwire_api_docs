# Markups

## Markup Fields

Field | Description
--------- | -----------
project_id | Project ID markup belongs to
sheet_id | Sheet ID markup belongs to
name | Name of the markup
creator_user_id | User ID of the markup's creator
last_editor_user_id | User ID of the markup's last editor
data | [GeoJSON of markup](#markup-data)

## Get Markups

```http
GET /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/markups HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
    {
        "created_at": "2014-06-16T18:55:17.000Z",
        "updated_at": "2014-06-16T18:56:01.000Z",
        "device_created_at": "2014-06-16T18:55:17.000Z",
        "device_updated_at": "2014-06-16T18:56:02.000Z",
        "resolved_conflict": false,
        "id": "692fb74a-9c65-4a65-8e72-57f8dac0147c",
        "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
        "sheet_id": "a93f75ad-a90c-4f7c-8b4a-1432bdddc8f1",
        "creator_user_id": 1,
        "last_editor_user_id": 1,
        "data": {
            "type": "Feature",
            "properties": {
                "style": "text",
                "description": "line 1\nline 2\nline 3",
                "fontSize": 8
            },
            "geometry": {
                "type": "Polygon",
                "coordinates": [
                    [
                        1661,
                        394
                    ],
                    [
                        1991,
                        394
                    ],
                    [
                        1991,
                        614
                    ],
                    [
                        1661,
                        614
                    ]
                ]
            }
        },
        "deleted_at": null
    },
    {
        "created_at": "2014-06-16T18:53:31.000Z",
        "updated_at": "2014-06-16T18:56:35.000Z",
        "device_created_at": "2014-06-16T18:53:31.000Z",
        "device_updated_at": "2014-06-16T18:56:35.000Z",
        "resolved_conflict": false,
        "id": "44a63a50-281b-4b7c-9889-cf9a48bc65f3",
        "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
        "sheet_id": "a93f75ad-a90c-4f7c-8b4a-1432bdddc8f1",
        "creator_user_id": 1,
        "last_editor_user_id": 1,
        "data": {
            "type": "Feature",
            "properties": {
                "style": "cloud",
                "arcRadius": 8
            },
            "geometry": {
                "type": "Polygon",
                "coordinates": [
                    [
                        240,
                        139
                    ],
                    [
                        1136,
                        139
                    ],
                    [
                        1136,
                        323
                    ],
                    [
                        240,
                        323
                    ]
                ]
            }
        },
        "deleted_at": null
    }
]
```

This endpoint retrieves all markups.

### HTTP Request

`GET /projects/<Project ID>/markups`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the project to retrieve

## Managing Markups

<aside class="warning">
    Fieldwire API does not currently support managing markups.
</aside>

<aside class="notice">
    <a href='https://console.fieldwire.net'>Log In</a> to manage markups.
</aside>
