# Errors

> Response JSON body example:

```json
{
    "error": {
        "code": 400,
        "message": "Missing fields"
    }
}
```

The Bindeo API uses the following error codes:

Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request need more data or it is not correct
401 | Unauthorized -- Your token is invalid
403 | Forbidden -- The resource requested needs other access privileges
404 | Not Found -- The requested resource doesn't exist
405 | Method Not Allowed -- You tried to access a resource with an invalid method
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarially offline for maintanance. Please try again later.

**Response body**: `JSON`