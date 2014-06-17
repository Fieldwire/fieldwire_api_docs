# Markups

## Markup Fields

Field | Description
--------- | -----------
name | Name of the markup
creator_user_id | User ID of the markup's creator
last_editor_user_id | User ID of the markup's last editor
data | GeoJSON of markup (see below)

## Get Markups

```shell
curl "https://console.fieldwire.net/api/v1/projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/markups" \
  -H "Authorization: Token api=[api token]>,project=[project token]"
```

> The above command returns JSON structured like this:

```json
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
                "font_size": 8
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
                "arc_radius": 8
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

`GET https://console.fieldwire.net/api/v1/projects/<Project ID>/markups`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the project to retrieve

## Markup data

Field | Description
--------- | -----------
type | Always "Feature"
properties | Contains markup specific data (style, description, etc.)
geometry | Describes markup shape

<aside class="notice">
    Polygon coordinates are [x,y] in clockwise order starting with top left corner
</aside>

<aside class="notice">
    <a href="http://geojson.org/geojson-spec.html">GeoJSON spec</a>
</aside>

## Cloud
```
{
    "data": {
        "type": "Feature",
        "properties": {
            "style": "cloud",
            "arc_radius": 8
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
    }
}
```

Property | Description
--------- | -----------
style | Always 'cloud'
arc_radius | Radius in pixels of each cloud arc
geometry | Describes markup shape

<aside class="notice">
    Polygon coordinates refer to the exact point where the arcs of the cloud should intersect
</aside>
<aside class="notice">
    Height and width of polygon must be evenly divisible by the arc radius
</aside>

## Text box

``` json
{
    "data": {
        "type": "Feature",
        "properties": {
            "style": "text",
            "description": "line 1\nline 2\nline 3",
            "font_size": 8
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
    }
}
```

Property | Description
--------- | -----------
style | Always 'text'
description | Text to be displayed (newlines marked with '\n')
font_size | Size of text in pixels

<aside class="notice">
    Polygon coordinates refer to the bounding box that contains the text (with 5 pixel padding in all directions)
</aside>
<aside class="notice">
    Text should not display outside box
</aside>

## Managing Markups

<aside class="warning">
    Fieldwire API does not currently support managing markups.
</aside>

<aside class="notice">
    <a href='https://console.fieldwire.net'>Log In</a> to manage markups.
</aside>
