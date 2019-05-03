---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript
  - shell

toc_footers:
  - <a href='https://apps.tlt.stonybrook.edu/marginaliacss/'>Marginalia Full Site</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Marginalia API! You can use the Marginalia API independently of the Marginalia website.

The purpose of these docs, are to allow new developers to learn, understand, expand or integrate their own applications with Marginalia.

The backend API was built with <a href='https://docs.slimframework.com/'>Slim 2 Framework</a> and PHP 5.

# About

Marginalia's API (Slim Framework) is a RESTful API service.

All the endpoints can be reached with simple GET & POST HTTP requests.

The right side of the browser shows sample JavaScript code which may be used to connect to various endpoints described.

<aside class="notice">
You must be logged in with your SUNY (Solar/Shibboleth) credentials to access any endpoints. Meaning you must supply valid cookie credentials with every request.
</aside>

# Permissions

## Get Work Permissions

## Add User to Work Permissions

## Remove User from Work Permissions

# Work

## Create Work

## Get Work Data

## Set Work Privacy

# Comments

## Get Highlighted Comments

## Get Comment Chain

## Create Comment

## Edit Comment

## Delete Comment

## Set Comment Public/Private

# Users

## Get Creators

This endpoint retrieves the EPPNs of users that have created works on the site.

```javascript
let base_url = "https://apps.tlt.stonybrook.edu/marginaliacss/api/public";
let endpoint = "/get_creators"

getCreators(base_url, endpoint)
  .then(data => console.log(JSON.stringify(data)))
  .catch(error => console.error(error));

function getCreators(base_url, endpoint) {
  return fetch(base_url + endpoint, {
    method: "GET"
  })
  .then(response => response.json());
}
```

```shell
curl "https://apps.tlt.stonybrook.edu/marginaliacss/api/public/get_creators"
--cookie "..."
```

> The above command returns JSON structured like this:

```json
{
  "status": "ok",
  "data": [
    "creator1@stonybrook.edu",
    "creator2@stonybrook.edu",
    "creator3@stonybrook.edu"
  ]
}
```

### HTTP Request

`GET https://apps.tlt.stonybrook.edu/marginaliacss/api/public/get_creators`

## Get Current User

Retrieves the first and last name, as-well as the EPPN of the currently logged in user.

```javascript
let base_url = "https://apps.tlt.stonybrook.edu/marginaliacss/api/public";
let endpoint = "/get_current_user"

getCurrentUser(base_url, endpoint)
  .then(data => console.log(JSON.stringify(data)))
  .catch(error => console.error(error));

function getCurrentUser(base_url, endpoint) {
  return fetch(base_url + endpoint, {
    method: "GET"
  })
  .then(response => response.json());
}
```

```shell
curl "https://apps.tlt.stonybrook.edu/marginaliacss/api/public/get_current_user"
--cookie "..."
```

> The above command returns JSON structured like this:

```json
{
  "status": "ok",
  "data": {
    "firstname": "John",
    "lastname": "Doe",
    "eppn": "jdoe@stonybrook.edu"
  }
}
```

### HTTP Request

`GET https://apps.tlt.stonybrook.edu/marginaliacss/api/public/get_current_user`

## Delete a Specific Kitten


```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete
