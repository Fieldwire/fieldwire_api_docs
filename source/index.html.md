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
  - entity_tags
  - entity_taggings
  - errors

search: true
---

# Introduction

**Welcome to the Fieldwire API! You can use our API to access your Fieldwire projects.**

<aside class="notice">Current API endpoint: https://console.fieldwire.net/api/v3</aside>

# Sample Apps

These apps demonstrate some basic API authentication and calls:

* Ruby: [https://github.com/Fieldwire/fieldwire_ruby_sample](https://github.com/Fieldwire/fieldwire_ruby_sample)
* Java: [https://github.com/Fieldwire/fieldwire_java_sample](https://github.com/Fieldwire/fieldwire_java_sample)


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

Fieldwire uses API tokens to allow access to the API. You can request a new Fieldwire API token by emailing <a href="mailto:support@fieldwire.net?subject=Api Token Request">support</a>.

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
X-Count | Number of entities in response
X-Last-Synced-At | Timestamp indicating exactly how up to date the client is after processing/storing these entities (see [Syncing Data](#syncing-data))
X-Has-More | Boolean indicating if additional entities exist

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
    "users": "2018-04-06T22:43:52.023Z",
    "teams": "2018-03-06T19:06:11.662Z",
    "floorplans": "2017-02-03T20:09:52.829Z",
    "hyperlinks": null,
    "multi_hyperlinks": null,
    "markups": null,
    "attachments": "2018-03-22T22:27:47.878Z",
    "template_checklists": "2018-03-07T23:25:05.438Z",
    "automatic_hyperlinks": null,
    "sheets": "2017-02-03T20:09:52.729Z",
    "attachments_multi_hyperlinks": null,
    "tasks": "2018-04-06T22:12:39.768Z",
    "bubbles": "2018-04-06T22:12:39.736Z",
    "bubble_markups": "2018-04-06T21:38:06.615Z",
    "task_check_items": "2018-04-06T21:52:30.570Z",
    "folders": "2018-03-22T22:27:40.180Z",
    "sheet_uploads": "2017-02-03T20:07:58.156Z",
    "entity_tags": "2018-04-04T17:59:28.203Z",
    "entity_taggings": "2018-04-06T00:31:49.581Z",
    "task_relations": "2018-04-06T21:00:11.932Z",
    "locations": "2018-01-15T22:35:30.876Z",
    "report_templates": "2018-04-02T12:01:10.395Z",
    "data_types": null,
    "data_type_values": null,
    "form_templates": null,
    "form_template_sections": null,
    "form_template_section_records": null,
    "form_template_section_record_inputs": null,
    "form_template_form_statuses": null,
    "forms": null,
    "form_sections": null,
    "form_section_records": null,
    "form_section_record_values": null,
    "form_section_record_inputs": null,
    "form_section_record_input_values": null
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

Field | Description | Type | Non-null? | Editable? | Default
--------- | --------- | --------- | --------- | --------- | ---------
id | The id of the entity | UUID | x | | _generated_
created_at | The time when the server created the entity | DateTime | x | | _generated_
updated_at | The time when the server last updated the entity | DateTime | x | | _generated_
device_created_at | The time when the device created the entity | DateTime | x | x | _generated_
device_updated_at | The time when the device last updated the entity | DateTime | x | x | _generated_
deleted_at | The time the entity was deleted | DateTime |  | x |
resolved_conflict | Indicates if the PUT/PATCH request was rejected - do not store this field! | Boolean | | | false

<aside class="notice">
When displaying entities, sort using device_created_at/device_updated_at as this will guarantee that entities are displayed when the user actually created them
</aside>