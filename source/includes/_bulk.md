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
                "bulkInfo": "{\"title\":\"document\",\"fields\":[\"hash\",\"size\"]}"
            }
        }
    ],
    "total_pages": 1
}
```

Get the list of Bulk Type your client credentials are able to use.

### HTTP REQUEST

`GET https://api.bindeo.com/bulk/types`

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------


### RESPONSE

<aside class="success"><b>Response code</b>: <code>200</code> | <b>Response body</b>: <code>JSON</code></aside>

## Open a new collection

> To open, use this code:

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

### HTTP REQUEST

`POST https://api.bindeo.com/bulk`

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
**mode** | string | Required | `open`
**type** | string | Required | Bulk type representing document collection type to be opened
**external_id** | string | Required | Client defined identifier for this collection (max: `64`)
**additional params** | mixed | Required | Additional parameters defined for selected document collection (e.g. `hash`, `size`...)

### RESPONSE

<aside class="success"><b>Response code</b>: <code>201</code> | <b>Response body</b>: <code>JSON</code></aside>