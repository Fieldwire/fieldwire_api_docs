# Template Check Items

## TemplateCheckItem Fields

Field | Description | Type | Non-null? | Editable? | Default
--------- | --------- | --------- | --------- | --------- | ---------
project_id | Project ID the template_check_item belongs to | UUID | x | |
name | Name of template_check_item | String | x | x |

## Post TemplateCheckItem

```http
POST /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/template_checklists/be0f608-7e89-4301-bb13-ffd9db05d60c/template_check_items HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{ "name": "First" }
```

> The above command returns:

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "created_at": "2014-07-08T23:45:22.000Z",
    "updated_at": "2014-07-08T23:45:22.000Z",
    "device_created_at": "2014-07-08T23:45:22.000Z",
    "device_updated_at": "2014-07-08T23:45:22.000Z",
    "resolved_conflict": false,
    "id": "a71a2d49-6a5e-4a9a-81dd-1f463a95e52b",
    "name": "First",
    "deleted_at": null
}
```

This endpoint creates a new template_check_item.

### HTTP Request

`POST /projects/<Project ID>/template_checklists/<TemplateChecklist ID>/template_check_items`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the template_check_item's project
TemplateCheckListId | The ID of the template_check_item's template_checklist

## Update TemplateCheckItem

```http
PATCH /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/template_check_items/75d68ca1-0fc1-456a-bd9d-8b23875ac540 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{ "name": "Updated item" }
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "created_at": "2014-07-08T23:45:22.000Z",
    "updated_at": "2014-07-08T23:45:22.000Z",
    "device_created_at": "2014-07-08T23:45:22.000Z",
    "device_updated_at": "2014-07-08T23:45:22.000Z",
    "resolved_conflict": false,
    "id": "a71a2d49-6a5e-4a9a-81dd-1f463a95e52b",
    "name": "Updated item",
    "deleted_at": null
}
```

This endpoint updates a specific template_check_item.

### HTTP Request

`PATCH /projects/<Project ID>/template_check_items/<TemplateCheckItem ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the template_check_item's project
TemplateCheckItem ID | The ID of the template_check_item to retrieve

## Delete TemplateCheckItem

```http
DELETE /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/template_check_items/75d68ca1-0fc1-456a-bd9d-8b23875ac540 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 204 OK
Content-Type: application/json
```

This endpoint deletes the template_check_item.

### HTTP Request

`DELETE /projects/<Project ID>/template_check_items/<TemplateCheckItem ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the template_check_item's project
TemplateCheckItem ID | The ID of the template_check_item to retrieve