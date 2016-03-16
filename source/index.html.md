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

```json
{
    "access_token": "random-string",
    "token_type": "Bearer",
    "expires_in": 31536000
}
```

We use oAuth2 in order to grant access to our API. For every request you need a client token. In order to get client token you have to do this request.

### HTTP Request

`GET http://api-v2.hellofresh.com/auth/oauth2/client/access_token`

### Headers

`Content-Type: application/json`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
country   | string   | Country is mandatory for all requests (AT, AU, BE, DE, GB, NL, US)

### Body Parameters

Remember to put these parameters as a JSON payload in the body request.

Parameter | Type | Description
--------- | ------- | -----------
client_id   | string   | Client ID that we provide you
client_secret   | string   | Client secret that we provide you
scope   | string   | Scope allowed for this client, by default is public
grant_type   | string   | Kind of credentials, in this case a client token


# Recipes

## Search Recipes

```shell
curl "https://api-v2.hellofresh.com/recipes/search?country=DE&q=pizza&limit=1"
  -H "Authorization: Bearer MY_TOKEN"
  -H "Content-Type: application/json"
```

> The above command returns JSON structured like this:

```json
{
  "items": [
    {
      "imageLink": "https://d3hvwccx09j84u.cloudfront.net/web/image/56b1bc45f8b25ebc158b4568.jpg?t=20160203083725",
      "thumbLink": "https://d3hvwccx09j84u.cloudfront.net/web/thumb/56b1bc45f8b25ebc158b4568.jpg?t=20160203083725",
      "videoLink": null,
      "cardLink": null,
      "favoritesCount": null,
      "ratingsCount": 1889,
      "averageRating": 2.8,
      "userFavorite": null,
      "userRating": null,
      "name": "Grüne Pizza mit Zitronen-Ricotta",
      "description": null,
      "headline": "und Kirschtomaten",
      "prepTime": "PT40M",
      "difficulty": 2,
      "weeks": null,
      "productFamilies": null,
      "allergens": [],
      "yieldType": null,
      "yields": null,
      "ingredients": [],
      "steps": null,
      "nutrition": null,
      "cuisines": null,
      "categories": [],
      "highlighted": false,
      "active": true,
      "utensils": [],
      "tags": [
        {
          "name": "Vegetarisch",
          "type": "vegetarian",
          "numberOfRecipes": null,
          "imageByAuthor": {
            "JO": "https://s3-eu-west-1.amazonaws.com/hf-recipes/tags/HF_IOS_icon_VEGGIE_105%401x_JO.png"
          },
          "id": "55422d79f8b25eb6758b474a",
          "link": null,
          "country": null,
          "iconLink": "https://s3-eu-west-1.amazonaws.com/hf-recipes/tags/icon-veggie%403x.png"
        }
      ],
      "presets": null,
      "author": null,
      "id": "56b1bc45f8b25ebc158b4568",
      "link": "https://api.dev.hellofresh.com//recipes/56b1bc45f8b25ebc158b4568?country=DE",
      "createdAt": "2016-02-03T08:37:25+0000",
      "updatedAt": "2016-02-03T08:37:25+0000",
      "country": "DE",
      "slug": "grune-pizza-mit-zitronen-ricotta",
      "websiteUrl": "/recipe/detail/56b1bc45f8b25ebc158b4568"
    }
  ],
  "count": 1,
  "total": 30,
  "criteria": {
    "q": "pizza",
    "limit": 1,
    "product": null,
    "week": null,
    "allergen": null,
    "ingredient": null,
    "cuisine": null,
    "tag": null,
    "diet": null,
    "max-prep-time": null,
    "level": null,
    "name": null,
    "offset": 0,
    "order": null
  }
}
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://api-v2.hellofresh.com/recipes/search`

### Headers

`Content-Type: application/json`
`Authorization: Bearer YOUR_TOKEN`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
country   | string   | Country is mandatory for all requests (AT, AU, BE, DE, GB, NL, US)
q   | string   | Fulltext search
week   | string   | Product or products: classic-box; classic-box|veggie-box
allergen   | string   | Allergen slug or slugs: shell; shell|egg|nuts
ingredient   | string   | Ingredient slug or slugs: carrot; carrot|pumpkin|sweet-potato
cuisine   | string   | Cuisine slug or slugs: french; french|spanish|moroccan
tag   | string   | Tag type or types: egg-free; egg-free|shell-free|vegan
diet   | string   | Diet or diets: high-protein; high-protein|low-fat|low-sodium
max-prep-time   | integer   | Maximum preparation time: 30; 50
level   | integer   | Difficulty level: 3; 1
name   | string   | Partial name of the recipe: chi; chicken
with-favorites   | boolean   | Whether the recipes should include customer favorites
with-ratings   | boolean   | Whether the recipes should include customer ratings
offset   | integer   | Offset from the first result
limit   | integer   | Maximum number of recipes to return
order   | string   | Sort order: date; -date; rating; -rating; time; -time; name; -name; -date|rating|-time|name

<aside class="success">
Remember to put the country in your request!
</aside>

## Get a Specific Kitten


```shell
curl "https://api-v2.hellofresh.com/recipes/search?country=DE&q=pizza&limit=1"
  -H "Authorization: Bearer MY_TOKEN"
  -H "Content-Type: application/json"
```

> The above command returns JSON structured like this:

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve
