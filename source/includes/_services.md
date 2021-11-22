# Services

Service related endpoints.

## Get services
This endpoint will give you the list of all your services.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/services \ 
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
    "domain": "example",
    "serviceName": "example",
    "serviceSchema": "<RTW><TXT></TXT></RTW>",
    "ghosts": "0",
    "serviceDescription": "VXBkYXRlZA==",
    "keywords": "hello",
    "commandSchema": "<CMD><ACTION></ACTION><PARAM1></PARAM1><PARAM2></PARAM2></CMD>",
    "webJS": "",
    "timeout": "90",
    "postInlineScript": "aGVsbG8=",
    "preInlineScript": "aGVsbG8="
  }
]
```

### HTTP Request

**`POST /api/services`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
url | STRING | YES | Url of the Hive you make request against
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
  "url":"{{url}}",
  "token":"{{token}}",
  "username":"{{username}}",
  "authToken":"{{authToken}}",
  "serviceDescription":"{{serviceDescription}}",
  "keywords":{{keywords}},
  "serviceSchema":"{{serviceSchema}}",
  "commandSchema":"{{commandSchema}}",
  "timeout":"{{timeout}}",
  "inlinePreScript":"{{inlinePreScript}}",
  "inlinePostScript":"{{inlinePostScript}}",
  "webJS":"{{webJS}}"
}'
```

> **RESPONSE**

```json
{
  "message": "Success"
}
```

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
url | STRING | YES | Url of the Hive you make request against
token | STRING | YES |
username | STRING | YES | 
authToken | STRING | YES |
serviceDescription | STRING | NO | `BASE64` encoded
keywords | STRING[] | NO | Array where each keyword is a `STRING`
serviceSchema | STRING | YES | See example below
commandSchema | STRING | NO | See example below
timeout | STRING | YES | Time in seconds when connection will go idle withou incomming data `Default: 30`
inlinePreScript | STRING | NO | `BASE64` encoded JavaScript code that will transform data before it's get to the service 
inlinePostScript | STRING | NO | `BASE64` encoded JavaScript code that will transform data when data will leave a service
webJS | STRING | NO | URL to extarnal stored `CDN` JavaScript code that will visualize the incomming data

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
  "url":"{{url}}",
  "token":"{{token}}",
  "serviceDescription":"{{serviceDescription}}",
  "keywords":"{{keywords}}",
  "serviceSchema":"{{serviceSchema}}",
  "commandSchema":"{{commandSchema}}",
  "timeout":"{{timeout}}",
  "inlinePreScript":"{{inlinePreScript}}",
  "inlinePostScript":"{{inlinePostScript}}",
  "webJS":"{{webJS}}"
}'
```

> **RESPONSE**

```json
{
  "message": "Success"
}
```

### HTTP Request

**`POST /api/services/update`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
url | STRING | YES | Url of the Hive you make request against
token | STRING | YES |
username | STRING | YES | 
authToken | STRING | YES |
serviceDescription | STRING | NO | `BASE64` encoded
keywords | STRING[] | NO | Array where each keyword is a `STRING`
serviceSchema | STRING | YES | See example below
commandSchema | STRING | NO | See example below
timeout | STRING | YES | Time in seconds when connection will go idle withou incomming data `Default: 30`
inlinePreScript | STRING | NO | `BASE64` encoded JavaScript code that will transform data before it's get to the service 
inlinePostScript | STRING | NO | `BASE64` encoded JavaScript code that will transform data when data will leave a service
webJS | STRING | NO | URL to extarnal stored `CDN` JavaScript code that will visualize the incomming data

## Remove service
This endpoint will remove a service.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/services/remove \ 
-H "Content-Type: application/json" \ 
-d '{
  "url":"{{url}}",
  "token":"{{token}}"
}'
```

> **RESPONSE**

```json
{
  "message": "Success"
}
```

### HTTP Request

**`POST /api/services/remove`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
url | STRING | YES | Url of the Hive you make request against
token | STRING | YES |

## Get micropage data
This endpoint will give micropage data.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/services/micropage \ 
-H "Content-Type: application/json" \ 
-d '{"url":"{{url}}"}'
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
  "imageUrl": "https://cdn.pixabay.com/photo/2015/04/23/22/00/tree-736885__480.jpg"
}
```

### HTTP Request

**`POST /api/services/micropage`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
url | STRING | YES | Url of the Hive you make request against

## Update micropage
This endpoint will update a service micropage.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/services/micropage-update \ 
-H "Content-Type: application/json" \ 
-d '{
  "url":"{{url}}",
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
url | STRING | YES | Url of the Hive you make request against
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
```

## Add links
This endpoint will add links.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/add-links \ 
-H "Content-Type: application/json" \ 
-d '{
  "url":"{{url}}",
  "token":"{{token}}",
  "links":{{links}}
}'
```

> **RESPONSE**

```json
{
  "message": "Success"
}
```

### HTTP Request

**`POST /api/services/add-links`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
url | STRING | YES | Url of the Hive you make request against
token | STRING | YES |
links | STRING[] | YES | Array where each link is a `STRING`, link is written as `domainName/serviceName`

## Remove links
This endpoint will add links.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/remove-links \ 
-H "Content-Type: application/json" \
-d '{
  "url":"{{url}}",
  "token":"{{token}}",
  "links":{{links}}
}'
```

> **RESPONSE**

```json
{
  "message": "Success"
}
```

### HTTP Request

**`POST /api/services/remove-links`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
url | STRING | YES | Url of the Hive you make request against
token | STRING | YES |
links | STRING[] | YES | Array where each link is a `STRING`, link is written as `domainName/serviceName`
