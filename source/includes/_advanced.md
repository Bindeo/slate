# Advanced functionality

## Store data into Bitcoin BlockChain

> To store, use this code:

```php
<?php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.bindeo.com/advanced/blockchain",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\"data\":\"HEX STRING\"}",
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

url = "https://api.bindeo.com/advanced/blockchain"

payload = "{\"data\":\"HEX STRING\"}"
headers = {
    'content-type': "application/json",
    'Authorization': "Bearer YOURTOKEN"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request POST \
  --url https://api.bindeo.com/advanced/blockchain \
  --header 'content-type: application/json' \
  --header 'Authorization: Bearer YOURTOKEN' \
  --data '{"data":"HEX STRING"}'
```

> Response JSON body example:

```json
{
    "txid": "2d8573982ef70d5a1e57e16d519896090d21ff7895f4045d734d13b727ef8fa0"
}
```

Store a hexadecimal string into bitcoin blockchain

### HTTP REQUEST

`POST https://api.bindeo.com/advanced/blockchain`

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
**data** | string | Required | Hexadecimal string to save (max: `128`)

### RESPONSE

<aside class="success"><b>Response code</b>: <code>201</code> | <b>Response body</b>: <code>JSON</code></aside>

## Get Transaction Info

> To get the info, use this code:

```php
<?php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.bindeo.com/advanced/blockchain?mode=MODE&txid=TXID",
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

url = "https://api.bindeo.com/advanced/blockchain"

payload = "{\"mode\":\"MODE\",\"txid\":\"TXID\"}"
headers = {
    'content-type': "application/json",
    'Authorization': "Bearer YOURTOKEN"
    }

response = requests.request("GET", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url https://api.bindeo.com/advanced/blockchain \
  --header 'content-type: application/json' \
  --header 'Authorization: Bearer YOURTOKEN' \
  --data '{"mode":"MODE","txid":"TXID"}'
```

> Response JSON body example:

```json
{
    "amount": 0,
    "fee": -0.00013,
    "confirmations": 21,
    "blockhash": "000000000000069a68a75e89a6fffde34310755b1793fef94ec47327d8a8ca9d",
    "blockindex": 20,
    "blocktime": 1459956380,
    "txid": "f858b0bfdd54d6e4c08098c1f16c56036f65fd5e2d91964e5220060e6198f386",
    "walletconflicts": [],
    "time": 1459953940,
    "timereceived": 1459953940,
    "bip125-replaceable": "no",
    "details": [
        {
            "account": "",
            "category": "send",
            "amount": 0,
            "vout": 0,
            "fee": -0.00013
        },
        {
            "account": "",
            "address": "mgv9nNLgmsgN5mhRVVZHrbRNEj3GG5LrsA",
            "category": "send",
            "amount": -0.0079556,
            "label": "",
            "vout": 1,
            "fee": -0.00013
        },
        {
            "account": "",
            "address": "mgv9nNLgmsgN5mhRVVZHrbRNEj3GG5LrsA",
            "category": "receive",
            "amount": 0.0079556,
            "label": "",
            "vout": 1
        }
    ],
    "hex": "01000000012f0eab430ad499b027728a207c9f78738b405139555c6eab69c950a6432a6524000000006a47304402200e0f8cb5dde8e19e08b05eaadf02424742dbe1cb6038059b40cfe1d43a01c869022049328f303b09cae646298f47425792a9a70badf1a5abeed163a39908e76b5f8f012102be28d5136ee58084d4fac0748c8931f428d0d2ee877dda9b4824bfa42bca2784ffffffff020000000000000000126a10d2b483265179cd028eda69ad69d1fe0fa8230c00000000001976a9140f5b4862dea7e7420574ad8fff209efc4ef6b9ec88ac00000000"
}
```

Get basic or extended transaction info. Modes are `basic_info` and `advanced_info`.

### HTTP REQUEST

`GET https://api.bindeo.com/advanced/blockchain`

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
**mode** | string | Required | `basic_info` or `advanced_info`
**txid** | string | Required | Hexadecimal string with the transaction id

### RESPONSE

<aside class="success"><b>Response code</b>: <code>200</code> | <b>Response body</b>: <code>JSON</code></aside>

<aside class="notice">
You must replace <code>MODE</code> with mode you want.
</aside>

## Get Stored Data

> To get the data, use this code:

```php
<?php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.bindeo.com/advanced/blockchain?mode=data&txid=TXID",
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

url = "https://api.bindeo.com/advanced/blockchain"

payload = "{\"mode\":\"data\",\"txid\":\"TXID\"}"
headers = {
    'content-type': "application/json",
    'Authorization': "Bearer YOURTOKEN"
    }

response = requests.request("GET", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url https://api.bindeo.com/advanced/blockchain \
  --header 'content-type: application/json' \
  --header 'Authorization: Bearer YOURTOKEN' \
  --data '{"mode":"data","txid":"TXID"}'
```

> Response JSON body example:

```json
{
    "data": "d2b483265179cd028eda69ad69d1fe0f"
}
```

Get data previously stored in the bitcoin blockchain. You need the associated transaction id.

### HTTP REQUEST

`GET https://api.bindeo.com/advanced/blockchain`

### ARGUMENTS

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
**mode** | string | Required | `data`
**txid** | string | Required | Hexadecimal string with the transaction id

### RESPONSE

<aside class="success"><b>Response code</b>: <code>200</code> | <b>Response body</b>: <code>JSON</code></aside>