# Ghosts

Ghost related endpoints.

## Get ghosts
Ths endpoint will give you the list of all your ghosts.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/ghosts \ 
-H "Content-Type: application/json" \ 
-d '{
  "domain":"{{domain}}",
  "rootDomain":"{{rootDomain}}",
  "token":"{{token}}"
}'
```

> **RESPONSE**

```json
{
  "data":[
    {
      "domain": "domain",
      "service": "service",
      "ghostID": "1",
      "mapID": null
    }
  ],
  "error": false,
  "message": "Success"
}
```

### HTTP Request

**`POST /api/ghosts`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
domain | STRING | YES |
rootDomain | STRING | YES | For example cioty.com
token | STRING | YES |

## Remove ghosts
Ths endpoint will remove ghost by it's ID from service.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/ghosts/delete \ 
-H "Content-Type: application/json" \ 
-d '{
  "domain":"{{domain}}",
  "rootDomain":"{{rootDomain}}",
  "service":"{{service}}",
  "token":"{{token}}",
  "ghostID":"{{ghostID}}"
}'
```

> **RESPONSE**

```json
{
  "data": null,
  "error": false,
  "message": "Success"
}
```

### HTTP Request

**`POST /api/ghosts/delete`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
domain | STRING | YES |
rootDomain | STRING | YES | For example cioty.com
service | STRING | YES |
token | STRING | YES |
ghostID | STRING | YES |

## Untied ghosts
Ths endpoint will give the list of ghosts waiting for your approval.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/ghosts/pending \ 
-H "Content-Type: application/json" \ 
-d '{
  "domain":"{{domain}}",
  "rootDomain":"{{rootDomain}}",
  "token":"{{token}}",
  "username":"{{username}}"
}'
```

> **RESPONSE**

```json
{
  "data":[
    {
      "domain": "domain",
      "service": "service",
      "ghostID": "1"
    }
  ],
  "error": false,
  "message": "Success"
}
```

### HTTP Request

**`POST /api/ghosts/pending`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
domain | STRING | YES |
rootDomain | STRING | YES | For example cioty.com
service | STRING | YES |
token | STRING | YES |
username | STRING | YES |

## Accept ghost
Ths endpoint will accept ghost.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/ghosts/pending/accept \ 
-H "Content-Type: application/json" \ 
-d '{
  "domain":"{{domain}}",
  "rootDomain":"{{rootDomain}}",
  "service":"{{service}}",
  "token":"{{token}}",
  "username":"{{username}}",
  "ghostID":"{{ghostID}}"
}'
```

> **RESPONSE**

```json
{
  "data": null,
  "error": false,
  "message": "Success"
}
```

> Server got your request, but something went wrong

```json
{
  "data": null,
  "error": true,
  "message": "Somethin went wrong",
}
```

### HTTP Request

**`POST /api/ghosts/pending/accept`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
domain | STRING | YES |
rootDomain | STRING | YES | For example cioty.com
service | STRING | YES |
token | STRING | YES |
username | STRING | YES |
ghostID | STRING | YES |

## Reject ghost
Ths endpoint will reject ghost.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/ghosts/pending/reject \ 
-H "Content-Type: application/json" \ 
-d '{
  "domain":"{{domain}}",
  "rootDomain":"{{rootDomain}}",
  "service":"{{service}}",
  "token":"{{token}}",
  "username":"{{username}}",
  "ghostID":"{{ghostID}}"
}'
```

> **RESPONSE**

```json
{
  "data": null,
  "error": false,
  "message": "Success"
}
```

> Server got your request, but something went wrong

```json
{
  "data": null,
  "error": true,
  "message": "Somethin went wrong",
}
```

### HTTP Request

**`POST /api/ghosts/pending/reject`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
domain | STRING | YES |
rootDomain | STRING | YES | For example cioty.com
service | STRING | YES |
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
  "domain":"{{domain}}",
  "rootDomain":"{{rootDomain}}",
  "service":"{{service}}",
  "token":"{{token}}",
  "username":"{{username}}",
  "ghostID":"{{ghostID}}"
}'
```

> **RESPONSE**

```json
{
  "data": {
    "morphedGhosts": [
      {
        "ghostAddress": "hello/world/1",
        "active": true
      }
    ],
    "readAccess": [
      {
        "email": "john@example.com",
        "active": true
      }
    ],
    "linkedTo": [
      {
        "serviceAddress": "hello/world",
        "active": true
      }
    ],
    "linkedFrom": [
      {
        "serviceAddress": "hello/world",
        "active": true
      }
    ]
  },
  "error": false,
  "message": "Success",
}
```

> Server got your request, but something went wrong

```json
{
  "data": null,
  "error": true,
  "message": "Somethin went wrong",
}
```

### HTTP Request

**`POST /api/ghosts/status`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
domain | STRING | YES |
rootDomain | STRING | YES | For example cioty.com
service | STRING | YES |
token | STRING | YES |
username | STRING | YES |
ghostID | STRING | YES |

## Add mapID to a ghost
Ths endpoint will add custom mapID to a ghost.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/ghosts/map-id/add \ 
-H "Content-Type: application/json" \ 
-d '{
  "domain":"{{domain}}",
  "rootDomain":"{{rootDomain}}",
  "service":"{{service}}",
  "token":"{{token}}",
  "ghostID":"{{ghostID}}",
  "mapID":"{{mapID}}"
}'
```

> **RESPONSE**

```json
{
  "data": null,
  "error": false,
  "message": "Success"
}
```

### HTTP Request

**`POST /api/ghosts/map-id/add`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
domain | STRING | YES |
rootDomain | STRING | YES | For example cioty.com
service | STRING | YES |
token | STRING | YES |
ghostID | STRING | YES |
mapID | false | Your custom unique ID for the ghost

## Generate mapID to a ghost
Ths endpoint will generate mapID to a ghost.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/ghosts/map-id/generate \ 
-H "Content-Type: application/json" \ 
-d '{
  "domain":"{{domain}}",
  "rootDomain":"{{rootDomain}}",
  "service":"{{service}}",
  "token":"{{token}}",
  "ghostID":"{{ghostID}}"
}'
```

> **RESPONSE**

```json
{
  "data": null,
  "error": false,
  "message": "Success"
}
```

### HTTP Request

**`POST /api/ghosts/map-id/generate`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
domain | STRING | YES |
rootDomain | STRING | YES | For example cioty.com
service | STRING | YES |
token | STRING | YES |
ghostID | STRING | YES |

## Transfer ownership of a ghost
Ths endpoint will change owner of a ghost, new user should accept or rejcet the ghost.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/ghosts/transfer \ 
-H "Content-Type: application/json" \ 
-d '{
  "domain":"{{domain}}",
  "rootDomain":"{{rootDomain}}",
  "service":"{{service}}",
  "token":"{{token}}",
  "username":"{{username}}",
  "ghostID":"{{ghostID}}",
  "newOwnerUsername":"{{username_2}}"
}'
```

> **RESPONSE**

```json
{
  "data": null,
  "error": false,
  "message": "Success"
}
```

### HTTP Request

**`POST /api/ghosts/transfer`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
domain | STRING | YES |
rootDomain | STRING | YES | For example cioty.com
service | STRING | YES |
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
  "domain":"{{domain}}",
  "rootDomain":"{{rootDomain}}",
  "service":"{{service}}",
  "token":"{{token}}",
  "ghostID":"{{ghostID}}"
}'
```

> **RESPONSE**

```json
{
  "data": null,
  "error": false,
  "message": "Success"
}
```

### HTTP Request

**`POST /api/ghosts/disable-data`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
domain | STRING | YES |
rootDomain | STRING | YES | For example cioty.com
service | STRING | YES |
token | STRING | YES |
ghostID | STRING | YES |

## Allow ghost to be linkable
Ths endpoint will allow ghost to share data with primary service who added link to it.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/ghosts/link/allow \ 
-H "Content-Type: application/json" \ 
-d '{
  "domain":"{{domain}}",
  "rootDomain":"{{rootDomain}}",
  "service":"{{service}}",
  "token":"{{token}}",
  "ghostID":"{{ghostID}}",
  "linkedFrom":"{{linkedFrom}}"
}'
```

> **RESPONSE**

```json
{
  "data": null,
  "error": false,
  "message": "Success"
}
```

### HTTP Request

**`POST /api/ghosts/link/allow`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
domain | STRING | YES |
rootDomain | STRING | YES | For example cioty.com
service | STRING | YES |
token | STRING | YES |
ghostID | STRING | YES |
linkedFrom | STRING | YES | `domain/service`

## Deny ghost to be linkable
Ths endpoint will deny ghost to share data with primary service who added link to it.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/ghosts/link/deny \ 
-H "Content-Type: application/json" \ 
-d '{
  "domain":"{{domain}}",
  "rootDomain":"{{rootDomain}}",
  "service":"{{service}}",
  "token":"{{token}}",
  "ghostID":"{{ghostID}}",
  "linkedFrom":"{{linkedFrom}}"
}'
```

> **RESPONSE**

```json
{
  "data": null,
  "error": false,
  "message": "Success"
}
```

### HTTP Request

**`POST /api/ghosts/link/deny`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
domain | STRING | YES |
rootDomain | STRING | YES | For example cioty.com
service | STRING | YES |
token | STRING | YES |
ghostID | STRING | YES |
linkedFrom | STRING | YES | `domain/service`

## Add morphed Ghost
Ths endpoint will add ghost to current ghost. User able to receive data from morphed ghosts.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/ghosts/morphed/add \ 
-H "Content-Type: application/json" \ 
-d '{
  "domain":"{{domain}}",
  "rootDomain":"{{rootDomain}}",
  "service":"{{service}}",
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
  "data": null,
  "error": false,
  "message": "Success"
}
```

### HTTP Request

**`POST /api/ghosts/morphed/add`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
domain | STRING | YES |
rootDomain | STRING | YES | For example cioty.com
service | STRING | YES |
token | STRING | YES |
ghostID | STRING | YES |
refDomain | STRING | YES |
refService | STRING | YES |
refGhostID | STRING | YES |

## Remove morphed Ghost
Ths endpoint will romove ghost current current ghost. User will no longer receive data from removed morphed ghosts.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/ghosts/morphed/remove \ 
-H "Content-Type: application/json" \ 
-d '{
  "domain":"{{domain}}",
  "rootDomain":"{{rootDomain}}",
  "service":"{{service}}",
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
  "data": null,
  "error": false,
  "message": "Success"
}
```

### HTTP Request

**`POST /api/ghosts/morphed/remove`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
domain | STRING | YES |
rootDomain | STRING | YES | For example cioty.com
service | STRING | YES |
token | STRING | YES |
ghostID | STRING | YES |
refDomain | STRING | YES |
refService | STRING | YES |
refGhostID | STRING | YES |

## Add read access
Ths endpoint will give another user a read access to an object he doesn't own.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/ghosts/read-access/add \ 
-H "Content-Type: application/json" \ 
-d '{
  "domain":"{{domain}}",
  "rootDomain":"{{rootDomain}}",
  "service":"{{service}}",
  "token":"{{token}}",
  "username":"{{username}}",
  "ghostID":"{{ghostID}}"
}'
```

> **RESPONSE**

```json
{
  "data": null,
  "error": false,
  "message": "Success"
}
```

### HTTP Request

**`POST /api/ghosts/read-access/add`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
domain | STRING | YES |
rootDomain | STRING | YES | For example cioty.com
service | STRING | YES |
token | STRING | YES |
username | STRING | YES | who will get read access
ghostID | STRING | YES |

## Remove read access
Ths endpoint will remove from another user a read access to an object he doesn't own.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/ghosts/read-access/remove \ 
-H "Content-Type: application/json" \ 
-d '{
  "domain":"{{domain}}",
  "rootDomain":"{{rootDomain}}",
  "service":"{{service}}",
  "token":"{{token}}",
  "username":"{{username}}",
  "ghostID":"{{ghostID}}"
}'
```

> **RESPONSE**

```json
{
  "data": null,
  "error": false,
  "message": "Success"
}
```

### HTTP Request

**`POST /api/ghosts/read-access/remove`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
domain | STRING | YES |
rootDomain | STRING | YES | For example cioty.com
service | STRING | YES |
token | STRING | YES |
username | STRING | YES | from who to remove read access
ghostID | STRING | YES |
