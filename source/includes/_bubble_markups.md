# Bubble Markups

## BubbleMarkup Fields

Field | Description
--------- | -----------
bubble_id | The ID of the bubble the markup belongs to
data | [GeoJSON of markup](#markup-data)

## Get BubbleMarkups

```http
GET /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/bubble_markups HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
  {
    "created_at": "2014-08-08T00:37:22.000Z",
    "updated_at": "2014-08-08T00:37:22.000Z",
    "device_created_at": "2014-08-08T00:37:22.000Z",
    "device_updated_at": "2014-08-08T00:37:22.000Z",
    "resolved_conflict": false,
    "id": "bd6054a2-a6b3-47ce-a6f4-47310086cd01",
    "bubble_id": "641c82f4-7129-45d3-af14-53656231eb4f",
    "data": {
      "type": "Feature",
      "properties": {
        "style": "text",
        "color": "#FF0000",
        "description": "text",
        "fontSize": 96
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [[152,98],[342,98],[342,229],[152,229]]
      }
    },
    "deleted_at": null
  },
  {
    "created_at": "2014-08-08T00:37:30.000Z",
    "updated_at": "2014-08-08T00:37:30.000Z",
    "device_created_at": "2014-08-08T00:37:30.000Z",
    "device_updated_at": "2014-08-08T00:37:30.000Z",
    "resolved_conflict": false,
    "id": "acc544c6-c7f8-443e-8a1b-e8f9776717f4",
    "bubble_id": "641c82f4-7129-45d3-af14-53656231eb4f",
    "data": {
      "type": "Feature",
      "properties": {
        "style": "drawing",
        "color": "#FF0000",
        "width": 40
      },
      "geometry": {
        "type": "LineString",
        "coordinates": [[563,374],[563,373] ...... [565,380],[563,380]]
      }
    },
    "deleted_at": null
  },
  {
    "created_at": "2014-08-08T00:37:33.000Z",
    "updated_at": "2014-08-08T00:37:33.000Z",
    "device_created_at": "2014-08-08T00:37:33.000Z",
    "device_updated_at": "2014-08-08T00:37:33.000Z",
    "resolved_conflict": false,
    "id": "7682aff0-b968-4cdd-9fb8-3911edc9e928",
    "bubble_id": "641c82f4-7129-45d3-af14-53656231eb4f",
    "data": {
      "type": "Feature",
      "properties": {
        "style": "rectangle",
        "color": "#FF0000",
        "width": 10
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [[362,62],[590,62],[590,244],[362,244]]
      }
    },
    "deleted_at": null
  },
  {
    "created_at": "2014-08-08T00:37:39.000Z",
    "updated_at": "2014-08-08T00:37:39.000Z",
    "device_created_at": "2014-08-08T00:37:39.000Z",
    "device_updated_at": "2014-08-08T00:37:39.000Z",
    "resolved_conflict": false,
    "id": "4aa59365-9a8e-4d0d-a3de-fdea137deff9",
    "bubble_id": "641c82f4-7129-45d3-af14-53656231eb4f",
    "data": {
      "type": "Feature",
      "properties": {
        "style": "arrow",
        "color": "#FF0000",
        "width": 5
      },
      "geometry": {
        "type": "LineString",
        "coordinates": [[56,399],[326,272]]
      }
    },
    "deleted_at": null
  }
]
```

This endpoint retrieves all bubble_markups.

### HTTP Requests

`GET /projects/<Project ID>/bubble_markups`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the project to retrieve

## Get BubbleMarkup

```http
GET /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/bubble_markups/29ca4ad0-a413-48aa-b8b8-28242d3cc205 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "created_at": "2014-08-08T00:37:22.000Z",
  "updated_at": "2014-08-08T00:37:22.000Z",
  "device_created_at": "2014-08-08T00:37:22.000Z",
  "device_updated_at": "2014-08-08T00:37:22.000Z",
  "resolved_conflict": false,
  "id": "bd6054a2-a6b3-47ce-a6f4-47310086cd01",
  "bubble_id": "641c82f4-7129-45d3-af14-53656231eb4f",
  "data": {
    "type": "Feature",
    "properties": {
      "style": "text",
      "color": "#FF0000",
      "description": "text",
      "fontSize": 96
    },
    "geometry": {
      "type": "Polygon",
      "coordinates": [[152,98],[342,98],[342,229],[152,229]]
    }
  },
  "deleted_at": null
}
```

This endpoint retrieves a specific bubble_markup.

### HTTP Request

`GET /projects/<Project ID>/bubble_markups/<BubbleMarkup ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the bubble_markup's project
BubbleMarkup ID | The ID of the bubble_markup to retrieve

## Post BubbleMarkup

```http
POST /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/bubble/75b86f78-0a94-42ea-9d58-a0f8fb5ed4bb/bubble_markups HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{
  "data": {
    "type": "Feature",
    "properties": {
      "style": "text",
      "color": "#FF0000",
      "description": "text",
      "fontSize": 96
    },
    "geometry": {
      "type": "Polygon",
      "coordinates": [[152,98],[342,98],[342,229],[152,229]]
    }
  }
}
```

> The above command returns:

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "created_at": "2014-08-08T00:37:22.000Z",
  "updated_at": "2014-08-08T00:37:22.000Z",
  "device_created_at": "2014-08-08T00:37:22.000Z",
  "device_updated_at": "2014-08-08T00:37:22.000Z",
  "resolved_conflict": false,
  "id": "bd6054a2-a6b3-47ce-a6f4-47310086cd01",
  "bubble_id": "641c82f4-7129-45d3-af14-53656231eb4f",
  "data": {
    "type": "Feature",
    "properties": {
      "style": "text",
      "color": "#FF0000",
      "description": "text",
      "fontSize": 96
    },
    "geometry": {
      "type": "Polygon",
      "coordinates": [[152,98],[342,98],[342,229],[152,229]]
    }
  },
  "deleted_at": null
}
```

This endpoint creates a new bubble_markup.

### HTTP Request

`POST /projects/<Project ID>/bubbles/<Bubble ID>/bubble_markups`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the bubble_markup's project
Bubble ID | The ID of the bubble_markup's bubble

## Update BubbleMarkup

```http
PATCH /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/bubble_markups/75d68ca1-0fc1-456a-bd9d-8b23875ac540 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{
  "data": {
    "type": "Feature",
    "properties": {
      "style": "text",
      "color": "#FF0000",
      "description": "text",
      "fontSize": 96
    },
    "geometry": {
      "type": "Polygon",
      "coordinates": [[152,98],[342,98],[342,229],[152,229]]
    }
  }
}
````

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "created_at": "2014-08-08T00:37:22.000Z",
  "updated_at": "2014-08-08T00:37:22.000Z",
  "device_created_at": "2014-08-08T00:37:22.000Z",
  "device_updated_at": "2014-08-08T00:37:22.000Z",
  "resolved_conflict": false,
  "id": "bd6054a2-a6b3-47ce-a6f4-47310086cd01",
  "bubble_id": "641c82f4-7129-45d3-af14-53656231eb4f",
  "data": {
    "type": "Feature",
    "properties": {
      "style": "text",
      "color": "#FF0000",
      "description": "text",
      "fontSize": 96
    },
    "geometry": {
      "type": "Polygon",
      "coordinates": [[152,98],[342,98],[342,229],[152,229]]
    }
  },
  "deleted_at": null
}
```

This endpoint updates a specific bubble_markup.

### HTTP Request

`PATCH /projects/<Project ID>/bubble_markups/<BubbleMarkup ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the bubble_markup's project
BubbleMarkup ID | The ID of the bubble_markup to retrieve

## Delete BubbleMarkup

```http
DELETE /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/bubble_markups/75d68ca1-0fc1-456a-bd9d-8b23875ac540 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 204 OK
Content-Type: application/json
```

This endpoint delete a specific bubble_markup.

### HTTP Request

`DELETE /projects/<Project ID>/bubble_markups/<BubbleMarkup ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the bubble_markup's project
BubbleMarkup ID | The ID of the bubble_markup to retrieve