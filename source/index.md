---
title: Composer API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Composer API!

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "http://drxserv.com/api"
  -H "Accept: application/vnd.drxserv+json; version=1"
  -H "Authorization: Token token=meowmeowmeow"
```

> Make sure to replace `meowmeowmeow` with your API key.

Composer uses API keys to allow access to the API.

Composer expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Token token=meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Current Version

`Accept: application/vnd.drxserv+json; version=1`

# Products

## Get All Products

```shell
curl "http://drxserv.com/api/products"
  -H "Accept: application/vnd.drxserv+json; version=1"
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "products": [
    {
      "id": "564a2b774ae4921ebf000012"
    },
    {
      "id": "564a2b7e4ae4921ebf000153"
    }
  ]
}
```

This endpoint retrieves all products.

### HTTP Request

`GET http://drxserv.com/api/products`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
category | empty | Limit the products to this specific category id.
brand | empty | Limit the products to this specific brand id.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Product

```shell
curl "http://drxserv.com/api/products/2"
  -H "Accept: application/vnd.drxserv+json; version=1"
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "product": {
    "id": "564a2b774ae4921ebf000012"
  }
}
```

This endpoint retrieves a specific product.

<aside class="warning">If you're not using an administrator API key, note that some kittens will return 403 Forbidden if they are hidden for admins only.</aside>

### HTTP Request

`GET http://drxserv.com/api/products/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the product to retrieve

# Categories

## Get All Categories

This endpoint retrieves all categories

### HTTP Request

`GET http://drxserv.com/api/categories`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
parent | optional | Limit to a specific parent category. A blank value will return top level categories.

# Search

## Search Products

This endpoint searches all products

### HTTP Request

`GET http://drxserv.com/api/search/products`


### Query Parameters

Parameter | Type   | Description
--------- | ------ | -----------
q         | string | The search keywords
