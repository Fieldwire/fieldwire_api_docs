# TemplateCheckItems

## TemplateCheckItem Fields

Field | Description
--------- | -----------
project_id | Project ID the template_check_item belongs to
name | Name of template_check_item

## Post TemplateCheckItem

```shell
curl "https://console.fieldwire.net/api/v2/projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/template_checklists/be0f608-7e89-4301-bb13-ffd9db05d60c/template_check_items" \
  -X POST \
  -H "Authorization: Token api=[api token]>,project=[project token]" \
  -H "Content-type: application/json" \
  -d '{ "template_check_item": { "name": "First" }}'
```

> The above command returns JSON structured like this:

```json
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

`POST https://console.fieldwire.net/api/v2/projects/<Project ID>/template_checklists/<TemplateChecklist ID>/template_check_items`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the template_check_item's project
TemplateCheckListId | The ID of the template_check_item's template_checklist

## Update TemplateCheckItem

```shell
curl "https://console.fieldwire.net/api/v2/projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/template_check_items/75d68ca1-0fc1-456a-bd9d-8b23875ac540" \
  -X PATCH \
  -H "Authorization: Token api=[api token]>,project=[project token]" \
  -H "Content-type: application/json" \
  -d '{ "template_check_item": { "name": "Updated item" }'
```

> The above command returns JSON structured like this:

```json
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

`PATCH https://console.fieldwire.net/api/v2/projects/<Project ID>/template_check_items/<TemplateCheckItem ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the template_check_item's project
TemplateCheckItem ID | The ID of the template_check_item to retrieve

## Delete TemplateCheckItem

```shell
curl "https://console.fieldwire.net/api/v2/projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/template_check_items/75d68ca1-0fc1-456a-bd9d-8b23875ac540" \
  -X DELETE \
  -H "Authorization: Token api=[api token]>,project=[project token]" \
  -H "Content-type: application/json"
```

> The above command returns 204 No Content

This endpoint updates a specific template_check_item.

### HTTP Request

`DELETE https://console.fieldwire.net/api/v2/projects/<Project ID>/template_check_items/<TemplateCheckItem ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the template_check_item's project
TemplateCheckItem ID | The ID of the template_check_item to retrieve