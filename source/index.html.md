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
curl -X POST "https://api-v2.hellofresh.com/auth/oauth2/client/access_token?country=de"
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

`POST http://api-v2.hellofresh.com/auth/oauth2/client/access_token`

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

## Get a Specific Recipe


```shell
curl "https://api-v2.hellofresh.com/recipes/ID"
  -H "Authorization: Bearer MY_TOKEN"
  -H "Content-Type: application/json"
```

> The above command returns JSON structured like this:

```json
{
  "imageLink": "https://d3hvwccx09j84u.cloudfront.net/web/image/56b1bc45f8b25ebc158b4568.jpg?t=20160316120957",
  "thumbLink": "https://d3hvwccx09j84u.cloudfront.net/web/thumb/56b1bc45f8b25ebc158b4568.jpg?t=20160316120957",
  "videoLink": null,
  "cardLink": "https://ddw4dkk7s1lkt.cloudfront.net/card/56b1bc45f8b25ebc158b4568.pdf?t=20160316120957",
  "favoritesCount": 937,
  "ratingsCount": 1921,
  "averageRating": 2.8,
  "userFavorite": null,
  "userRating": null,
  "name": "Grüne Pizza mit Zitronen-Ricotta",
  "description": "Pizza mal anders: Anstatt Mozzarella gibt es fruchtigen Ricotta, die Tomaten liegen nicht unten, sondern oben, und Pesto und karamellisierte Walnüsse sorgen für ein ganz besonderes Geschmackerlebnis. Obendrein ist diese Pizza auch noch ein echter Augenschmaus! Guten Appetit!",
  "headline": "und Kirschtomaten",
  "prepTime": "PT40M",
  "difficulty": 2,
  "weeks": null,
  "productFamilies": null,
  "allergens": [
    {
      "code": 7,
      "description": null,
      "id": "55422d79f8b25eb6758b456d",
      "link": null,
      "type": "milk",
      "country": "DE",
      "name": "Lactose",
      "slug": "lactose"
    }
  ],
  "yieldType": "servings",
  "yields": [
    {
      "ingredients": [
        {
          "id": "555da63dfd2cb95a758b4569",
          "amount": 1,
          "unit": "Stück"
        }
      ],
      "yields": 2
    }
  ],
  "ingredients": [
    {
      "internalName": "Basilikum",
      "imageLink": "https://d3hvwccx09j84u.cloudfront.net/200,200/image/554b32d1f8b25ef93e8b456e.png",
      "shipped": "1",
      "clonedFrom": "",
      "allergens": [],
      "family": null,
      "description": null,
      "id": "554b32d1f8b25ef93e8b456e",
      "link": null,
      "type": "basilikum",
      "country": "DE",
      "name": "Basilikum",
      "slug": "basilikum"
    }
  ],
  "steps": [
    {
      "index": 1,
      "instructions": "Brokkoli in feine Röschen teilen, waschen und dann grob hacken. Knoblauch abziehen. Basilikum waschen, trocken schütteln und die Blätter abzupfen. Parmesan grob reiben. Kirschtomaten waschen und in Scheiben schneiden. Limette entsaften.",
      "ingredients": [
        "554b32d1f8b25ef93e8b456e"
      ],
      "utensils": [
        "55422d79f8b25eb6758b4759"
      ],
      "images": [
        {
          "type": "image",
          "link": "https://d3hvwccx09j84u.cloudfront.net/0,1000/56b1bc45f8b25ebc158b4568/step_56b2418fa0b30.jpg",
          "caption": "Brokkoli klein schneiden"
        }
      ],
      "videos": [],
      "timers": []
    }
  ],
  "nutrition": [
    {
      "type": "55422d79f8b25eb6758b46c3",
      "country": "DE",
      "name": "Ballaststoffe",
      "amount": 4,
      "unit": "g"
    }
  ],
  "cuisines": [
    {
      "id": "55422d79f8b25eb6758b45ed",
      "link": null,
      "type": "fusion",
      "country": "DE",
      "name": "fusion",
      "slug": "fusion",
      "iconLink": ""
    }
  ],
  "categories": [],
  "highlighted": false,
  "active": true,
  "utensils": [
    {
      "id": "55422d79f8b25eb6758b475d",
      "link": null,
      "type": "stove",
      "country": "DE",
      "name": "Ofen",
      "iconLink": null
    }
  ],
  "tags": [
    {
      "name": "Vegetarisch",
      "type": "vegetarian",
      "numberOfRecipes": 193,
      "imageByAuthor": {
        "JO": "https://s3-eu-west-1.amazonaws.com/hf-recipes/tags/HF_IOS_icon_VEGGIE_105%401x_JO.png"
      },
      "id": "55422d79f8b25eb6758b474a",
      "link": null,
      "country": "DE",
      "iconLink": "https://s3-eu-west-1.amazonaws.com/hf-recipes/tags/icon-veggie%403x.png"
    }
  ],
  "presets": [],
  "author": null,
  "id": "56b1bc45f8b25ebc158b4568",
  "link": "https://api.dev.hellofresh.com//recipes/56b1bc45f8b25ebc158b4568?country=de",
  "createdAt": "2016-02-03T09:37:25+0100",
  "updatedAt": "2016-03-16T12:09:57+0100",
  "country": "DE",
  "slug": "grune-pizza-mit-zitronen-ricotta",
  "websiteUrl": "http://www.hellofresh.de/recipe/detail/56b1bc45f8b25ebc158b4568"
}
```

### HTTP Request

`GET https://api-v2.hellofresh.com.com/recipes/<ID>`

### Headers

`Content-Type: application/json`
`Authorization: Bearer YOUR_TOKEN`

### URL Parameters

Parameter | Type | Description
--------- | ---- | -----------
country   | string   | Country is mandatory for all requests (AT, AU, BE, DE, GB, NL, US)
ID | string | The ID of the recipe

# Ingredients

## Get ingredients

```shell
curl "https://api-v2.hellofresh.com/ingredients?country=DE&limit=1"
  -H "Authorization: Bearer MY_TOKEN"
  -H "Content-Type: application/json"
```

> The above command returns JSON structured like this:

```json
{
  "items": [
    {
      "internalName": "Karotte, lila",
      "imageLink": "https://d3hvwccx09j84u.cloudfront.net/200,200/image/5568261dfd2cb96e228b4568.png",
      "shipped": "1",
      "clonedFrom": "",
      "allergens": [],
      "family": null,
      "description": null,
      "id": "5568261dfd2cb96e228b4568",
      "link": null,
      "type": "karotte, lila",
      "country": "DE",
      "name": "Karotte, lila",
      "slug": "karotte-lila"
    }
  ],
  "count": 1
}
```

### HTTP Request

`GET https://api-v2.hellofresh.com.com/ingredients/`

### Headers

`Content-Type: application/json`
`Authorization: Bearer YOUR_TOKEN`

### URL Parameters

Parameter | Type | Description
--------- | ---- | -----------
country   | string   | Country is mandatory for all requests (AT, AU, BE, DE, GB, NL, US)
skip | integer | Number of results to skip
take | integer | Number of results to show
sort | string | Sort by field(s) in the response collection. You can do ASC and DESC by using + and -. Default is +. Ex: ?sort=price,-createdAt
