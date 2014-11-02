# API

Brief description of end-point

#### Page Navigation

* [Overview](#overview)
    * [Uri](#uri)
    * [Available Methods](#available-methods)
    * [Object](#object)
* [Examples](#examples)
    * [GET List](#get-list)
    * [GET Resource](#get-a-single-resource)
    * [POST Resource](#post-create-resource)
    * [PUT Resource](#put-update-resource)
    
---

## Overview

### Uri

`/uri[/id]`

### Available methods

`GET` / `POST` / `PUT`

### Object

```javascript

	{
        "key-name": {type},
        ...
	}

```

- - -

### Examples

#### [GET] list

Returns a collection of resoure objects

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

Usually first property with be `id` with newly created value 

```javascript

	{
        "key-name": {type},
        ...
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
