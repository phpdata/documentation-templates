# API

Brief description of `user` end-point

#### Page Navigation

* [Overview](#overview)
    * [Uri](#uri)
    * [Available Methods](#available-methods)
    * [Object](#object)
* [Examples](#examples)
    * [GET List](#get-list-users)
    * [GET User](#get-a-single-user)
    * [POST User](#post-create-user)
    * [PUT User](#put-update-user)
    
---

## Overview

### Uri

`/api/user[/id]`

### Available methods

`GET` / `POST` / `PUT`

### Object

```javascript

	{
        "id": {int},
        "name": {string},
        "email": {string}
	}

```

- - -

### Examples

#### [GET] list users

Returns a collection of user objects

[GET] `/api/user`

##### Response

Response code `200`

```javascript

    [
         {
            "id": 1,
            "name": "Mickey Mouse",
            "email": "mickey@mouse.com"
        },
        {
            "id": 2,
            "name": "Minnie Mouse",
            "email": "minnie@mouse.com"
        }
    ]

```

#### [GET] a single user

Returns a user object

[GET] `/api/user/1`

##### Response

Response code `200`

```javascript

	{
        "id": 1,
        "name": "Mickey Mouse",
        "email": "mickey@mouse.com"
	}

```

#### [POST] create user

Create a single user

[POST] `/api/user`

##### Request

```javascript

	{
        "name": "Mickey Mouse",
        "email": "mickey@mouse.com"
	}

```

##### Response

Response code `201`

```javascript

	{
        "id": 1,
        "name": "Mickey Mouse",
        "email": "mickey@mouse.com"
	}

```

#### [PUT] update user

Update a single user

[POST] `/api/user/1`

##### Request

```javascript

	{
        "id": 1,
        "name": "Mickey Mouse",
        "email": "mickey@mouse.com"
	}

```

##### Response

Response code `200`

```javascript

	{
        "id": 1,
        "name": "Mickey Mouse",
        "email": "mickey@mouse.com"
	}

```
