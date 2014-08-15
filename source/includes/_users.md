# Users

## User Fields

Field | Description
--------- | -----------
first_name | First name of the user
last_name | Last name of the user
company | Company of the user
phone_number | Phone number of the user
photo_url | Photo of the user
is_admin | Indicates if user is an admin on the project
is_approved | Indicates if user is approved by an admin on the project
is_confirmed | Indicates if an invited user has accepted their invite
user_blocked_at | Time when user was blocked from accessing this project
user_deleted_at | Time when user was removed from project
current_sign_in_at | Approximately last time user signed into fieldwire
invited_by_id | The user ID that invited this user
is_email_notifications_enabled | Indicates if the user receives email notifications
emails_address | Contains array of emails with an is_primary indicator

## Get Users

```http
GET /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/users HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
    {
        "created_at": "2014-02-27T00:00:29.000Z",
        "updated_at": "2014-04-30T19:02:10.000Z",
        "id": 2,
        "first_name": "Bob",
        "last_name": "Super",
        "company": "Fieldwire",
        "phone_number": null,
        "photo_url": null,
        "is_admin": true,
        "is_approved": true,
        "is_confirmed": true,
        "user_blocked_at": null,
        "user_deleted_at": null,
        "current_sign_in_at": null,
        "invited_by_id": null,
        "is_email_notifications_enabled": true,
        "email_addresses": [
            {
                "email": "bob@fieldwire.net",
                "is_primary": true
            }
        ]
    },
    {
        "created_at": "2014-02-27T00:00:30.000Z",
        "updated_at": "2014-04-30T19:02:10.000Z",
        "id": 3,
        "first_name": "James",
        "last_name": "Foreman",
        "company": "Fieldwire",
        "phone_number": null,
        "photo_url": null,
        "is_admin": true,
        "is_approved": true,
        "is_confirmed": true,
        "user_blocked_at": null,
        "user_deleted_at": null,
        "current_sign_in_at": null,
        "invited_by_id": null,
        "is_email_notifications_enabled": true,
        "email_addresses": [
            {
                "email": "james@fieldwire.net",
                "is_primary": true
            }
        ]
    }
]
```

This endpoint retrieves all users.

### HTTP Request

`GET /projects/<Project ID>/users`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the project to retrieve

## Invite Users

```http
POST /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/users/invite HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{ "email": "bob@fieldwire.net,james@fieldwire.net" }
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "success": true,
    "users": [
        {
            "created_at": "2014-01-23T00:32:18.657Z",
            "updated_at": "2014-08-15T21:40:27.273Z",
            "id": 15,
            "first_name": "Bob",
            "last_name": "Super",
            "company": "Fieldwire",
            "phone_number": null,
            "photo_url": null,
            "is_admin": false,
            "is_approved": true,
            "is_confirmed": true,
            "user_blocked_at": null,
            "user_deleted_at": null,
            "current_sign_in_at": null,
            "invited_by_id": null,
            "is_email_notifications_enabled": true,
            "email_addresses": [
                {
                    "email": "bob@fieldwire.net",
                    "is_primary": true
                }
            ]
        },
        {
            "created_at": "2014-01-23T00:32:19.354Z",
            "updated_at": "2014-08-15T21:40:27.923Z",
            "id": 16,
            "first_name": "James",
            "last_name": "Foreman",
            "company": "Fieldwire",
            "phone_number": null,
            "photo_url": null,
            "is_admin": false,
            "is_approved": true,
            "is_confirmed": true,
            "user_blocked_at": null,
            "user_deleted_at": null,
            "current_sign_in_at": null,
            "invited_by_id": null,
            "is_email_notifications_enabled": true,
            "email_addresses": [
                {
                    "email": "james@fieldwire.net",
                    "is_primary": true
                }
            ]
        }
    ]
}
```

This endpoint invites users to your project. If they have a fieldwire account, they will receive an email notification, otherwise they will receive invite instructions to join fieldwire.

### HTTP Request

`POST /projects/<Project ID>/users/invite`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the user's project

### Email

Can be up to 25 emails separated by commas or semicolons.

## Update User's Role

```http
PUT /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/users/15 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{ "user": { "is_admin": true, "is_approved": true } }
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "created_at": "2014-01-23T00:32:18.657Z",
    "updated_at": "2014-08-15T21:40:27.273Z",
    "id": 15,
    "first_name": "Bob",
    "last_name": "Super",
    "company": "Fieldwire",
    "phone_number": null,
    "photo_url": null,
    "is_admin": true,
    "is_approved": true,
    "is_confirmed": true,
    "user_blocked_at": null,
    "user_deleted_at": null,
    "current_sign_in_at": null,
    "invited_by_id": null,
    "is_email_notifications_enabled": true,
    "email_addresses": [
        {
            "email": "bob@fieldwire.net",
            "is_primary": true
        }
    ]
}
```

This endpoint will update a user's role and approval status on a project.

### HTTP Request

`PUT /projects/<Project ID>/users/<User ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the user's project
User ID | The ID of the user

## Update User's Profile

```http
PUT /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/users/15/profile HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json

{ "user": { "company": "Fieldwire", "phone_number": "(415) 555-5555" } }
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "created_at": "2014-01-23T00:32:18.657Z",
    "updated_at": "2014-08-15T22:02:50.404Z",
    "id": 15,
    "first_name": "Bob",
    "last_name": "Super",
    "company": "Fieldwire",
    "phone_number": "(415) 555-5555",
    "photo_url": null,
    "is_admin": false,
    "is_approved": true,
    "is_confirmed": true,
    "user_blocked_at": null,
    "user_deleted_at": null,
    "current_sign_in_at": null,
    "invited_by_id": null,
    "is_email_notifications_enabled": true,
    "email_addresses": [
        {
            "email": "bob@fieldwire.net",
            "is_primary": true
        }
    ]
}
```

This endpoint will update a user's role and approval status on a project.

### HTTP Request

`PUT /projects/<Project ID>/users/<User ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the user's project
User ID | The ID of the user

## Resend Invite

```http
POST /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/users/15/reinvite HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json
```

This endpoint will resend an invite email to user if they haven't joined fieldwire yet.

<aside class="warning">
    This will not reinvite removed users to a project. To re-add a user simply invite their email address again.
</aside>

### HTTP Request

`POST /projects/<Project ID>/users/<User ID>/reinvite`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the user's project
User ID | The ID of the user

## Delete User

```http
DELETE /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/users/15 HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 204 OK
Content-Type: application/json
```

This endpoint removes a user from the project.

### HTTP Request

`DELETE /projects/<Project ID>/users/<User ID>`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the user's project
User ID | The ID of the user to retrieve