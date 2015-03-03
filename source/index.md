---
title: API Reference

language_tabs:
  - cURL


toc_footers:
  - <a href='http://www.dirxion.com'>Dirxion</a>
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Dirxion Products API! You can use our API to access Products API endpoints.

This example API documentation page was created with [Slate](http://github.com/tripit/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Authentication

> The Dirxion products API uses keys to allow access to the API. The key is expected in the header of all requests:

```cURL
# With cURL, you can just pass the correct header with each request

curl "http://account.drxlive.com/api/businesses" \
  -H "Authorization: Token token=TOK3N"
```

> Make sure to replace `TOK3N` with your API key.

The Dirxion Product API uses keys to allow access to the API.

The Dirxion Product API  expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Token token="TOK3N"`

<aside class="notice">
You must replace `TOK3N` with your API key.
</aside>

# Accounts (Only Used for Admin Functions)

## Get All Accounts

```cURL
curl "http://example.com/api/accounts"
  -H "Authorization: TOK3N"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Acklands",
    "address": "123 main street yourtown, mo 63122"
  }
]


### HTTP Request

`GET http://example.com/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/3"
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Isis",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">If you're not using an administrator API key, note that some kittens will return 403 Forbidden if they are hidden for admins only.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the cat to retrieve

