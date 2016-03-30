# Accounts

## Create new account

> To create it, use this code:

```php
<?php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.bindeo.com/account",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\"email\":\"ACCOUNT EMAIL\",\"password\":\"ACCOUNT PASSWORD\",\"name\":\"ACCOUNT NAME\",\"locale\":\"ACCOUNT LOCALE\",\"latitude\":\"ACCOUNT LATITUDE\",\"longitude\":\"ACCOUNT LONGITUDE\"}",
  CURLOPT_HTTPHEADER => array(
    "content-type: application/json",
    "Authorization: Bearer YOURTOKEN"
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

url = "https://api.bindeo.com/account"

payload = "{\"email\":\"ACCOUNT EMAIL\",\"password\":\"ACCOUNT PASSWORD\",\"name\":\"ACCOUNT NAME\",\"locale\":\"ACCOUNT LOCALE\",\"latitude\":\"ACCOUNT LATITUDE\",\"longitude\":\"ACCOUNT LONGITUDE\"}"
headers = {
    'content-type': "application/json",
    'Authorization': "Bearer YOURTOKEN"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request POST \
  --url https://api.bindeo.com/account \
  --header 'content-type: application/json' \
  --header 'Authorization: Bearer YOURTOKEN' \
  --data '{"email":"ACCOUNT EMAIL","password":"ACCOUNT PASSWORD","name":"ACCOUNT NAME","locale":"ACCOUNT LOCALE","latitude":"ACCOUNT LATITUDE","longitude":"ACCOUNT LONGITUDE"}'
```

> Response JSON body example:

```json
{
    "data": {
        "type": "users",
        "attributes": {
            "idUser": 1,
            "email": "email@email.com",
            "type": 2,
            "name": "Test account",
            "lang": "en_US",
            "latitude": "37.356695",
            "longitude": "-121.996100"
        }
    }
}
```

Create a new user account

### HTTP REQUEST

`POST https://api.bindeo.com/account`

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
**email** | string | Required | Valid email
**password** | string | Required | Account password (min: `6`, max: `4096`)
**name** | string | Required | Account name (min: `2`, max: `256`)
**locale** | string | Required | Valid locale code
**latitude** | float | Optional | Valid latitude format (e.g. 37.356695)
**longitude** | float | Optional | Valid longitude format (e.g. -121.996100)

### RESPONSE

<aside class="success"><b>Response code</b>: <code>201</code> | <b>Response body</b>: <code>JSON</code></aside>

## Modify locale

> To modify it, use this code:

```php
<?php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.bindeo.com/account",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "PUT",
  CURLOPT_POSTFIELDS => "{\"locale\":\"ACCOUNT LOCALE\"}",
  CURLOPT_HTTPHEADER => array(
    "content-type: application/json",
    "Authorization: Bearer YOURTOKEN"
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

url = "https://api.bindeo.com/account"

payload = "{\"locale\":\"ACCOUNT LOCALE\"}"
headers = {
    'content-type': "application/json",
    'Authorization': "Bearer YOURTOKEN"
    }

response = requests.request("PUT", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request PUT \
  --url https://api.bindeo.com/account \
  --header 'content-type: application/json' \
  --header 'Authorization: Bearer YOURTOKEN' \
  --data '{"locale":"ACCOUNT LOCALE"}'
```

> Response JSON body example:

```json
{
    "data": {
        "type": "users",
        "attributes": {
            "idUser": 1,
            "email": "email@email.com",
            "type": 2,
            "name": "Test account",
            "confirmed": "1",
            "lang": "en_US",
            "storageLeft": "509337",
            "stampsLeft": "10"
        }
    }
}
```

Modify an account locale

### HTTP REQUEST

`PUT https://api.bindeo.com/account`

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
**locale** | string | Required | Valid locale code

### RESPONSE

<aside class="success"><b>Response code</b>: <code>200</code> | <b>Response body</b>: <code>JSON</code></aside>

## Cancel the account

> To cancel it, use this code:

```php
<?php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.bindeo.com/account",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "DELETE",
  CURLOPT_HTTPHEADER => array(
    "content-type: application/json",
    "Authorization: Bearer YOURTOKEN"
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

url = "https://api.bindeo.com/account"

headers = {
    'content-type': "application/json",
    'Authorization': "Bearer YOURTOKEN"
    }

response = requests.request("DELETE", url, headers=headers)

print(response.text)
```

```shell
curl --request DELETE \
  --url https://api.bindeo.com/account \
  --header 'content-type: application/json' \
  --header 'Authorization: Bearer YOURTOKEN'
```

Delete an account

### HTTP REQUEST

`DELETE https://api.bindeo.com/account`

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------

### RESPONSE

<aside class="success"><b>Response code</b>: <code>204</code> | <b>Response body</b>: <code>empty</code></aside>

## Reset password

> To reset it, use this code:

```php
<?php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.bindeo.com/account/password?email=USEREMAIL",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "content-type: application/json",
    "Authorization: Bearer YOURTOKEN"
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

url = "https://api.bindeo.com/account/password"

payload = "{\"email\":\"USER EMAIL\"}"
headers = {
    'content-type': "application/json",
    'Authorization': "Bearer YOURTOKEN"
    }

response = requests.request("GET", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url https://api.bindeo.com/account/password \
  --header 'content-type: application/json' \
  --header 'Authorization: Bearer YOURTOKEN' \
  --data '{"email":"USER EMAIL"}'
```

Delete an account

### HTTP REQUEST

`GET https://api.bindeo.com/account/password`

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
**email** | string | Required | Valid email

### RESPONSE

<aside class="success"><b>Response code</b>: <code>204</code> | <b>Response body</b>: <code>empty</code></aside>

## Modify password

> To modify it, use this code:

```php
<?php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.bindeo.com/account/password",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "PUT",
  CURLOPT_POSTFIELDS => "{\"locale\":\"ACCOUNT LOCALE\",\"old_password\":\"OLD PASSWORD\"}",
  CURLOPT_HTTPHEADER => array(
    "content-type: application/json",
    "Authorization: Bearer YOURTOKEN"
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

url = "https://api.bindeo.com/account/password"

payload = "{\"locale\":\"ACCOUNT LOCALE\",\"old_password\":\"OLD PASSWORD\"}"
headers = {
    'content-type': "application/json",
    'Authorization': "Bearer YOURTOKEN"
    }

response = requests.request("PUT", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request PUT \
  --url https://api.bindeo.com/account/password \
  --header 'content-type: application/json' \
  --header 'Authorization: Bearer YOURTOKEN' \
  --data '{"password":"NEW PASSWORD","old_password":"OLD PASSWORD"}'
```

> Response JSON body example:

```json
{
    "data": {
        "type": "users",
        "attributes": {
            "idUser": 1,
            "email": "email@email.com",
            "type": 2,
            "name": "Test account",
            "confirmed": "1",
            "lang": "en_US",
            "storageLeft": "509337",
            "stampsLeft": "10"
        }
    }
}
```

Modify the account password

### HTTP REQUEST

`PUT https://api.bindeo.com/account/password`

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
**password** | string | Required | New password (min: `6`, max: `4096`)
**old_password** | string | Required | Old password (min: `6`, max: `4096`)

### RESPONSE

<aside class="success"><b>Response code</b>: <code>200</code> | <b>Response body</b>: <code>JSON</code></aside>

## Modify type

> To modify it, use this code:

```php
<?php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.bindeo.com/account/type",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "PUT",
  CURLOPT_POSTFIELDS => "{\"type\":\"ACCOUNT TYPE ID\"}",
  CURLOPT_HTTPHEADER => array(
    "content-type: application/json",
    "Authorization: Bearer YOURTOKEN"
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

url = "https://api.bindeo.com/account/type"

payload = "{\"type\":\"ACCOUNT TYPE ID\"}"
headers = {
    'content-type': "application/json",
    'Authorization': "Bearer YOURTOKEN"
    }

response = requests.request("PUT", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request PUT \
  --url https://api.bindeo.com/account/type \
  --header 'content-type: application/json' \
  --header 'Authorization: Bearer YOURTOKEN' \
  --data '{"password":"ACCOUNT TYPE ID"}'
```

> Response JSON body example:

```json
{
    "data": {
        "type": "users",
        "attributes": {
            "idUser": 1,
            "email": "email@email.com",
            "type": 2,
            "name": "Test account",
            "confirmed": "1",
            "lang": "en_US",
            "storageLeft": "509337",
            "stampsLeft": "10"
        }
    }
}
```

Modify the account type

### HTTP REQUEST

`PUT https://api.bindeo.com/account/type`

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
**type** | int | Required | New account type ID (view Account Types List)

### RESPONSE

<aside class="success"><b>Response code</b>: <code>200</code> | <b>Response body</b>: <code>JSON</code></aside>

## Resend validation token

> To resend it, use this code:

```php
<?php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.bindeo.com/account/token",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "content-type: application/json",
    "Authorization: Bearer YOURTOKEN"
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

url = "https://api.bindeo.com/account/token"

headers = {
    'content-type': "application/json",
    'Authorization': "Bearer YOURTOKEN"
    }

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url https://api.bindeo.com/account/token \
  --header 'content-type: application/json' \
  --header 'Authorization: Bearer YOURTOKEN'
```

Resend the account activation token by email

### HTTP REQUEST

`GET https://api.bindeo.com/account/token`

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------

### RESPONSE

<aside class="success"><b>Response code</b>: <code>204</code> | <b>Response body</b>: <code>empty</code></aside>