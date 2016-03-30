# Authentication

Bindeo uses OAuth2 to authorize your requests using temporary tokens. Only previously authorized clients can grant access to our resources.

If you already have your `client_id` and `client_secret` you could obtain your token. In first place you need to ask for a new token or refresh your old one if it has expired.
To get your fresh token you have to send a **POST** request to `https://api.bindeo.com/access_token` with your client credentials.

Then you will can call our resources including the header `Authorization: Bearer YOURTOKEN` in each request.

<aside class="notice">
You must replace <code>YOURTOKEN</code> with your active token.
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

> Response JSON body example:

```json
{
    "token_type": "Bearer",
    "expires_in": 3600,
    "access_token": "TOKEN"
}
```

This grant is suitable for machine-to-machine authentication. There is not a logged user accessing the system.

### HTTP REQUEST

`POST https://api.bindeo.com/access_token`

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
**grant_type** | string | Required | String `client_credentials`
**client_id** | string | Required | Your client id
**client_secret** | string | Required | Your client secret

### RESPONSE:

<aside class="success"><b>Response code</b>: <code>200</code> | <b>Response body</b>: <code>JSON</code></aside>

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

> Response JSON body example:

```json
{
    "token_type": "Bearer",
    "expires_in": 3600,
    "access_token": "TOKEN",
    "refresh_token": "TOKEN"
}
```

This grant is suitable for clients who need logged users identification. Those clients will need to ask for special privileges.

### HTTP REQUEST

`POST https://api.bindeo.com/access_token`

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
**grant_type** | string | Required | String `password`
**client_id** | string | Required | Your client id
**client_secret** | string | Required | Your client secret
**username** | string | Required | Username to login with
**password** | string | Required | User password

### RESPONSE:

**Response code**: `200`

**Response body**: `JSON`

## Refresh Token Grant

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
  CURLOPT_POSTFIELDS => "{\"grant_type\":\"refresh_token\",\"client_id\":\"YOUR CLIENT ID\",\"client_secret\":\"YOUR CLIENT SECRET\",\"refresh_token\":\"YOUR VALID REFRESH TOKEN\"}",
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

payload = "{\"grant_type\":\"refresh_token\",\"client_id\":\"YOUR CLIENT ID\",\"client_secret\":\"YOUR CLIENT SECRET\",\"refresh_token\":\"YOUR VALID REFRESH TOKEN\"}"
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
  --data '{"grant_type":"refresh_token","client_id":"YOUR CLIENT ID","client_secret":"YOUR CLIENT SECRET","refresh_token":"YOUR VALID REFRESH TOKEN"}'
```

> Response JSON body example:

```json
{
    "token_type": "Bearer",
    "expires_in": 3600,
    "access_token": "TOKEN",
    "refresh_token": "TOKEN"
}
```

Tokens granted with Password Grant can refresh their expired tokens. They need to exchange their `refresh_token` for a new `access_token`.

### HTTP REQUEST

`POST https://api.bindeo.com/access_token`

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
**grant_type** | string | Required | String `refresh_token`
**client_id** | string | Required | Your client id
**client_secret** | string | Required | Your client secret
**refresh_token** | string | Required | Valid refresh token

### RESPONSE:

**Response code**: `200`

**Response body**: `JSON`