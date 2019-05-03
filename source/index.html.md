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



# Marginalia

## Get Creators [GET: /get_creators]

This endpoint

```javascript
getCreators()
  .then(data => console.log(JSON.stringify(data)))
  .catch(error => console.error(error));

function getCreators() {
  return fetch("https://apps.tlt.stonybrook.edu/marginaliacss/api/public/get_creators", {
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

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten


```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

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
