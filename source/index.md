---
title: API Reference

language_tabs:
  - shell
  - ruby
  - python

toc_footers:
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Kittn API! You can use our API to access Kittn API endpoints, which can get information on various cats, kittens, and breeds in our database.

We have language bindings in Shell, Ruby, and Python! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Authentication

> To authorize, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "http://api.drxserv.com"
  -H "Authorization: Token token=meowmeowmeow"
```

> Make sure to replace `meowmeowmeow` with your API key.

DRX Products uses API keys to allow access to the API.

DRX Products expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Token token=meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Products

## Get All Products

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://api.drxserv.com/products"
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "item_id": "calico"
  },
  {
    "id": 2,
    "name": "Isis",
    "item_id": "unknown"
  }
]
```

This endpoint retrieves all products.

### HTTP Request

`GET http://api.drxserv.com/products`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
category | empty | Limit the products to this specific category id.
brand | empty | Limit the products to this specific brand id.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Product

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
curl "http://api.drxserv.com/products/2"
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Isis",
  "item_id": "unknown"
}
```

This endpoint retrieves a specific product.

<aside class="warning">If you're not using an administrator API key, note that some kittens will return 403 Forbidden if they are hidden for admins only.</aside>

### HTTP Request

`GET http://api.drxserv.com/products/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the product to retrieve

# Categories

## Get All Categories

This endpoint retrieves all categories

### HTTP Request

`GET http://api.drxserv.com/categories`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
parent | optional | Limit to a specific parent category. A blank value will return top level categories.

# Search

## Search Products

This endpoint searches all products

### HTTP Request

`GET http://api.drxserv.com/search/products`


### Query Parameters

Parameter | Type   | Description
--------- | ------ | -----------
q         | string | The search keywords
