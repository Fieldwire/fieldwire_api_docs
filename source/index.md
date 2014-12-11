---
title: Fieldwire API

language_tabs:
  - http

toc_footers:
  - <a href='https://console.fieldwire.net'>Log In</a>
  - <a href="mailto:support@fieldwire.net?subject=Api Token Request">Request an API token</a>
  - <a href="mailto:support@fieldwire.net">Email support</a>

includes:
  - projects
  - users
  - teams
  - folders
  - sheet_uploads
  - floorplans
  - sheets
  - tasks
  - task_check_items
  - template_checklists
  - template_check_items
  - bubbles
  - bubble_markups
  - attachments
  - hyperlinks
  - multi_hyperlinks
  - automatic_hyperlinks
  - markups
  - markup_data
  - errors

search: true
---

# Introduction

**Welcome to the fieldwire API! You can use our API to access your fieldwire projects.**

<aside class="notice">Current API endpoint: https://console.fieldwire.net/api/v2</aside>



# Authentication

> To authorize for viewing and creating projects, use this code:

```http
GET /projects HTTP/1.1
Authorization: Token api=[api token]>
```

> To authorize for modifying project and all of its entities, use this code:

```http
GET /projects/<ProjectID> HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
```

Fieldwire uses API tokens to allow access to the API. You can request a new fieldwire API token by emailing <a href="mailto:support@fieldwire.net?subject=Api Token Request">support</a>.

Fieldwire expects for the API and project token to be included in all API requests to the server in a header that looks like one of the following:

`Authorization: Token api=[api token]`
<br>
<br>
`Authorization: Token api=[api token],project=[project token]`

<aside class="notice">
You must replace [api token] and [project token] with your api and project tokens, respectively.
</aside>

# Request Headers

Header | Description
--------- | -----------
Fieldwire-Per-Page | Number of items returned (default: 50, max: 1000)
Fieldwire-With-Deleted | Boolean that determines if deleted entities are returned (default: true)

# Response Headers

Header | Description
--------- | -----------
X-Total-Pages | Number of total pages that exist for this resource
X-Current-Page | Number of current page (add 1 to this to retrieve the next page of entities)
X-Count | Number of entities in response
X-Last-Synced-At | Timestamp indicating exactly how up to date the client is after processing/storing these entities (see [Syncing Data](#syncing-data))

# Syncing Data

```http
GET /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/activity HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "users": "2014-08-15T19:42:24.359Z",
    "teams": "2014-08-15T00:42:36.722Z",
    "floorplans": "2014-08-15T01:28:17.107Z",
    "tasks": null,
    "bubbles": null,
    "hyperlinks": null,
    "markups": null,
    "attachments": null,
    "task_check_items": null,
    "template_checklists": null,
    "automatic_hyperlinks": null,
    "bubble_markups": null
}
```
> Local stored timestamp for floorplans, teams, and users are 2014-08-12T01:28:17.107Z, 2014-08-13T01:28:17.107Z, 2014-08-14T01:28:17.107Z respectively

```http
GET /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/floorplans?last_synced_at=2014-08-12T01:28:17.107Z HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

```http
GET /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/teams?last_synced_at=2014-08-13T01:28:17.107Z HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

```http
GET /projects/aceb1617-2dcf-4b01-a6b1-d8ae02bc3027/users?last_synced_at=2014-08-14T01:28:17.107Z HTTP/1.1
Authorization: Token api=[api token]>,project=[project token]
Content-type: application/json
```

If you want to retain a synced local copy of your project data you can use a combination of [Project Activity](#get-project-activity) and [Last Synced At](#response-headers) to guarantee correctness while minimizing API requests.

Steps:

* Retrieve [Project Activity](#get-project-activity)
* Skip all resources with `null` values since they have 0 entities.
* For resources with values, compare timestamp to your stored local timestamp (from [Last Synced At](#response-headers))
* If your local timestamp is greater or equal than the activities' timestamp, no need to query that response
* If your local timestamp is less than the activities' timestamp, query the resource using `?last_synced_at=[local timestamp]` (omit if you are querying for the first time)

# Common fields

These fields are shared across entities

Field | Description
--------- | -----------
id | The id of the entity
created_at | The time when the server created the entity
updated_at | The time when the server last updated the entity
device_created_at | The time when the device created the entity
device_updated_at | The time when the device last updated the entity
deleted_at | The time the entity was deleted
resolved_conflict | Indicates if the PUT/PATCH request was rejected - do not store this field!

<aside class="notice">
When displaying entities, sort using device_created_at/device_updated_at as this will guarantee that entities are displayed when the user actually created them
</aside>