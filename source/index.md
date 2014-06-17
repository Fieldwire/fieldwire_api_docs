---
title: Fieldwire API

language_tabs:
  - shell

toc_footers:
  - <a href='https://console.fieldwire.net'>Log In</a>
  - <a href="mailto:support@fieldwire.net?subject=Api Token Request">Request an API token</a>
  - <a href="mailto:support@fieldwire.net">Email support</a>

includes:
  - projects
  - teams
  - users
  - floorplans
  - tasks
  - bubbles
  - attachments
  - hyperlinks
  - errors

---

# Introduction

<aside class="warning">This is an alpha version of the fieldwire API and we don't yet make commitments to preserve backwards compatibility.</aside>

Welcome to the fieldwire API! You can use our API to access your fieldwire projects.

<aside class="notice">
All calls must be made over HTTPS.
</aside>

# Authentication

> To authorize, use this code:

```shell
curl "https://console.fieldwire.net/api/v1/projects/..."
  -H "Authorization: Token api=[api token]>,project=[project token]"
```

> Make sure to replace [api token] and [project token] with your api token and project token, respectively.

Fieldwire uses API tokens to allow access to the API. You can request a new fieldwire API token by emailing <a href="mailto:support@fieldwire.net?subject=Api Token Request">support</a>.

Fieldwire expects for the API and project token to be included in all API requests to the server in a header that looks like the following:

`Authorization: Token api=[api token],project=[project token]`

<aside class="notice">
You must replace [api token] and [project token] with your api and project tokens, respectively.
</aside>

# Common fields

Field | Description
--------- | -----------
id | The id of the entity
created_at | The time when the server created the entity
updated_at | The time when the server last updated the entity
device_created_at | The time when the device created the entity
device_updated_at | The time when the device last updated the entity
deleted_at | The time the entity was deleted
resolved_conflict | Indicates if the PUT request was rejected - do not store this field!
