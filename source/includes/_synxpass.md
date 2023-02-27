# Synx Pass

Authentication and identification system for heterogeneous networks.

## Create user
Ths endpoint will trigger email verification. You should check your email for verification link.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/synxpass/user/create \ 
-H "Content-Type: application/json" \ 
-d '{
  "username": "{{username}}",
  "authToken": "{{authToken}}",
  "password": "{{password}}",
  "password2": "{{password2}}"
}'
```

> **RESPONSE**

```json
{
  "data": null,
  "error": false,
  "message": "Success",
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

<aside class="notice">
This endpoint can be used only by the root domain owner as it require authToken.
</aside>

### HTTP Request

**`POST /api/synxpass/user/create`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
username | STRING | YES | Email
password | STRING | YES |
password2 | STRING | YES |
authToken | STRING | YES |

## Verify user
This endpoint will verify your email. After that you can continue registraton proccess.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/synxpass/user/verify \ 
-H "Content-Type: application/json" \ 
-d '{
  "username": "{{username}}",
  "authToken": "{{authToken}}",
  "verificationToken": "{{verificationToken}}"
}'
```

> **RESPONSE**

```json
{
  "data": null,
  "error": false,
  "message": "Success",
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

<aside class="notice">
This endpoint can be used only by the root domain owner as it require authToken.
</aside>

### HTTP request

**`POST /api/synxpass/user/verify`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
username | STRING | YES | Email
verificationToken | STRING | YES | You can get this token from the url that you got on your email
authToken | STRING | YES |

## Register user
This endpoint will finally register user in the system.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/synxpass/user/register \ 
-H "Content-Type: application/json" \ 
-d '{
  "rootDomain": "{{rootDomain}}",
  "username": "{{username}}",
  "authToken": "{{authToken}}",
  "password": "{{password}}"
}'
```

> **RESPONSE**

```json
{
  "data": null,
  "error": false,
  "message": "Success",
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

<aside class="notice">
This endpoint can be used only by the root domain owner as it require authToken.
</aside>

### HTTP request

**`POST /api/synxpass/user/register`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
rootDomain | STRING | YES | For example cioty.com
username | STRING | YES | Email
password | STRING | YES |
authToken | STRING | YES |

## Get token
This endpoint will give you a token.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/synxpass/user/token \ 
-H "Content-Type: application/json" \ 
-d '{
  "username": "{{username}}",
  "password": "{{password}}"
}'
```

> **RESPONSE**

```json
{
  "data": "your_token",
  "error": false,
  "message": "Success",
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

### HTTP request

**`POST /api/synxpass/user/token`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
username | STRING | YES | Email
password | STRING | YES |

## Recover password
This endpoint will send you an email with the temporary password which you should use to create new password in the next request.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/synxpass/user/password/recover \ 
-H "Content-Type: application/json" \ 
-d '{
  "username": "{{username}}"
}'
```

> **RESPONSE**

```json
{
  "data": null,
  "error": false,
  "message": "Success",
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

### HTTP request

**`POST /api/synxpass/user/password/recover`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
username | STRING | YES | Email

## New password
This endpoint allow you to create a new password.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/synxpass/user/password/new \ 
-H "Content-Type: application/json" \ 
-d '{
  "username": "{{username}}",
  "password": "{{password}}",
  "tempPassword": "{{tempPassword}}"
}'
```

> **RESPONSE**

```json
{
  "data": null,
  "error": false,
  "message": "Success",
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

### HTTP request

**`POST /api/synxpass/user/password/new`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
username | STRING | YES | Email
password | STRING | YES |
tempPassword | STRING | YES | Temporary password which you should get from url that you got on your email

## Delete user
This endpoint will remove user from the system.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/synxpass/user/delete \ 
-H "Content-Type: application/json" \ 
-d '{
  "rootDomain": "{{rootDomain}}",
  "username": "{{username}}",
  "authToken": "{{authToken}}",
  "token": "{{token}}"
}'
```

> **RESPONSE**

```json
{
  "data": null,
  "error": false,
  "message": "Success",
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

<aside class="notice">
This endpoint can be used only by the root domain owner as it require authToken.
</aside>

### HTTP request

**`POST /api/synxpass/user/delete`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
rootDomain | STRING | YES | For example cioty.com
username | STRING | YES | Email
token | STRING | YES |
authToken | STRING | YES |
