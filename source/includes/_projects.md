# Projects

## Fields

Field | Description
--------- | -----------
name | Name of the project
address | Address of the project
archived_at | The time when the project was archived

## Get Project

```shell
curl "https://console.fieldwire.net/api/v1/projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027"
  -H "Authorization: Token api=[api token]>,project=[project token]"
```

> The above command returns JSON structured like this:

```json
{
    "created_at": "2014-04-30T19:02:10.000Z",
    "updated_at": "2014-04-30T19:02:10.000Z",
    "device_created_at": "2014-04-30T19:02:10.000Z",
    "device_updated_at": "2014-04-30T19:02:10.000Z",
    "resolved_conflict": false,
    "id": "aceb1617-2dcf-4b01-a6b1-d8ae02bc3027",
    "name": "Sample project",
    "address": null,
    "archived_at": null,
    "deleted_at": null
}
```

This endpoint retrieves a specific project.

### HTTP Request

`GET https://console.fieldwire.net/api/v1/projects/<Project ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the project to retrieve