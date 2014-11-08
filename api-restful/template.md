# API

Brief description of end-point

#### Page Navigation

* [Overview](#overview)
    * [Uri](#uri)
    * [Available Methods](#available-methods)
    * [Object](#object)
    * [Status Codes](#status-codes)
* [Methods](#methods)
    * [GET List](#get-list)
    * [GET Resource](#get-a-single-resource)
    * [POST Resource](#post-create-resource)
    * [PUT Resource](#put-update-resource)
    * [DELETE Resource](#delete-resource)
    * [PATCH Resource](#patch-partial-update-resource)
    * [HEAD Resource](#head-get-resource)
    * [OPTIONS Resource](#options-methods-available)
    
---

## Overview

### Uri

`/uri[/id]`

### Available methods

`GET` / `POST` / `PUT` / `DELETE` / `PATCH` / `HEAD` / `OPTIONS`

### Object

```javascript

	{
        "key-name": {type},
        ...
	}

```

### Status Codes

Response status code used on this end point. 

*Below are just some common examples, update accordingly for your end point*

| Code | Description | Methods | Notes |
| ---- | ----------- | ------- | ----- |
| 200 | Successful | GET / POST / PUT | OK |
| 201 | Created successfully | POST | OK |
| 202 | Accepted by the server | POST / PUT | OK, usually used for async |
| 204 | Successful | DELETE | OK but no content |
| 304 | Not modified, can use cache | GET | Use cached version |
| 400 | Invalid parameters | GET / POST / PUT | Response will contain error message. Update your request & try again |
| 401 | Unauthorized | GET / POST / PUT / DELETE | Login & try again |
| 403 | Forbidden | GET / POST / PUT / DELETE | You do not have permissions |
| 404 | Not found | GET / POST / PUT / DELETE | Failed |
| 500 | Internal Server Error | GET / POST / PUT | Failed |

- - -

### Methods

#### [GET] list

Returns a collection of resource objects

[GET] `/uri`

##### Response

Response code `200`

```javascript

    [
         {
            "key-name": {type},
            ...
        },
        {
            "key-name": {type},
            ...
        },
    ]

```

#### [GET] a single

Returns a resource object

[GET] `/uri/[id]`

##### Response

Response code `200`

```javascript

	{
        "key-name": {type},
        ...
	}

```

##### Error Response (invalid request)

Response code `404`

Resource not found

#### [POST] create resource

Create a single resource

[POST] `/uri`

##### Request

```javascript

	{
        "key-name": {type},
        ...
    }

```

##### Response

Response code `201`

Usually first property will be `id` with newly created value 

```javascript

	{
        "key-name": {type},
        ...
    }

```

##### Error Response (invalid request)

Response code `400`

Should return the requesting object & errors for which field 

```javascript

	{
        "key-name": {type},
        ...
        "errors": {
            "key-name": "message"
            ...
        }
    }
```

#### [PUT] update resource

Update a single resource

[PUT] `/uri/[id]`

##### Request

```javascript

	{
        "key-name": {type},
        ...
    }

```

##### Response

Response code `200`

```javascript

	{
        "key-name": {type},
        ...
    }

```

##### Error Response (invalid request)

Response code `400`

Should return the requesting object & errors for which field 

```javascript

	{
        "key-name": {type},
        ...
        "errors": {
            "key-name": "message"
            ...
        }
    }
```

#### [DELETE] delete resource

Delete a single resource

[DELETE] `/uri/[id]`

##### Request

```
NO BODY
```

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

[HEAD] `/uri/[id]`

##### Response

Response code `200`

```
NO BODY
```

##### Error Response (invalid request)

Response code `404`

Resource not found

#### [OPTIONS] Methods available

Coming soon...
