## Joke

This is our Joke API. You can use this API to request
and create different jokes with different categories

### Retrieve all jokes

Lists all jokes from all categories.

```endpoint
GET /jokes

```

#### Example request

```curl
$ curl https://joke-api-hoang-jevgeni.herokuapp.com/jokes
```

#### Example response

```json
[
  {
    "_id": "{joke_id}",
    "name": "Train and Plane joke",
    "content": "This is the first joke about Train and Plane",
    "categories": ["{category_id}", "{category_id}"],
    "like": 0,
    "dislike": 0,
    "__v": 0
  },
  {
    "_id": "{joke_id}",
    "name": "Train joke",
    "content": "This is the first joke about Train",
    "categories": ["{category_id}"],
    "like": 1,
    "dislike": 2,
    "__v": 0
  }
]
```

### Retrieve a random joke from all jokes

Gets a random joke from all jokes in the database.

```endpoint
GET /jokes/random

```

#### Example request

```curl
$ curl https://joke-api-hoang-jevgeni.herokuapp.com/jokes/random
```

#### Example response

```json
{
  "_id": "{joke_id}",
  "name": "Train joke",
  "content": "This is the first joke about Train",
  "categories": ["{category_id}"],
  "like": 1,
  "dislike": 2,
  "__v": 0
}
```

### Retrieve a random joke from a category

Gets a random joke from a category of joke.

```endpoint
GET /categories/{category_name}/random

```

#### Example request

```curl
$ curl https://joke-api-hoang-jevgeni.herokuapp.com/categories/Train/random
```

#### Example response

```json
{
  "_id": "{joke_id}",
  "name": "Train joke",
  "content": "This is the first joke about Train",
  "categories": ["{category_id}"],
  "like": 1,
  "dislike": 2,
  "__v": 0
}
```

### Retrieve all categories

Lists all categories.

```endpoint
GET /categories

```

#### Example request

```curl
$ curl https://joke-api-hoang-jevgeni.herokuapp.com/categories
```

#### Example response

```json
[
  {
    "_id": "{category_id}",
    "name": "Train",
    "__v": 0
  },
  {
    "_id": "{category_id}",
    "name": "Plane",
    "__v": 0
  },
  {
    "_id": "{category_id}",
    "name": "Bike",
    "__v": 0
  }
]
```

### Retrieve all jokes for a category

Lists all jokes for a category.

```endpoint
GET /categories/{category_name}

```

#### Example request

```curl
$ curl https://joke-api-hoang-jevgeni.herokuapp.com/categories/Plane
```

#### Example response

```json
[
  {
    "_id": "{joke_id}",
    "name": "Train and Plane joke",
    "content": "This is the first joke about Train and Plane",
    "categories": ["{category_id}", "{category_id}"],
    "like": 0,
    "dislike": 0,
    "__v": 0
  }
]
```

### Retrieve a joke

Gets a joke by its id

```endpoint
GET /jokes/{joke_id}

```

#### Example request

```curl
$ curl https://joke-api-hoang-jevgeni.herokuapp.com/jokes/{joke_id}
```

#### Example response

```json
{
  "_id": "{joke_id}",
  "name": "Train and Plane joke",
  "content": "This is the first joke about Train and Plane",
  "categories": ["{category_id}", "{category_id}"],
  "like": 0,
  "dislike": 0,
  "__v": 0
}
```

### Add a new category

Creates a new category.

```endpoint
POST /categories
```

#### Example request

```curl
curl -X POST https://joke-api-hoang-jevgeni.herokuapp.com/categories
```

#### Example request body

```json
{
  "name": "Ship"
}
```

Property | Description
---|---
`name` | the name of the category

#### Example response

```json
{
  "name": "Ship",
  "_id": "{category_id}",
  "__v": 0
}
```

### Add a new joke to a category

Creates a new joke in a category.

```endpoint
POST /categories/{category_name}
```

#### Example request

```curl
curl -X POST https://joke-api-hoang-jevgeni.herokuapp.com/categories/Ship
```

#### Example request body

```json
{
    "name": "Ship and Bike joke",
    "content": "This is the first joke about Ship and Bike"
}
```

Property | Description
---|---
`name` | the name of the joke
`content` | the content of the joke
`like` | (optional) number of like for the joke
`dislike` | (optional) number of dislike for the joke

#### Example response

```json
{
  "name": "Ship and Bike joke",
  "content": "This is the first joke about Ship and Bike",
  "categories": [
    "{category_id}"
  ],
  "like": 0,
  "dislike": 0,
  "_id": "{joke_id}",
  "__v": 0
}
```

### Add existing joke to a category

Add an existing joke to a category.

```endpoint
PATCH /categories/{category_name}/{joke_id}
```

#### Example request

```curl
curl --request PATCH https://joke-api-hoang-jevgeni.herokuapp.com/categories/Bike/{joke_id} \
  -d @data.json
```

#### Example response

```json
{
  "_id": "{joke_id}",
  "name": "Ship and Bike joke",
  "content": "This is the first joke about Ship and Bike",
  "categories": [
    "{category_id}",
    "{category_id}"
  ],
  "like": 0,
  "dislike": 0,
  "__v": 1
}
```

### Give like/dislike to a joke

Gives a joke like or dislike

```endpoint
PATCH /jokes/{joke_id}/favor/{favor_name}
```

#### Example request

```curl
curl --request PATCH https://joke-api-hoang-jevgeni.herokuapp.com/jokes/{joke_id}/favor/like \
  -d @data.json
```

#### Example response

```json
{
  "_id": "{joke_id}",
  "name": "Ship and Bike joke",
  "content": "This is the first joke about Ship and Bike",
  "categories": [
    "{category_id}",
    "{category_id}"
  ],
  "like": 1,
  "dislike": 0,
  "__v": 1
}
```





