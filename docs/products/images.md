# Products Images

Images on Ordercloud are served with cloud front CDN to make sure they are loaded as fast as possible for the user.

##Types supported

Currently supported image are :
* JPG
* PNG

## Size


### Max File size

The maximum file size for an image accepted by the api is 5 MB (5120 B).

###Dimensions

<aside class="info">
    Images are automatically resized if larger while maintaining the width to height ratio.
</aside>

Images are resized to:
* Normal : 640px
* Thumbnail : 120px

<aside class="info">
Thumbnails are automatically generated and can be accessed by using the image url and appending "_thumb". (jpg or png)
</aside>


## Uploading Product Images

> To test, use this code:

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https//staging-api.ordercloud.com/resource/resource/product/%7BproductId%7D/image",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "PUT",
  CURLOPT_POSTFIELDS => "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"file\"\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--",
  CURLOPT_HTTPHEADER => array(
    "authorization: Basic dXNlcm5hbWU6cGFzc3dvcmQ=",
    "content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    "x-ordercloud-organisation: {your_unique_header_here}"
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
import http.client

conn = http.client.HTTPSConnection("https")

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"file\"\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"

headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'x-ordercloud-organisation': "{your_unique_header_here}",
    'authorization': "Basic dXNlcm5hbWU6cGFzc3dvcmQ=",
    }

conn.request("PUT", "//staging-api.ordercloud.com/resource/resource/product/%7BproductId%7D/image", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
# With shell, you can just pass the correct header with each request
curl --request PUT \
  --url https//staging-api.ordercloud.com/resource/resource/product/%7BproductId%7D/image \
  --header 'authorization: Basic dXNlcm5hbWU6cGFzc3dvcmQ=' \
  --header 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  --header 'x-ordercloud-organisation: {your_unique_header_here}' \
  --form file=undefined```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW");
RequestBody body = RequestBody.create(mediaType, "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"file\"\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--");
Request request = new Request.Builder()
  .url("https//staging-api.ordercloud.com/resource/resource/product/%7BproductId%7D/image")
  .put(body)
  .addHeader("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
  .addHeader("x-ordercloud-organisation", "{your_unique_header_here}")
  .addHeader("authorization", "Basic dXNlcm5hbWU6cGFzc3dvcmQ=")
  .build();

Response response = client.newCall(request).execute();
```


```ruby
require 'uri'
require 'net/http'

url = URI("https//staging-api.ordercloud.com/resource/resource/product/%7BproductId%7D/image")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Put.new(url)
request["content-type"] = 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW'
request["x-ordercloud-organisation"] = '{your_unique_header_here}'
request["authorization"] = 'Basic dXNlcm5hbWU6cGFzc3dvcmQ='
request["cache-control"] = 'no-cache'
request["postman-token"] = 'a1fa20e4-a1b5-2d64-5596-0223fa05f5ca'
request.body = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"images\"\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"

response = http.request(request)
puts response.read_body
```

```html
<form action="https://staging-api.ordercloud.com/resource/product/{productId}/image" method="post" name="frmUpload" enctype="multipart/form-data">
<tr>
  <td>Upload</td>
  <td align="center">:</td>
  <td><input name="images" type="file" id="file"/></td>
</tr>
<tr>
  <td>&nbsp;</td>
  <td align="center">&nbsp;</td>
  <td><input name="btnUpload" type="submit" value="Upload" /></td>
</tr>
```


The API call to upload an image is located  [here](https://docs.ordercloud.com/#!/productlibraryproducts/createProductLibraryItem).

It takes a content type :multipart-form and needs to have a field with the name images.



### Setting as default

## Removing Image
A Image can be removed with the following call.

The API call to view the list of products are [here](https://docs.ordercloud.com/#!/productlibraryproducts/findAllForOrganisation) and to view a single product is [here](https://docs.ordercloud.com/#!/productlibraryproducts/findProductLibraryItem).

## Setting Image as Default
The API call to update product can be found [here](https://docs.ordercloud.com/#!/productlibraryproducts/updateProductLibraryItem).

## Disabling a product
Global products can be disabled. Disabled products are not searched for by default and will not be imported to another orgnisations list of products.
The API call to disable a product can be found [here](https://docs.ordercloud.com/#!/productlibraryproducts/disableProductLibraryItem).

## Enabling a product
Once a product is disabled it can be re-enabled. This means it will once again function as before.
The API call to enable a product can be found [here](https://docs.ordercloud.com/#!/productlibraryproducts/enableProductLibraryItem).
