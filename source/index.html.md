---
title: API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the HelloFresh API! You can use our API to access HelloFresh API endpoints.

# Authentication

> To authorize, use this code:


```shell
# With shell, you can just pass the correct header with each request
curl "https://api-v2.hellofresh.com/auth/oauth2/client/access_token?country=de"
-H "Content-Type: application/json"
--data-binary $'{"clienet_id": "YOUR_CLIENT_ID", "client_secret": "YOUR_CLIENT_SECRET", "scope": "public", "grant_type": "client_credentials"}'
```

> Make sure to replace `YOUR_CLIENT_ID` and `YOUR_CLIENT_SECRET` with your real API credentials.

We use oAuth2 in order to grant access to our API. For every request you need a client token. In order to get client token you have to do this request.

### HTTP Request

`GET http://api-v2.hellofresh.com/auth/oauth2/client/access_token`

### Headers

`Content-Type: application/json`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
country   | false   | Country is mandatory for all requests (AT, AU, BE, DE, GB, NL, US)

### Body Parameters

Remember to put these parameters as a JSON payload in the body request.

Parameter | Default | Description
--------- | ------- | -----------
client_id   | none   | Client ID that we provide you
client_secret   | none   | Client secret that we provide you
scope   | public   | Scope allowed for this client, by default is public
grant_type   | client_credentials   | Kind of credentials, in this case a client token


# Kittens

## Get All Kittens

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
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
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
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
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
