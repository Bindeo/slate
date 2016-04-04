# General data

## List of Account Types

> To get the list, use this code:

```php
<?php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.bindeo.com/general/account-types?locale=en_US",
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

url = "https://api.bindeo.com/general/account-types"

payload = "{\"locale\":\"en_US\"}"
headers = {
    'content-type': "application/json",
    'Authorization': "Bearer YOURTOKEN"
    }

response = requests.request("GET", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url https://api.bindeo.com/general/account-types \
  --header 'content-type: application/json' \
  --header 'Authorization: Bearer YOURTOKEN' \
  --data '{"locale":"en_US"}'
```

> Response JSON body example:

```json
{
    "data": [
        {
            "type": "account_type",
            "attributes": {
                "idType": "1",
                "name": "Admin"
            }
        },
        {
            "type": "account_type",
            "attributes": {
                "idType": "2",
                "name": "Usuario gratis",
                "maxFilesize": "3072",
                "maxStorage": "524288",
                "maxStampsMonth": "10"
            }
        },
        {
            "type": "account_type",
            "attributes": {
                "idType": "3",
                "name": "Usuario premium",
                "cost": "10",
                "maxFilesize": "10240",
                "maxStorage": "52428800",
                "maxStampsMonth": "1000"
            }
        }
    ],
    "total_pages": 1
}
```

Get a list of translated Account Types

### HTTP REQUEST

`GET https://api.bindeo.com/general/account-types`

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
**locale** | string | Required | Valid locale code

### RESPONSE

<aside class="success"><b>Response code</b>: <code>200</code> | <b>Response body</b>: <code>JSON</code></aside>

## List of File Types

> To get the list, use this code:

```php
<?php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.bindeo.com/general/file-types?locale=en_US",
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

url = "https://api.bindeo.com/general/file-types"

payload = "{\"locale\":\"en_US\"}"
headers = {
    'content-type': "application/json",
    'Authorization': "Bearer YOURTOKEN"
    }

response = requests.request("GET", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url https://api.bindeo.com/general/file-types \
  --header 'content-type: application/json' \
  --header 'Authorization: Bearer YOURTOKEN' \
  --data '{"locale":"en_US"}'
```

> Response JSON body example:

```json
{
    "data": [
        {
            "type": "file_type",
            "attributes": {
                "idType": "1",
                "name": "Document"
            }
        },
        {
            "type": "file_type",
            "attributes": {
                "idType": "2",
                "name": "Bilateral contract"
            }
        },
        {
            "type": "file_type",
            "attributes": {
                "idType": "3",
                "name": "Smart property"
            }
        },
        {
            "type": "file_type",
            "attributes": {
                "idType": "4",
                "name": "Others"
            }
        }
    ],
    "total_pages": 1
}
```

Get a list of translated File Types

### HTTP REQUEST

`GET https://api.bindeo.com/general/file-types`

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
**locale** | string | Required | Valid locale code

### RESPONSE

<aside class="success"><b>Response code</b>: <code>200</code> | <b>Response body</b>: <code>JSON</code></aside>

## List of Media Types

> To get the list, use this code:

```php
<?php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.bindeo.com/general/media-types?locale=en_US",
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

url = "https://api.bindeo.com/general/media-types"

payload = "{\"locale\":\"en_US\"}"
headers = {
    'content-type': "application/json",
    'Authorization': "Bearer YOURTOKEN"
    }

response = requests.request("GET", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url https://api.bindeo.com/general/media-types \
  --header 'content-type: application/json' \
  --header 'Authorization: Bearer YOURTOKEN' \
  --data '{"locale":"en_US"}'
```

> Response JSON body example:

```json
{
    "data": [
        {
            "type": "media_type",
            "attributes": {
                "idType": "1",
                "name": "PDF"
            }
        },
        {
            "type": "media_type",
            "attributes": {
                "idType": "2",
                "name": "Text documents"
            }
        },
        {
            "type": "media_type",
            "attributes": {
                "idType": "3",
                "name": "Spreadsheets"
            }
        },
        {
            "type": "media_type",
            "attributes": {
                "idType": "4",
                "name": "Photos & Images"
            }
        },
        {
            "type": "media_type",
            "attributes": {
                "idType": "5",
                "name": "Presentations"
            }
        }
    ],
    "total_pages": 1
}
```

Get a list of translated Media Types

### HTTP REQUEST

`GET https://api.bindeo.com/general/media-types`

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
**locale** | string | Required | Valid locale code

### RESPONSE

<aside class="success"><b>Response code</b>: <code>200</code> | <b>Response body</b>: <code>JSON</code></aside>