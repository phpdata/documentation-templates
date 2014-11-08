# API

Brief description of `user` end-point

#### Page Navigation

* [Overview](#overview)
    * [Uri](#uri)
    * [Available Methods](#available-methods)
    * [Object](#object)
    * [Status Codes](#status-codes)
* [Methods](#methods)
    * [GET List](#get-list-users)
    * [GET User](#get-a-single-user)
    * [POST User](#post-create-user)
    * [PUT User](#put-update-user)
    * [DELETE Resource](#delete-resource)
    
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

### Status Codes

Response status code used on this end point.

| Code | Description | Methods | Notes |
| ---- | ----------- | ------- | ----- |
| 200 | Successful | GET / POST / PUT | OK |
| 201 | Created successfully | POST | OK |
| 204 | Successful | DELETE | OK but no content |
| 304 | Not modified, can use cache | GET | Use cached version |
| 400 | Invalid parameters | GET / POST / PUT | Response will contain error message. Update your request & try again |
| 401 | Unauthorized | GET / POST / PUT / DELETE | Login & try again |
| 403 | Forbidden | GET / POST / PUT / DELETE | You do not have permissions |
| 404 | Not found | GET / POST / PUT / DELETE | Failed |
| 500 | Internal Server Error | GET / POST / PUT | Failed |

- - -

### Methods

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

##### Error Response (invalid request)

Response code `404`

Resource not found

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

##### Error Response (invalid request)

Response code `400`

Should return the requesting object & errors for which field 

```javascript

	{
        "name": "Mickey Mouse",
        "email": "mickey-mouse.com",
        "errors": {
            "email": "Invalid email address"
        }
    }
```

#### [PUT] update user

Update a single user

[PUT] `/api/user/1`

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

##### Error Response (invalid request)

Response code `400`

Should return the requesting object & errors for which field 

```javascript

	{
	    "id": 1,
        "name": "Mickey Mouse",
        "email": "mickey-mouse.com",
        "errors": {
            "email": "Invalid email address"
        }
    }
```

#### [DELETE] delete resource

Delete a single resource

[DELETE] `/uri/1`

##### Request

No body required

##### Response

Response code `204`

Successful, no response returned. Response code is sufficient. 

##### Error Response (invalid request)

Response code `404`

Resource not found

#### [PATCH] Partial update resource

Coming soon...

#### [HEAD] Get resource

This is similar to a **GET** a single resource but no body is returned.
An example of the use of this RESTful Vert, is to check weather a Resource has changed without actually get the Resource body (caching)

[HEAD] `/uri/1`

##### Response

Response code `200`

```
NO BODY
```

##### Error Response (invalid request)

Response code `404`

Resource not found

```
NO BODY
```

#### [OPTIONS] Methods available

Coming soon...
