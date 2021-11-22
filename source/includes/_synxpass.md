# Synx Pass

Authentication and identification system for heterogeneous networks.

## Register user
Ths endpoint will trigger email verification. You should check your email for verification link.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/synxpass/create-user \ 
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
  "message": "Success"
}
```

> Server got your request, but something went wrong

```json
{
  "error": "Error"
}
```

<aside class="notice">
This endpoint can be used only by the root domain owner as it require authToken.
</aside>

### HTTP Request

**`POST /api/synxpass/create-user`**

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
curl -X POST https://synxhive.com/api/synxpass/verify-user \ 
-H "Content-Type: application/json" \ 
-d '{
  "username": "{{username}}",
  "authToken": "{{authToken}}",
  "verification": "{{verificationToken}}"
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

<aside class="notice">
This endpoint can be used only by the root domain owner as it require authToken.
</aside>

### HTTP request

**`POST /api/synxpass/verify-user`**

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
curl -X POST https://synxhive.com/api/synxpass/register-user \ 
-H "Content-Type: application/json" \ 
-d '{
  "username": "{{username}}",
  "authToken": "{{authToken}}",
  "password": "{{password}}"
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

<aside class="notice">
This endpoint can be used only by the root domain owner as it require authToken.
</aside>

### HTTP request

**`POST /api/synxpass/register-user`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
username | STRING | YES | Email
password | STRING | YES |
authToken | STRING | YES |

## Get token
This endpoint will give you a token.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/synxpass/get-token \ 
-H "Content-Type: application/json" \ 
-d '{
  "username": "{{username}}",
  "password": "{{password}}"
}'
```

> **RESPONSE**

```json
{
  "token": "aToken_yourToken"
}
```

> Server got your request, but something went wrong

```json
{
  "error": "Error"
}
```

### HTTP request

**`POST /api/synxpass/get-token`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
username | STRING | YES | Email
password | STRING | YES |

## Forgot password
This endpoint will send you an email with the temporary password which you should use to create new password in the next request.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/synxpass/forgot-password \ 
-H "Content-Type: application/json" \ 
-d '{
  "username": "{{username}}"
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

### HTTP request

**`POST /api/synxpass/forgot-password`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
username | STRING | YES | Email

## New password
This endpoint allow you to create a new password.

> **REQUEST**

```shell
curl -X POST https://synxhive.com/api/synxpass/new-password \ 
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
  "message": "Success"
}
```

> Server got your request, but something went wrong

```json
{
  "error": "Error"
}
```

### HTTP request

**`POST /api/synxpass/new-password`**

### Query Parameters

Parameter | Type | Mandatory | Description
--------- | ---- | --------- | -----------
username | STRING | YES | Email
password | STRING | YES |
tempPassword | STRING | YES | Temporary password which you should get from url that you got on your email
