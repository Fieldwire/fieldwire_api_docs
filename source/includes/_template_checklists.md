# Template Checklists

## TemplateChecklist Fields

Field | Description | Type | Non-null? | Editable? | Default
--------- | --------- | --------- | --------- | --------- | ---------
project_id | Project ID the template_checklist belongs to | UUID | x | |
name | Name of template_checklist | String | x | x |
template_check_items | Array of [template_check_items](#templatecheckitems)

## Get TemplateChecklists

```http
GET /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/template_checklists HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
    {
        "created_at": "2014-07-08T23:45:19.000Z",
        "updated_at": "2014-07-08T23:47:22.000Z",
        "device_created_at": "2014-07-08T23:45:19.000Z",
        "device_updated_at": "2014-07-08T23:47:22.000Z",
        "resolved_conflict": false,
        "id": "aba2c9a1-da23-4e6d-a9b0-c20b8497a942",
        "name": "Template 1",
        "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
        "deleted_at": null,
        "template_check_items": [
            {
                "created_at": "2014-07-08T23:45:22.000Z",
                "updated_at": "2014-07-08T23:45:22.000Z",
                "device_created_at": "2014-07-08T23:45:22.000Z",
                "device_updated_at": "2014-07-08T23:45:22.000Z",
                "resolved_conflict": false,
                "id": "a71a2d49-6a5e-4a9a-81dd-1f463a95e52b",
                "name": "first",
                "deleted_at": null
            },
            {
                "created_at": "2014-07-08T23:45:24.000Z",
                "updated_at": "2014-07-08T23:45:24.000Z",
                "device_created_at": "2014-07-08T23:45:24.000Z",
                "device_updated_at": "2014-07-08T23:45:24.000Z",
                "resolved_conflict": false,
                "id": "fa6ff0d1-a066-4560-a73a-e55600a6f7a7",
                "name": "second",
                "deleted_at": null
            }
        ]
    },
    {
        "created_at": "2014-07-08T23:48:45.000Z",
        "updated_at": "2014-07-08T23:48:51.000Z",
        "device_created_at": "2014-07-08T23:48:45.000Z",
        "device_updated_at": "2014-07-08T23:48:51.000Z",
        "resolved_conflict": false,
        "id": "ebe0f608-7e89-4301-bb13-ffd9db05d60c",
        "name": "Template 2",
        "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
        "deleted_at": null,
        "template_check_items": []
    }
]
```

This endpoint retrieves all template_checklists.

### HTTP Requests

`GET /projects/<Project ID>/template_checklists`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the project to retrieve

## Get TemplateChecklist

```http
GET /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/template_checklists/29ca4ad0-a413-48aa-b8b8-28242d3cc205 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "created_at": "2014-07-08T23:48:45.000Z",
    "updated_at": "2014-07-08T23:48:51.000Z",
    "device_created_at": "2014-07-08T23:48:45.000Z",
    "device_updated_at": "2014-07-08T23:48:51.000Z",
    "resolved_conflict": false,
    "id": "ebe0f608-7e89-4301-bb13-ffd9db05d60c",
    "name": "Template 2",
    "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
    "deleted_at": null,
    "template_check_items": []
}
```

This endpoint retrieves a specific template_checklist.

### HTTP Request

`GET /projects/<Project ID>/template_checklists/<TemplateChecklist ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the template_checklist's project
TemplateChecklist ID | The ID of the template_checklist to retrieve

## Post TemplateChecklist

```http
POST /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/template_checklists HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{ "name": "Template 2" }
```

> The above command returns:

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "created_at": "2014-07-08T23:48:45.000Z",
    "updated_at": "2014-07-08T23:48:51.000Z",
    "device_created_at": "2014-07-08T23:48:45.000Z",
    "device_updated_at": "2014-07-08T23:48:51.000Z",
    "resolved_conflict": false,
    "id": "ebe0f608-7e89-4301-bb13-ffd9db05d60c",
    "name": "Template 2",
    "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
    "deleted_at": null,
    "template_check_items": []
}
```

This endpoint creates a new template_checklist.

### HTTP Request

`POST /projects/<Project ID>/template_checklists`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the template_checklist's project

## Update TemplateChecklist

```http
PATCH /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/template_checklists/75d68ca1-0fc1-456a-bd9d-8b23875ac540 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{ "name": "Updated template" }
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "created_at": "2014-07-08T23:48:45.000Z",
    "updated_at": "2014-07-08T23:48:51.000Z",
    "device_created_at": "2014-07-08T23:48:45.000Z",
    "device_updated_at": "2014-07-08T23:48:51.000Z",
    "resolved_conflict": false,
    "id": "ebe0f608-7e89-4301-bb13-ffd9db05d60c",
    "name": "Updated Template",
    "project_id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
    "deleted_at": null,
    "template_check_items": []
}
```

This endpoint updates a specific template_checklist.

### HTTP Request

`PATCH /projects/<Project ID>/template_checklists/<TemplateChecklist ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the template_checklist's project
TemplateChecklist ID | The ID of the template_checklist to retrieve

## Delete TemplateChecklist

```http
DELETE /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/template_checklists/75d68ca1-0fc1-456a-bd9d-8b23875ac540 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 204 OK
Content-Type: application/json
```

This endpoint deletes the template_checklist.

### HTTP Request

`DELETE /projects/<Project ID>/template_checklists/<TemplateChecklist ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the template_checklist's project
TemplateChecklist ID | The ID of the template_checklist to retrieve