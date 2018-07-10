# Post S3 token

## Post S3 tokens purpose

The storage used by Fieldwire, Amazon S3, allow user to directly post files to it, 
without having to go through Fieldwire server.

https://docs.aws.amazon.com/AmazonS3/latest/API/sigv4-UsingHTTPPOST.html

The post S3 token contains all the information you need to use this functionnality
and has a 1 day expiry.
After receiving one, you simply have to create a POST request that contains all the
fields of the post S3 token, and add a "file" field with your file content and 
send it directly to aws (to the post_address contained in the token)

The only action you can do on Fieldwire api with post S3 token is to request one.

It is highly recommended to look at the two demo client applications :

* Ruby: [https://github.com/Fieldwire/fieldwire_ruby_sample](https://github.com/Fieldwire/fieldwire_ruby_sample)
* Java: [https://github.com/Fieldwire/fieldwire_java_sample](https://github.com/Fieldwire/fieldwire_java_sample)

Which both contains an example of post S3 token usage.

## Post S3 token field

Field | Description | Type | Non-null? | Editable? | Default
--------- | --------- | --------- | --------- | --------- | ---------
post_address | The url where to send the request | String | x | |
post_parameters | The input to include in the POST request | JSON | x | |

The post_parameters included are :

- key
- policy
- x-amz-signature
- x-amz-date
- x-amz-credential
- acl
- x-amz-algorithm

All of them are string-type and must be sent as they were received to AWS post service.
The post_address is the url of the AWS post service itself.

## Create Post S3 Token

```http
POST /aws_post_tokens HTTP/1.1
Authorization: Token api=[api token]>
Content-type: application/json
```

> The above command returns:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "post_address": "http://example.s3.amazonaws.com",
    "post_parameters": 
    {
        "key": "example/bbef5b6b9e00e19eaa94d81323280238_${filename}", 
        "policy": "eyJleHBpcmF0aW9uIjoiMjAxOC0wNy0wNlQxMTowMjozNVoiLCJjb25kaXRpb25zIjpbeyJidWNrZXQiOiJuaWNvbGFzLWZ3LWRldmVsb3BtZW50In0sWyJzdGFydHMtd2l0aCIsIiRrZXkiLCI2Yjg2YjI3M2ZmMzRmY2UxOWQ2YjgwNGVmZjVhM2Y1Ny9iYmVmNWI2YjllMDBlMTllYWE5NGQ4MTMyMzI4MDIzOCJdLFsiY29udGVudC1sZW5ndGgtcmFuZ2UiLDAsMTA0ODU3NjAwMF0seyJ4LWFtei1kYXRlIjotY3JlZGVudGlhbCI6IkFLSUFJWEhURVpPWVRRUlUzToiMjAxODA3MDVUMTEwMjM1WiJ9LHsieC1hbXEJBLzIwMTgwNzA1L3VzLWVhc3QtMS9zMy9hd3M0X3JlcXVlc3QifSx7ImFjbCI6InB1YmxpYy1yZWFkIn0seyJ4LWFtei1hbGdvcml0aG0iOiJBV1M0LUhNQUMtU0hBMjU2In1dfQ==",
        "x-amz-signature": "63d932252334c0c888561bb2c86412d1f2faf3c15842dd8af6ff022ec95201c2", 
        "x-amz-date": "20180705T110235Z", 
        "x-amz-credential": "EXAMPLE/20180705/us-east-1/s3/aws4_request", 
        "acl": "public-read", 
        "x-amz-algorithm": "AWS4-HMAC-SHA256"
    }
}
```

### HTTP Request

`POST /aws_post_tokens`

## Post file to AWS S3 using token

```http
POST http://example.s3.amazonaws.com HTTP/1.1
Content-type: multipart/form-data

{
    "key": "example/bbef5b6b9e00e19eaa94d81323280238_${filename}", 
    "policy": "eyJleHBpcmF0aW9uIjoiMjAxOC0wNy0wNlQxMTowMjozNVoiLCJjb25kaXRpb25zIjpbeyJidWNrZXQiOiJuaWNvbGFzLWZ3LWRldmVsb3BtZW50In0sWyJzdGFydHMtd2l0aCIsIiRrZXkiLCI2Yjg2YjI3M2ZmMzRmY2UxOWQ2YjgwNGVmZjVhM2Y1Ny9iYmVmNWI2YjllMDBlMTllYWE5NGQ4MTMyMzI4MDIzOCJdLFsiY29udGVudC1sZW5ndGgtcmFuZ2UiLDAsMTA0ODU3NjAwMF0seyJ4LWFtei1kYXRlIjotY3JlZGVudGlhbCI6IkFLSUFJWEhURVpPWVRRUlUzToiMjAxODA3MDVUMTEwMjM1WiJ9LHsieC1hbXEJBLzIwMTgwNzA1L3VzLWVhc3QtMS9zMy9hd3M0X3JlcXVlc3QifSx7ImFjbCI6InB1YmxpYy1yZWFkIn0seyJ4LWFtei1hbGdvcml0aG0iOiJBV1M0LUhNQUMtU0hBMjU2In1dfQ==",
    "x-amz-signature": "63d932252334c0c888561bb2c86412d1f2faf3c15842dd8af6ff022ec95201c2", 
    "x-amz-date": "20180705T110235Z", 
    "x-amz-credential": "EXAMPLE/20180705/us-east-1/s3/aws4_request", 
    "acl": "public-read", 
    "x-amz-algorithm": "AWS4-HMAC-SHA256",
    "file": "example file content"
}
```

> The above command returns:

```http
HTTP/1.1 200 OK
```

### HTTP Request

`POST http://example.s3.amazonaws.com`

<aside class="warning">
    This request is not part of the Fieldwire API as it is a request to AWS S3.
    It is given as an example of usage of the post S3 token. 
</aside>

You might receive the following error codes :

- 400 : bad request, your token has expired or your file is oversized (> 1 GB)
- 403 : forbidden, you modified one of the attributes transmitted by the post token
