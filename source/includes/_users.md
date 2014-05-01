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

```shell
curl "https://console.fieldwire.net/api/v1/projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/users" \
  -H "Authorization: Token api=[api token]>,project=[project token]"
```

> The above command returns JSON structured like this:

```json
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

`GET https://console.fieldwire.net/api/v1/projects/<Project ID>/users`

### URL Parameters

Parameter | Description
--------- | -----------
Project ID | The ID of the project to retrieve

## Managing Users

<aside class="warning">
    Fieldwire API does not currently support managing users.
</aside>

<aside class="notice">
    <a href='https://console.fieldwire.net'>Log In</a> to manage users.
</aside>
