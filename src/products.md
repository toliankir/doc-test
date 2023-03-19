## Add product application

```
POST /uploads/organizations/product/application
```

**Parameters**

| **Name** | **Type** | **Mandatory** | **Description** |
|----------|----------|---------------|-----------------|
| **entityId** | NUMBER | YES | Entity id of external system |
| **name** | STRING | YES | Product name |
| **avatar** | STRING | NO | Product logo link, must be valid url |
| **raiting** | NUMBER | NO | Product raiting | 
| **appLink** | STRING | YES | Product website link, must be valid url |
| **category** | STRING | NO | Product category |
| **downloads** | NUMBER | NO | Product downloads count |
| **appLaunchDate** | DATE | NO | Product lanch date, must be in valid date format | 
| **reviews** | NUMBER | NO | Product reviews count | 
| **fullDescription** | STRING | NO | Product description |

**Request**

Upload products and link it to companies

```json
[
    {
        "entityId": 123,
        "name": "Test product",
        "appLink": "http://www.google.com",
        "organizations": ["b243e228-1744-4b00-878c-26755ce2be7e"]
    },
    {
        "entityId": 124,
        "name": "Test product 2",
        "appLink": "http://www.facebook.com",
        "organizations": ["b243e228-1744-4b00-878c-26755ce2be7e"]
    },
    ...
]
```

**Response**
```json
{
    "message": "Product appliaction was added!",
    "data": [
        {
            "uuid": "8f29b5d5-20f3-4ee8-a389-cd2b1c01bba5",
            "id": 123
        },
        {
            "uuid": "8f29b5d5-20f3-4ee8-a389-cd2b1c01bba5",
            "id": 124
        },
        ...
    ]
}
```
___

## Update product application

Update existing products by uniqe uuids

```
PATCH /uploads/organizations/product/application
```

**Parameters**

| **Name** | **Type** | **Mandatory** | **Description** |
|----------|----------|---------------|-----------------|
| **uuid** | STRING | YES | Unqie product id, must be valid uuid |
| **name** | STRING |  NO | Product name |
| **avatar** | STRING | NO | Product logo link, must be valid url |
| **raiting** | NUMBER | NO | Product raiting | 
| **appLink** | STRING |  NO | Product website link, must be valid url |
| **category** | STRING | NO | Product category |
| **downloads** | NUMBER | NO | Product downloads count |
| **appLaunchDate** | DATE | NO | Product lanch date, must be in valid date format | 
| **reviews** | NUMBER | NO | Product reviews count | 
| **fullDescription** | STRING | NO | Product description |

!!! note "Update relation to organizations"

    Note, that new list of organization relations fully rewrite all product relations and erase all previous.

```json
{
    "message": "Product appliaction was added!",
    "data": [
        {
            "uuid": "8f29b5d5-20f3-4ee8-a389-cd2b1c01bba5",
            "name": "Test product",
            "appLink": "http://www.google.com",
            "organizations": ["b243e228-1744-4b00-878c-26755ce2be7e", "3a3c41d3-b59e-45d2-95bc-5e6bbafb7e72"],
            "fullDescription": "Some full description",
            "downloads": 321,
            "avatar": "http://avatar.com/logo.jpg"
        },
        {
            "uuid": "df5713d6-e94c-4087-9790-7d296853fe6f",
            "name": "New product name"
        },
        ...
    ]
}
```

**Response**
```json
{
    "message": "Product appliaction was updated!",
    "data": [
        {
            "uuid": "8f29b5d5-20f3-4ee8-a389-cd2b1c01bba5"
        },
        {
            "uuid": "df5713d6-e94c-4087-9790-7d296853fe6f"
        },
        ...
    ]
}
```