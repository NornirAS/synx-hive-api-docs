# Domains

Domain related endpoints.

## Get subdomains
Ths endpoint will give you the list of all your subdomains.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/domains \ 
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
    "active": true
  }
]
```

### HTTP Request

**`POST /api/domains`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
url | STRING | YES | Url of the Hive you make request against
token | STRING | YES |
username | STRING | YES |

## Create subdomain
Ths endpoint will create a subdomain.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/domains/create \ 
-H "Content-Type: application/json" \ 
-d '{
  "url":"{{url}}",
  "token":"{{token}}",
  "username":"{{username}}",
  "domainName":"{{domainName}}"
}'
```

> **RESPONSE**

```json
{
  "message": "Success"
}
```

### HTTP Request

**`POST /api/domains/create`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
url | STRING | YES | Url of the Hive you make request against
token | STRING | YES |
username | STRING | YES |
domainName | STRING | YES |

## Delete subdomain
Ths endpoint will delete a subdomain.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/domains/delete \ 
-H "Content-Type: application/json" \ 
-d '{
  "url":"{{url}}",
  "token":"{{token}}",
  "username":"{{username}}",
  "domainName":"{{domainName}}"
}'
```

> **RESPONSE**

```json
{
  "message": "Success"
}
```

### HTTP Request

**`POST /api/domains/delete`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
url | STRING | YES | Url of the Hive you make request against
token | STRING | YES |
username | STRING | YES |
domainName | STRING | YES |

## Activate subdomain
Ths endpoint will activate a subdomain.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/domains/activate \ 
-H "Content-Type: application/json" \ 
-d '{
  "url":"{{url}}",
  "token":"{{token}}",
  "username":"{{username}}",
  "domainName":"{{domainName}}",
  "authToken":"{{authToken}}"
}'
```

> **RESPONSE**

```json
{
  "message": "Success"
}
```

<aside class="notice">
This endpoint can be used only by the root domain owner as it require authToken.
</aside>

### HTTP Request

**`POST /api/domains/activate`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
url | STRING | YES | Url of the Hive you make request against
token | STRING | YES |
username | STRING | YES |
domainName | STRING | YES |
authToken | STRING | YES |

## Deactivate subdomain
Ths endpoint will deactivate a subdomain.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/domains/dactivate \ 
-H "Content-Type: application/json" \ 
-d '{
  "url":"{{url}}",
  "token":"{{token}}",
  "username":"{{username}}",
  "domainName":"{{domainName}}",
  "authToken":"{{authToken}}"
}'
```

> **RESPONSE**

```json
{
  "message": "Success"
}
```

<aside class="notice">
This endpoint can be used only by the root domain owner as it require authToken.
</aside>

### HTTP Request

**`POST /api/domains/deactivate`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
url | STRING | YES | Url of the Hive you make request against
token | STRING | YES |
username | STRING | YES |
domainName | STRING | YES |
authToken | STRING | YES |
