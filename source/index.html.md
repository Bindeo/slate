---
title: Bindeo API reference

language_tabs:
  - shell
  - php
  - python

toc_footers:
  - <a href='mailto:info@bindeo.com'>Need help? contact us!</a>

includes:
  - errors

search: true
---

# Introduction

Bindeo provides a RESTful API to easily integrate our services in your systems. Using this documentation you will be able to access al described resources from our application.

We have language bindings in Shell, Php, and Python! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Authentication

Bindeo uses OAuth2 to authorize your requests using temporary tokens. Only previously authorized clients can grant access to our resources. 

If you already have your `client_id` and `client_secret` you could obtain your token. In first place you need to ask for a new token or refresh your old one if it has expired.
To get your fresh token you have to send a **POST** request to `https://api.bindeo.com/access_token` with your client credentials.
Then you will can call our resources including the header `Authorization: Bearer YOURTOKEN` in each request.

<aside class="notice">
You must replace <code>YOURTOKEN</code> with your personal token.
</aside>

## Authenticate with Client Credentials Grant

> To authorize, use this code:

```php
<?php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.bindeo.com/access_token",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\"grant_type\":\"client_credentials\",\"client_id\":\"YOUR CLIENT ID\",\"client_secret\":\"YOUR CLIENT SECRET\"}",
  CURLOPT_HTTPHEADER => array(
    "content-type: application/json"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

```python
import requests

url = "https://api.bindeo.com/access_token"

payload = "{\"grant_type\":\"client_credentials\",\"client_id\":\"YOUR CLIENT ID\",\"client_secret\":\"YOUR CLIENT SECRET\"}"
headers = {
    'content-type': "application/json"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request POST \
  --url https://api.bindeo.com/access_token \
  --header 'content-type: application/json' \
  --data '{"grant_type":"client_credentials","client_id":"YOUR CLIENT ID","client_secret":"YOUR CLIENT SECRET"}'
```

> The above command returns JSON structured like this:

```json
{
    "token_type": "Bearer",
    "expires_in": 3600,
    "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6ImRkYjgwZTE5OTI3ZWNmMzAzMDhhMWU2NzgzZTQwYzQ0MWI5YzM1ZTJiODhiNGUxYmQxMjI2ZjM0MmU0N2U5OGE1YmJkYmY1YjlmOTE5ZmQ0In0.eyJhdWQiOiIyIiwianRpIjoiZGRiODBlMTk5MjdlY2YzMDMwOGExZTY3ODNlNDBjNDQxYjljMzVlMmI4OGI0ZTFiZDEyMjZmMzQyZTQ3ZTk4YTViYmRiZjViOWY5MTlmZDQiLCJpYXQiOjE0NTkyNjczMzEsIm5iZiI6MTQ1OTI2NzMzMSwiZXhwIjoxNDU5MjcwOTMxLCJzdWIiOiIxIiwic2NvcGVzIjpbXX0.xUzC2WOa8vMoxmB0l-xMq1uOeZ6-SY1qmJDDRShawJM_zP-jDKgAQnobYEeXdW5d98pbCpt3LSYzRF8SMgKRjgMHjZuDpT0IHVr3fRVrt_1qnaNxcqQRj2lO_feZ0ygnIsVwM9q1OTcNzB-FcfCDn9Kao565CyyLwftJU4Q6maY"
}
```

This grant is suitable for machine-to-machine authentication. There is not a logged user accessing the system.

### HTTP REQUEST

`POST https://api.bindeo.com/access_token`

### ARGUMENTS

Parameter | Type | Required | Description
-------------- | -------------- | -------------- | --------------
**grant_type** | string | Required | String `client_credentials`
**client_id** | string | Required | Your client id
**client_secret** | string | Required | Your client secret

## Authenticate with Password Grant

> To authorize, use this code:

```php
<?php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.bindeo.com/access_token",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\"grant_type\":\"password\",\"client_id\":\"YOUR CLIENT ID\",\"client_secret\":\"YOUR CLIENT SECRET\",\"username\":\"USERNAME\",\"password\":\"USER PASSWORD\"}",
  CURLOPT_HTTPHEADER => array(
    "content-type: application/json"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

```python
import requests

url = "https://api.bindeo.com/access_token"

payload = "{\"grant_type\":\"password\",\"client_id\":\"YOUR CLIENT ID\",\"client_secret\":\"YOUR CLIENT SECRET\",\"username\":\"USERNAME\",\"password\":\"USER PASSWORD\"}"
headers = {
    'content-type': "application/json"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request POST \
  --url https://api.bindeo.com/access_token \
  --header 'content-type: application/json' \
  --data '{"grant_type":"password","client_id":"YOUR CLIENT ID","client_secret":"YOUR CLIENT SECRET","username":"USERNAME","password":"USER PASSWORD"}'
```

> The above command returns JSON structured like this:

```json
{
    "token_type": "Bearer",
    "expires_in": 3600,
    "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6ImRkYjgwZTE5OTI3ZWNmMzAzMDhhMWU2NzgzZTQwYzQ0MWI5YzM1ZTJiODhiNGUxYmQxMjI2ZjM0MmU0N2U5OGE1YmJkYmY1YjlmOTE5ZmQ0In0.eyJhdWQiOiIyIiwianRpIjoiZGRiODBlMTk5MjdlY2YzMDMwOGExZTY3ODNlNDBjNDQxYjljMzVlMmI4OGI0ZTFiZDEyMjZmMzQyZTQ3ZTk4YTViYmRiZjViOWY5MTlmZDQiLCJpYXQiOjE0NTkyNjczMzEsIm5iZiI6MTQ1OTI2NzMzMSwiZXhwIjoxNDU5MjcwOTMxLCJzdWIiOiIxIiwic2NvcGVzIjpbXX0.xUzC2WOa8vMoxmB0l-xMq1uOeZ6-SY1qmJDDRShawJM_zP-jDKgAQnobYEeXdW5d98pbCpt3LSYzRF8SMgKRjgMHjZuDpT0IHVr3fRVrt_1qnaNxcqQRj2lO_feZ0ygnIsVwM9q1OTcNzB-FcfCDn9Kao565CyyLwftJU4Q6maY",
    "refresh_token": "XR4TTCoT2xGPJ\/6MwBcByb9j3ILlY8wVnmxcm+NA9N6JGSfGHOt4H7EQ3Xxv83u5Qtkf7SzkfSj3E1RoxKtku7VP1NIg5A\/RIU854gUP24uywGkt9\/LDsXq2nI+UA2KOywuPTdWi0EDmd+2UetrY2XOZ4uHEjiCdYI2CTm2sPxmqVOFYMCFy7MdsGRNWbgQFzhcyvwFEkKQ7CiVJL6sRLl0qXxHFdVcQPfTkB6A+Hk0mDdppNMQxz70K+XFf\/GxgyIIk5wE6xHUHHvSSuDDbXmGGdCAYGt3VSz7Ly5WHRUqUsYd9UMjheleZW56Gig0pDDm5IM3OyiXqsbi7F2ymxUtIoJWazYcIPvDm8N2FnMef7JAjKO2w23KSpREzGdSzeslb4RtchDnf4wO1LsiS7P30WCuyZk3YDdggnlmizn1EscrFbe19LpB4bNXUJrb\/TdSPv5ZsHB0NDfBbzTYVPB9GM8DFIuN\/NwqqEBwISjucawKa8X+mCm7UuYRGX8se"
}
```

This grant is suitable for clients who need logged users identification

### HTTP REQUEST

`POST https://api.bindeo.com/access_token`

### ARGUMENTS

Parameter | Type | Required | Description
-------------- | -------------- | -------------- | --------------
**grant_type** | string | Required | String `password`
**client_id** | string | Required | Your client id
**client_secret** | string | Required | Your client secret
**username** | string | Required | Username to login with
**password** | string | Required | User password

## Refresh Token Grant

