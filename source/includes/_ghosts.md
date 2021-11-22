# Ghosts

Ghost related endpoints.

## Get ghosts
Ths endpoint will give you the list of all your ghosts.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/ghosts \ 
-H "Content-Type: application/json" \ 
-d '{
  "url":"{{url}}",
  "token":"{{token}}"
}'
```

> **RESPONSE**

```json
[
  {
    "domain": "domainName",
    "service": "serviceName",
    "ghostID": "1",
    "mapID": null
  }
]
```

### HTTP Request

**`POST /api/ghosts`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
url | STRING | YES | Url of the Hive you make request against
token | STRING | YES |

## Add ghosts
Ths endpoint will add ghosts to your service.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/ghosts/add \ 
-H "Content-Type: application/json" \ 
-d '{
  "url":"{{url}}",
  "token":"{{token}}",
  "quantity":"{{quantity}}"
}'
```

> **RESPONSE**

```json
{
  "message": "Success"
}
```

### HTTP Request

**`POST /api/ghosts/add`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
url | STRING | YES | Url of the Hive you make request against
token | STRING | YES |
quantity | STRING | YES |

## Remove ghosts
Ths endpoint will remove ghost by it's ID from service.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/ghosts/remove \ 
-H "Content-Type: application/json" \ 
-d '{
  "url":"{{url}}",
  "token":"{{token}}",
  "ghostID":"{{ghostID}}"
}'
```

> **RESPONSE**

```json
{
  "message": "Success"
}
```

### HTTP Request

**`POST /api/ghosts/remove`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
url | STRING | YES | Url of the Hive you make request against
token | STRING | YES |
ghostID | STRING | YES |

## Untied ghosts
Ths endpoint will give the list of ghosts waiting for your approval.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/ghosts/untied \ 
-H "Content-Type: application/json" \ 
-d '{
  "url":"{{url}}",
  "token":"{{token}}",
  "username":"{{username}}"
}'
```

> **RESPONSE**

```json
[
  {
    "domain": "domainName",
    "service": "serviceName",
    "ghostID": "1"
  }
]
```

### HTTP Request

**`POST /api/ghosts/untied`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
url | STRING | YES | Url of the Hive you make request against
token | STRING | YES |
username | STRING | YES |

## Accept ghost
Ths endpoint will accept ghost.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/ghosts/accept \ 
-H "Content-Type: application/json" \ 
-d '{
  "url":"{{url}}",
  "token":"{{token}}",
  "username":"{{username}}",
  "ghostID":"{{ghostID}}"
}'
```

> **RESPONSE**

```json
{
  "message": "Success"
}
```

> Server got your request, but something went wrong

```json
{
  "error": "Error"
}
```

### HTTP Request

**`POST /api/ghosts/accept`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
url | STRING | YES | Url of the Hive you make request against
token | STRING | YES |
username | STRING | YES |
ghostID | STRING | YES |

## Reject ghost
Ths endpoint will reject ghost.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/ghosts/reject \ 
-H "Content-Type: application/json" \ 
-d '{
  "url":"{{url}}",
  "token":"{{token}}",
  "username":"{{username}}",
  "ghostID":"{{ghostID}}"
}'
```

> **RESPONSE**

```json
{
  "message": "Success"
}
```

> Server got your request, but something went wrong

```json
{
  "error": "Error"
}
```

### HTTP Request

**`POST /api/ghosts/reject`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
url | STRING | YES | Url of the Hive you make request against
token | STRING | YES |
username | STRING | YES |
ghostID | STRING | YES |

## Ghost status
Ths endpoint will give you the ghost status.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/ghosts/status \ 
-H "Content-Type: application/json" \ 
-d '{
  "url":"{{url}}",
  "token":"{{token}}",
  "username":"{{username}}",
  "ghostID":"{{ghostID}}"
}'
```

> **RESPONSE**

```json
{
  "Linked To": {
    "test/example": true,
    // ...
  },
  "Secondary Service": {
    "domain/service/objectID": true,
    // ...
  },
  "Read Access": {
    "username": true,
    // ...
  },
  "Linked From": {
    "CRYPTO/EXAMPLE": true,
    // ...
  }
}
```

> Server got your request, but something went wrong

```json
{
  "error": "Error"
}
```

### HTTP Request

**`POST /api/ghosts/status`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
url | STRING | YES | Url of the Hive you make request against
token | STRING | YES |
username | STRING | YES |
ghostID | STRING | YES |

## Add mapID to a ghost
Ths endpoint will add custom mapID to a ghost.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/ghosts/add-map-id \ 
-H "Content-Type: application/json" \ 
-d '{
  "url":"{{url}}",
  "token":"{{token}}",
  "ghostID":"{{ghostID}}",
  "mapID":"{{mapID}}"
}'
```

> **RESPONSE**

```json
{
  "message": "Success"
}
```

### HTTP Request

**`POST /api/ghosts/add-map-id`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
url | STRING | YES | Url of the Hive you make request against
token | STRING | YES |
ghostID | STRING | YES |
mapID | false | Your custom unique ID for the ghost

## Generate mapID to a ghost
Ths endpoint will generate mapID to a ghost.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/ghosts/generate-map-id \ 
-H "Content-Type: application/json" \ 
-d '{
  "url":"{{url}}",
  "token":"{{token}}",
  "ghostID":"{{ghostID}}"
}'
```

> **RESPONSE**

```json
{
  "message": "Success"
}
```

### HTTP Request

**`POST /api/ghosts/generate-map-id`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
url | STRING | YES | Url of the Hive you make request against
token | STRING | YES |
ghostID | STRING | YES |

## Transfer ownership of a ghost
Ths endpoint will change owner of a ghost, new user should accept or rejcet the ghost.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/ghosts/transfer \ 
-H "Content-Type: application/json" \ 
-d '{
  "url":"{{url}}",
  "token":"{{token}}",
  "username":"{{username}}",
  "ghostID":"{{ghostID}}",
  "newOwnerUsername":"{{username_2}}"
}'
```

> **RESPONSE**

```json
{
  "message": "Success"
}
```

### HTTP Request

**`POST /api/ghosts/transfer`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
url | STRING | YES | Url of the Hive you make request against
token | STRING | YES |
username | STRING | YES |
ghostID | STRING | YES |
newOwnerUsername | STRING | YES |

## Disable data of a ghost
Ths endpoint will disable incomming data for a ghost.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/ghosts/disable-data \ 
-H "Content-Type: application/json" \ 
-d '{
  "url":"{{url}}",
  "token":"{{token}}",
  "ghostID":"{{ghostID}}"
}'
```

> **RESPONSE**

```json
{
  "message": "Success"
}
```

### HTTP Request

**`POST /api/ghosts/disable-data`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
url | STRING | YES | Url of the Hive you make request against
token | STRING | YES |
ghostID | STRING | YES |

## Allow ghost to be linkable
Ths endpoint will allow ghost to share data with primary service who added link to it.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/ghosts/allow-link \ 
-H "Content-Type: application/json" \ 
-d '{
  "url":"{{url}}",
  "token":"{{token}}",
  "ghostID":"{{ghostID}}",
  "linkedFrom":"{{linkedFrom}}"
}'
```

> **RESPONSE**

```json
{
  "message": "Success"
}
```

### HTTP Request

**`POST /api/ghosts/allow link`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
url | STRING | YES | Url of the Hive you make request against
token | STRING | YES |
ghostID | STRING | YES |
linkedFrom | STRING | YES | `domainName/serviceName`

## Deny ghost to be linkable
Ths endpoint will deny ghost to share data with primary service who added link to it.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/ghosts/deny-link \ 
-H "Content-Type: application/json" \ 
-d '{
  "url":"{{url}}",
  "token":"{{token}}",
  "ghostID":"{{ghostID}}",
  "linkedFrom":"{{linkedFrom}}"
}'
```

> **RESPONSE**

```json
{
  "message": "Success"
}
```

### HTTP Request

**`POST /api/ghosts/deny-link`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
url | STRING | YES | Url of the Hive you make request against
token | STRING | YES |
ghostID | STRING | YES |
linkedFrom | STRING | YES | `domainName/serviceName`

## Add ghost to primary
Ths endpoint will add ghost to a primary service ghost.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/ghosts/add-primary \ 
-H "Content-Type: application/json" \ 
-d '{
  "url":"{{url}}",
  "token":"{{token}}",
  "ghostID":"{{ghostID}}",
  "refDomain":"{{refDomain}}",
  "refService":"{{refService}}",
  "refGhostID":"{{refGhostID}}"
}'
```

> **RESPONSE**

```json
{
  "message": "Success"
}
```

### HTTP Request

**`POST /api/ghosts/add-primary`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
url | STRING | YES | Url of the Hive you make request against
token | STRING | YES |
ghostID | STRING | YES |
refDomain | STRING | YES |
refService | STRING | YES |
refGhostID | STRING | YES |

## Remove ghost from primary
Ths endpoint will remove ghost from a primary service ghost.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/ghosts/remove-primary \ 
-H "Content-Type: application/json" \ 
-d '{
  "url":"{{url}}",
  "token":"{{token}}",
  "ghostID":"{{ghostID}}",
  "refDomain":"{{refDomain}}",
  "refService":"{{refService}}",
  "refGhostID":"{{refGhostID}}"
}'
```

> **RESPONSE**

```json
{
  "message": "Success"
}
```

### HTTP Request

**`POST /api/ghosts/add-primary`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
url | STRING | YES | Url of the Hive you make request against
token | STRING | YES |
ghostID | STRING | YES |
refDomain | STRING | YES |
refService | STRING | YES |
refGhostID | STRING | YES |

## Give read access
Ths endpoint will give another user a read access to an object he doesn't own.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/ghosts/give-read-access \ 
-H "Content-Type: application/json" \ 
-d '{
  "url":"{{url}}",
  "token":"{{token}}",
  "username":"{{username}}",
  "ghostID":"{{ghostID}}"
}'
```

> **RESPONSE**

```json
{
  "message": "Success"
}
```

### HTTP Request

**`POST /api/ghosts/give-read-access`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
url | STRING | YES | Url of the Hive you make request against
token | STRING | YES |
username | STRING | YES | who will get read access
ghostID | STRING | YES |

## Remove read access
Ths endpoint will remove from another user a read access to an object he doesn't own.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/ghosts/remove-read-access \ 
-H "Content-Type: application/json" \ 
-d '{
  "url":"{{url}}",
  "token":"{{token}}",
  "username":"{{username}}",
  "ghostID":"{{ghostID}}"
}'
```

> **RESPONSE**

```json
{
  "message": "Success"
}
```

### HTTP Request

**`POST /api/ghosts/remove-read-access`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
url | STRING | YES | Url of the Hive you make request against
token | STRING | YES |
username | STRING | YES | from who to remove read access
ghostID | STRING | YES |
