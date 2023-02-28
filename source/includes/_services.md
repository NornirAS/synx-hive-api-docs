# Services

Service related endpoints.

## Get services
This endpoint will give you the list of all your services.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/services \ 
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
  "data": [
    {
      "domain": "example",
      "service": "example",
      "dataSchema": "<RTW><TXT></TXT></RTW>",
      "ghosts": "0",
      "commandSchema": "<CMD><ACTION></ACTION><PARAM1></PARAM1><PARAM2></PARAM2></CMD>",
      "timeout": "90",
      "postScript": "aGVsbG8=",
      "preScript": "aGVsbG8="
    }
  ],
  "error": false,
  "message": "Success"
}
```

> Server got your request, but something went wrong

```json
{
  "data": null,
  "error": true,
  "message": "Backend did not understand your request.",
}
```

### HTTP Request

**`POST /api/services`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
domain | STRING | YES |
rootDomain | STRING | YES | For example cioty.com
token | STRING | YES |

## Create service
This endpoint will create a service.

<aside class="notice">
This endpoint can be used only by the root domain owner as it require authToken.
</aside>

### HTTP Request

**`POST /api/services/create`**

### Query Parameters

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/services/create \ 
-H "Content-Type: application/json" \ 
-d '{
  "domain":"{{domain}}",
  "rootDomain":"{{rootDomain}}",
  "service":"{{service}}",
  "token":"{{token}}",
  "username":"{{username}}",
  "authToken":"{{authToken}}",
  "dataSchema":"{{dataSchema}}",
  "commandSchema":"{{commandSchema}}",
  "timeout":"{{timeout}}",
  "preScript":"{{preScript}}",
  "postScript":"{{postScript}}",
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
  "message": "Backend did not understand your request.",
}
```

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
domain | STRING | YES |
rootDomain | STRING | YES | For example cioty.com
service | STRING | YES |
token | STRING | YES |
username | STRING | YES | 
authToken | STRING | YES |
dataSchema | STRING | YES | See example below
commandSchema | STRING | NO | See example below
timeout | STRING, NUMBER | YES | Time in seconds when connection will go idle withou incomming data `Default: 30`
preScript | STRING | NO | `BASE64` encoded JavaScript code that will transform data before it's get to the service 
postScript | STRING | NO | `BASE64` encoded JavaScript code that will transform data when data will leave a service

### Examples

**Service schema**

Data elements should be between RTW tags.

`<RTW><DATA_ONE></DATA_ONE><DATA_TWO></DATA_TWO></RTW>`


**Command schema**

Command elements should be between CMD tags.

`<CMD><ACTION></ACTION><PARAM1></PARAM1><PARAM2></PARAM2></CMD>`

## Update service
This endpoint will update a service.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/services/update \ 
-H "Content-Type: application/json" \ 
-d '{
  "domain":"{{domain}}",
  "rootDomain":"{{rootDomain}}",
  "service":"{{service}}",
  "token":"{{token}}",
  "dataSchema":"{{dataSchema}}",
  "commandSchema":"{{commandSchema}}",
  "timeout":"{{timeout}}",
  "preScript":"{{preScript}}",
  "postScript":"{{postScript}}",
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
  "message": "Backend did not understand your request.",
}
```

### HTTP Request

**`POST /api/services/update`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
domain | STRING | YES |
rootDomain | STRING | YES | For example cioty.com
service | STRING | YES |
token | STRING | YES |
authToken | STRING | YES |
dataSchema | STRING | YES | See example below
commandSchema | STRING | NO | See example below
timeout | STRING, NUMBER | YES | Time in seconds when connection will go idle withou incomming data `Default: 30`
preScript | STRING | NO | `BASE64` encoded JavaScript code that will transform data before it's get to the service 
postScript | STRING | NO | `BASE64` encoded JavaScript code that will transform data when data will leave a service

## Remove service
This endpoint will remove a service.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/services/remove \ 
-H "Content-Type: application/json" \ 
-d '{
  "domain":"{{domain}}",
  "rootDomain":"{{rootDomain}}",
  "service":"{{service}}",
  "token":"{{token}}"
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
  "message": "Backend did not understand your request.",
}
```

### HTTP Request

**`POST /api/services/remove`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
domain | STRING | YES |
rootDomain | STRING | YES | For example cioty.com
service | STRING | YES |
token | STRING | YES |

<!-- ## Get micropage data
This endpoint will give micropage data.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/services/micropage \ 
-H "Content-Type: application/json" \ 
-d '{
  "domain":"{{domain}}",
  "rootDomain":"{{rootDomain}}",
  "service":"{{service}}"
}'
```

> **RESPONSE**

```json
{
  "serviceDescription": "description",
  "schemaDescription": {
    "description": "Overall description of your data schema",
    "elements": [
      {
        "element": "element name",
        "description": "element descrition"
      }
    ]
  },
  "commandDescription": {
    "description": "Overall description of your command schema",
    "headers": ["Command", "Param1", "Param2", "Description"],
    "commands": [
      {
        "command": "turn on",
        "param1": "id",
        "param2": "color",
        "description": "Command will turn on lamp with id 1 with red color"
      }
    ]
  },
  "imageUrl": "https://cdn.pixabay.com/photo/2015/04/23/22/00/tree-736885__480.jpg"
}
```

### HTTP Request

**`POST /api/services/micropage`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
domain | STRING | YES |
rootDomain | STRING | YES | For example cioty.com
service | STRING | YES |

## Update micropage
This endpoint will update a service micropage.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/services/micropage-update \ 
-H "Content-Type: application/json" \ 
-d '{
  "domain":"{{domain}}",
  "rootDomain":"{{rootDomain}}",
  "service":"{{service}}"
  "token":"{{token}}",
  "description":"{{serviceDescription}}",
  "imageURL":"{{imageUrl}}",
  "schemaDescription":"{{schemaDescription}}",
  "commandDescription":"{{commandDescription}}"
}'
```

> **RESPONSE**

```json
{
  "message": "Success"
}
```

### HTTP Request

**`POST /api/services/micropage-update`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
domain | STRING | YES |
rootDomain | STRING | YES | For example cioty.com
service | STRING | YES |
token | STRING | YES |
serviceDescription | STRING | NO |
schemaDesciption | OBJECT | NO | Stringified. See example below
commandDescription | OBJECT | NO | Stringified. See example below
imageUrl | STRING | NO | Image which can represent service

### Example

> **Schema description OBJECT**

```json
{
  "schemaDescription": {
    "description": "Overall description of your data schema",
    "elements": [
      {
        "element": "element name",
        "description": "element descrition"
      }
    ]
  },
}
```

> **Command description OBJECT**

```json
{
  "commandDescription": {
    "description": "Overall description of your command schema",
    "headers": ["Command", "Param1", "Param2", "Description"],
    "commands": [
      {
        "command": "turn on",
        "param1": "id",
        "param2": "color",
        "description": "Command will turn on lamp with id 1 with red color"
      }
    ]
  }
}
``` -->

## Get links
This endpoint will add links.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/services/links \ 
-H "Content-Type: application/json" \
-d '{
  "domain":"{{domain}}",
  "rootDomain":"{{rootDomain}}",
  "service":"{{service}}",
  "token":"{{token}}"
}'
```

> **RESPONSE**

```json
{
  "data": [{
    "serviceAddress": "domain/service",
    "active": true
  },
  // ...
  ],
  "error": false,
  "message": "Success"
}
```

### HTTP Request

**`POST /api/services/links`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
domain | STRING | YES |
rootDomain | STRING | YES | For example cioty.com
service | STRING | YES |
token | STRING | YES |


## Update links
This endpoint will add links.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/services/links/update \ 
-H "Content-Type: application/json" \
-d '{
  "domain":"{{domain}}",
  "rootDomain":"{{rootDomain}}",
  "service":"{{service}}",
  "token":"{{token}}",
  "links":{{links}}
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
  "message": "Backend did not understand your request.",
}
```

### HTTP Request

**`POST /api/services/links/update`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
domain | STRING | YES |
rootDomain | STRING | YES | For example cioty.com
service | STRING | YES |
token | STRING | YES |
links | STRING[] | YES | Array where each link is a `STRING`, link is written as `domain/service`

## Add ghosts
Ths endpoint will add ghosts to your service.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/services/ghosts/add \ 
-H "Content-Type: application/json" \ 
-d '{
  "domain":"{{domain}}",
  "rootDomain":"{{rootDomain}}",
  "service":"{{service}}",
  "token":"{{token}}",
  "quantity":"{{quantity}}"
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
  "message": "Backend did not understand your request.",
}
```

### HTTP Request

**`POST /api/services/ghosts/add`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
domain | STRING | YES |
rootDomain | STRING | YES | For example cioty.com
service | STRING | YES |
token | STRING | YES |
quantity | STRING, NUMBER | YES |