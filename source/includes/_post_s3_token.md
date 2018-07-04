# Post S3 token

## Post S3 tokens purpose

The storage used by Fieldwire, Amazon S3, allow user to directly post files to it, 
without having to go through Fieldwire server.

https://docs.aws.amazon.com/AmazonS3/latest/API/sigv4-UsingHTTPPOST.html

The post S3 token contains all the information you need to use this functionnality
and has a 1 day expiry.
After receiving one, you simply have to create a POST request that contains all the
fields of the post S3 token, and add a "file" field with your file content and 
send it directly to aws (to the post_address contained in the token)

The only action you can do on Fieldwire api with post S3 token is to request one.

It is highly recommended to look at the two demo client applications :

* Ruby: [https://github.com/Fieldwire/fieldwire_ruby_sample](https://github.com/Fieldwire/fieldwire_ruby_sample)
* Java: [https://github.com/Fieldwire/fieldwire_java_sample](https://github.com/Fieldwire/fieldwire_java_sample)

Which both contains an example of post S3 token usage.

## Post S3 token field

Field | Description | Type | Non-null? | Editable? | Default
--------- | --------- | --------- | --------- | --------- | ---------
post_address |  | UUID | x | |
post_parameters | Name of the sheet | JSON | x | |


## Get Sheet Uploads

```http
GET /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/sheet_uploads HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
    {
        "created_at": "2014-08-26T00:18:17.000Z",
        "updated_at": "2014-08-26T00:18:22.000Z",
        "id": "51af34a9-b8fc-477d-907d-0b9064120b88",
        "name": "Single.pdf",
        "file_url": "https://example.com/Single.pdf",
        "file_size": "2244590",
        "user_id": 1,
        "is_processed": true,
        "pages": 1
    },
    {
        "created_at": "2014-08-26T00:20:00.000Z",
        "updated_at": "2014-08-26T00:20:10.000Z",
        "id": "701f69be-02bb-4786-ab48-be0d993bf2a5",
        "name": "Multipage.pdf",
        "file_url": "https://example.com/.pdf",
        "file_size": "5584913",
        "user_id": 1,
        "is_processed": true,
        "pages": 3
    }
]
```

This endpoint retrieves all sheet_uploads.

### HTTP Request

`GET /projects/<Project ID>/sheet_uploads`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the project to retrieve

## Get Sheet Upload

```http
GET /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/sheet_uploads/51af34a9-b8fc-477d-907d-0b9064120b88 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "created_at": "2014-08-26T00:18:17.000Z",
    "updated_at": "2014-08-26T00:18:22.000Z",
    "id": "51af34a9-b8fc-477d-907d-0b9064120b88",
    "name": "Single.pdf",
    "file_url": "https://example.com/Single.pdf",
    "file_size": "2244590",
    "user_id": 1,
    "is_processed": true,
    "pages": 1
}
```

This endpoint retrieves a specific sheet_upload.

### HTTP Request

`GET /projects/<Project ID>/sheet_uploads/<Sheet Upload ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the sheet_upload's project
Sheet Upload ID | The ID of the sheet_upload to retrieve

## Post Sheet Upload

```http
POST /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/sheet_uploads HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{
    "name": "Single.pdf",
    "file_url": "https://example.com/Single.pdf",
    "file_size": "2244590",
    "user_id": 1
}
```

> The above command returns:

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "created_at": "2014-08-26T00:18:17.000Z",
    "updated_at": "2014-08-26T00:18:22.000Z",
    "id": "51af34a9-b8fc-477d-907d-0b9064120b88",
    "name": "Single.pdf",
    "file_url": "https://example.com/Single.pdf",
    "file_size": "2244590",
    "user_id": 1,
    "is_processed": true,
    "pages": 1
}
```

This endpoint creates a new sheet_upload.

### HTTP Request

`POST /projects/<Project ID>/sheet_uploads`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the sheet_upload's project

## Update Sheet Upload

```http
PATCH /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/sheet_uploads/51af34a9-b8fc-477d-907d-0b9064120b88 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{ "is_processed": "true" }
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "created_at": "2014-08-26T00:18:17.000Z",
    "updated_at": "2014-08-26T00:18:22.000Z",
    "id": "51af34a9-b8fc-477d-907d-0b9064120b88",
    "name": "Single.pdf",
    "file_url": "https://example.com/Single.pdf",
    "file_size": "2244590",
    "user_id": 1,
    "is_processed": true,
    "pages": 1
}
```

This endpoint updates a specific sheet upload.

### HTTP Request

`PATCH /projects/<Project ID>/sheet_uploads/<Sheet Upload ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the sheet upload's project
Sheet Upload ID | The ID of the sheet upload to retrieve

## Managing Sheet Uploads

<aside class="warning">
    Once created, sheet uploads cannot be modified or deleted. To remove floorplans/sheets created from the sheet upload, delete them through their respective endpoints.
</aside>
