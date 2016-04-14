# Document Collections

## List of Bulk Types

> To get the list, use this code:

```php
<?php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.bindeo.com/bulk/types",
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

url = "https://api.bindeo.com/bulk/types"

headers = {
    'content-type': "application/json",
    'Authorization': "Bearer YOURTOKEN"
    }

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url https://api.bindeo.com/bulk/types \
  --header 'content-type: application/json' \
  --header 'Authorization: Bearer YOURTOKEN'
```

> Response JSON body example:

```json
{
    "data": [
        {
            "type": "bulk_type",
            "attributes": {
                "type": "Audit Book",
                "elementsType": "Events",
                "bulkInfo": "{\"title\":\"document\",\"fields\":[\"hash\",\"size\"]}"
            }
        }
    ],
    "total_pages": 1
}
```

Get the list of Bulk Type your client credentials allow you to use.

### HTTP REQUEST

`GET https://api.bindeo.com/bulk/types`

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------


### RESPONSE

<aside class="success"><b>Response code</b>: <code>200</code> | <b>Response body</b>: <code>JSON</code></aside>

## Open a New Collection

> To open (example of Event Type collection), use this code:

```php
<?php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.bindeo.com/bulk",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\"mode\":\"open\",\"type\":\"Audit Book\",\"external_id\":\"IDENTIFIER\",\"hash\":\"DOCUMENT HASH\",\"size\":\"DOCUMENT SIZE\"}",
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

url = "https://api.bindeo.com/bulk"

payload = "{\"mode\":\"open\",\"type\":\"Audit Book\",\"external_id\":\"IDENTIFIER\",\"hash\":\"DOCUMENT HASH\",\"size\":\"DOCUMENT SIZE\"}"
headers = {
    'content-type': "application/json",
    'Authorization': "Bearer YOURTOKEN"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request POST \
  --url https://api.bindeo.com/bulk \
  --header 'content-type: application/json' \
  --header 'Authorization: Bearer YOURTOKEN' \
  --data '{"mode":"open","type":"Audit Book","external_id":"IDENTIFIER","hash":"DOCUMENT HASH","size":"DOCUMENT SIZE"}'
```

> Response JSON body example:

```json
{
    "externalId": "Test Id 35",
    "type": "Audit Book"
}
```

Open a document collection to store later in Blockchain. Collections are based on Bulk Type structures defined for each client.

Each collection may have additional parameters depending on collection Bulk Type.

### HTTP REQUEST

`POST https://api.bindeo.com/bulk`

### ARGUMENTS

<b>Event type</b>

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
**mode** | string | Required | `open`
**type** | string | Required | Bulk type representing document collection type to be opened
**external_id** | string | Required | Client defined identifier for this collection (max: `64`)
**hash** | string | Required | Hash code of the document that collection represents
**size** | int | Required | Size in bytes of the document that collection represents

### RESPONSE

<aside class="success"><b>Response code</b>: <code>201</code> | <b>Response body</b>: <code>JSON</code></aside>

## Get Collection Status

> To get the status, use this code:

```php
<?php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.bindeo.com/bulk/IDENTIFIER?mode=status",
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

url = "https://api.bindeo.com/bulk/IDENTIFIER?mode=status"

headers = {
    'content-type': "application/json",
    'Authorization': "Bearer YOURTOKEN"
    }

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url https://api.bindeo.com/bulk/IDENTIFIER?mode=status \
  --header 'content-type: application/json' \
  --header 'Authorization: Bearer YOURTOKEN'
```

> Response JSON body example:

```json
{
    "data": {
        "type": "bulk_transaction",
        "attributes": {
            "externalId": "Test identifier",
            "type": "Audit Book",
            "closed": "0",
            "numItems": "2"
        }
    }
}
```

Get the status of your collection. If collection is closed you will get extra information about the Blockchain transaction id and its confirmation status.

You need to replace `IDENTIFIER` with your collection identifier and specify `status` mode.

### HTTP REQUEST

`GET https://api.bindeo.com/bulk/IDENTIFIER`

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
**mode** | string | Required | `status`

### RESPONSE

<aside class="success"><b>Response code</b>: <code>200</code> | <b>Response body</b>: <code>JSON</code></aside>
<aside class="notice">Replace <code>IDENTIFIER</code> with your collection identifier</aside>

## Get Collection Hash

> To get the hash, use this code:

```php
<?php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.bindeo.com/bulk/IDENTIFIER?mode=hash",
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

url = "https://api.bindeo.com/bulk/IDENTIFIER?mode=hash"

headers = {
    'content-type': "application/json",
    'Authorization': "Bearer YOURTOKEN"
    }

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url https://api.bindeo.com/bulk/IDENTIFIER?mode=hash \
  --header 'content-type: application/json' \
  --header 'Authorization: Bearer YOURTOKEN'
```

> Response JSON body example:

```json
{
    "data": {
        "type": "bulk_transaction",
        "attributes": {
            "externalId": "Test identifier",
            "type": "Audit Book",
            "hash": "5b313307366261817ab6fa02c1f798e2c3f37bba0b5516941d8fb07010de95cb"
        }
    }
}
```

Get current hash code of collection.

You need to replace `IDENTIFIER` with your collection identifier and specify `hash` mode.

### HTTP REQUEST

`GET https://api.bindeo.com/bulk/IDENTIFIER`

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
**mode** | string | Required | `hash`

### RESPONSE

<aside class="success"><b>Response code</b>: <code>200</code> | <b>Response body</b>: <code>JSON</code></aside>
<aside class="notice">Replace <code>IDENTIFIER</code> with your collection identifier</aside>

## Get Collection Structure

> To get the structure, use this code:

```php
<?php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.bindeo.com/bulk/IDENTIFIER?mode=structure",
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

url = "https://api.bindeo.com/bulk/IDENTIFIER?mode=structure"

headers = {
    'content-type': "application/json",
    'Authorization': "Bearer YOURTOKEN"
    }

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url https://api.bindeo.com/bulk/IDENTIFIER?mode=structure \
  --header 'content-type: application/json' \
  --header 'Authorization: Bearer YOURTOKEN'
```

> Response JSON body example:

```json
{
    "data": {
        "type": "bulk_transaction",
        "attributes": {
            "externalId": "Test identifier",
            "type": "Audit Book",
            "structure": "JSON WITH STRUCTURE"
        }
    }
}
```

Get current collection structure in JSON format. Collection structure is generated according Bulk Type selected in opening process.

You need to replace `IDENTIFIER` with your collection identifier and specify `structure` mode.

### HTTP REQUEST

`GET https://api.bindeo.com/bulk/IDENTIFIER`

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
**mode** | string | Required | `structure`

### RESPONSE

<aside class="success"><b>Response code</b>: <code>200</code> | <b>Response body</b>: <code>JSON</code></aside>
<aside class="notice">Replace <code>IDENTIFIER</code> with your collection identifier</aside>

## Add Item to Collection

> To add item, use this code (example of `Event Type` collection):

```php
<?php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.bindeo.com/bulk/IDENTIFIER",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\"type\":\"event\",\"name\":\"EVENT NAME\",\"timestamp\":\"EVENT TIMESTAMP\",\"data\":\"JSON STRING\"}",
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

url = "https://api.bindeo.com/bulk/IDENTIFIER"

payload = "{\"type\":\"event\",\"name\":\"EVENT NAME\",\"timestamp\":\"EVENT TIMESTAMP\",\"data\":\"JSON STRING\"}"
headers = {
    'content-type': "application/json",
    'Authorization': "Bearer YOURTOKEN"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request POST \
  --url https://api.bindeo.com/bulk/IDENTIFIER \
  --header 'content-type: application/json' \
  --header 'Authorization: Bearer YOURTOKEN' \
  --data '{"type":"event","name":"EVENT NAME","timestamp":"EVENT TIMESTAMP","data":"JSON STRING"}'
```

> Response JSON body example:

```json
{
    "data": {
        "type": "bulk_transaction",
        "attributes": {
            "externalId": "Test id",
            "type": "Audit Book",
            "numItems": 2,
            "structure": "{\"document\":{\"hash\":\"7316008510843f2ce94f03fca8f4688c6c67a9d3b32cb5f7a33946ad8cd99547\",\"size\":\"185000\"},\"events\":[{\"name\":\"event-1\",\"timestamp\":\"2016-01-01 10:00:35\",\"data\":\"{\\\"info\\\":\\\"ok\\\"}\"},{\"name\":\"event-2\",\"timestamp\":\"2016-01-01 10:10:35\",\"data\":\"{\\\"info\\\":\\\"ok\\\"}\"}]}",
            "hash": "91a282ec1c9d407214d0b25160b77de55ea2829b746773de7a7e7fe90cc2661a"
        }
    }
}
```

Add an item to an opened collection.

Item could be `event` or `file`. The item type you need depends on the Bulk Type of collection.

### HTTP REQUEST

`POST https://api.bindeo.com/bulk/IDENTIFIER`

### ARGUMENTS

<b>Event type</b>

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
**type** | string | Required | Type of item. It could be `event`
**name** | string | Required | Event name (max: `128`)
**timestamp** | string | Required | Event timestamp in ISO_8601 (YYYY-MM-DD hh:mm:ss)
**data** | string | Required | JSON string with event data. For the client use (max: `4000`)

### RESPONSE

<aside class="success"><b>Response code</b>: <code>201</code> | <b>Response body</b>: <code>JSON</code></aside>
<aside class="notice">Replace <code>IDENTIFIER</code> with your collection identifier</aside>

## Delete Collection

> To delete it, use this code:

```php
<?php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.bindeo.com/bulk/IDENTIFIER",
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

url = "https://api.bindeo.com/bulk/IDENTIFIER"

headers = {
    'content-type': "application/json",
    'Authorization': "Bearer YOURTOKEN"
    }

response = requests.request("DELETE", url, headers=headers)

print(response.text)
```

```shell
curl --request DELETE \
  --url https://api.bindeo.com/bulk/IDENTIFIER \
  --header 'content-type: application/json' \
  --header 'Authorization: Bearer YOURTOKEN'
```

Delete an opened collection.

### HTTP REQUEST

`DELETE https://api.bindeo.com/bulk/IDENTIFIER`

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------

### RESPONSE

<aside class="success"><b>Response code</b>: <code>204</code> | <b>Response body</b>: <code>empty</code></aside>
<aside class="notice">Replace <code>IDENTIFIER</code> with your collection identifier</aside>

## Close and Notarize Collection

> To close it, use this code:

```php
<?php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.bindeo.com/bulk/IDENTIFIER",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "PUT",
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

url = "https://api.bindeo.com/bulk/IDENTIFIER"

headers = {
    'content-type': "application/json",
    'Authorization': "Bearer YOURTOKEN"
    }

response = requests.request("PUT", url, headers=headers)

print(response.text)
```

```shell
curl --request PUT \
  --url https://api.bindeo.com/bulk/IDENTIFIER \
  --header 'content-type: application/json' \
  --header 'Authorization: Bearer YOURTOKEN'
```

> Response JSON body example:

```json
{
    "data": {
        "type": "bulk_transaction",
        "attributes": {
            "externalId": "Test id",
            "type": "Audit Book",
            "closed": 1,
            "numItems": "2",
            "structure": "{\"document\":{\"hash\":\"7316008510843f2ce94f03fca8f4688c6c67a9d3b32cb5f7a33946ad8cd99547\",\"size\":\"185000\"},\"events\":[{\"name\":\"event-1\",\"timestamp\":\"2016-01-01 10:00:35\",\"data\":\"{\\\"info\\\":\\\"ok\\\"}\"},{\"name\":\"event-2\",\"timestamp\":\"2016-01-01 10:25:35\",\"data\":\"{\\\"info\\\":\\\"ok\\\"}\"}]}",
            "hash": "096c732e8e83b2b5ad7de63b0099c011fbb3ef721e7814b9101bd5bc6701f6d1",
            "transaction": "629f5ad1c4523f92d03d30bc608ab9c87aab5bf2299e3b787e62c3d704332fb5",
            "confirmed": "0"
        }
    }
}
```

Close an opened collection and notarize it in Blockchain. After this step you won't be able to add more items or delete the collection.

When the Blockchain transaction is confirmed and permanently sealed, you will be notified as agreed. You can check it also asking for Collection Status.

### HTTP REQUEST

`PUT https://api.bindeo.com/bulk/IDENTIFIER`

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------

### RESPONSE

<aside class="success"><b>Response code</b>: <code>200</code> | <b>Response body</b>: <code>JSON</code></aside>
<aside class="notice">Replace <code>IDENTIFIER</code> with your collection identifier</aside>