<!--Endpoint introduction -->
## Upload a Document via URL

### PUT {UPLOADURL}

<!-- RIGHT: code samples -->
> Sample request:

```shell
curl --location --request PUT '<UPLOAD URL>' \
--header 'Content-Type: <CONTENT TYPE>' \
--data-binary '@/<FILE LOCATION>/<FILENAME>'
```

```csharp
var client = new RestClient("<UPLOAD URL>");
client.Timeout = -1;
var request = new RestRequest(Method.PUT);
request.AddHeader("Content-Type", "<CONTENT TYPE>");
request.AddParameter("<CONTENT TYPE>", "<FILE CONTENTS>", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```

```javascript
var data = "<FILE CONTENTS>";

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function() {
  if(this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("PUT", "<UPLOAD URL>");
xhr.setRequestHeader("Content-Type", "<CONTENT TYPE>");

xhr.send(data);
```

```python
import http.client

conn = http.client.HTTPSConnection("<HOST>")
payload = "<FILE CONTENTS>"
headers = {
  'Content-Type': '<CONTENT TYPE>'
}
conn.request("PUT", "<URL PATHS>", payload, headers)
res = conn.getresponse()
data = res.read()
```

> JSON returned:

```json
EMPTY - 200 Status
```
<!--LEFT: Documentation -->

**Uploads a file that can be associated with a borrower and/or loan.**

A successful `POST /documents/upload` call returns a URL for a temporary storage location where you can upload a document or file associated with a borrower and/or loan. The URL is valid for 300 seconds after the call. Use the URL in your `PUT` call to upload the document.

### HTTP Request

`PUT {uploadUrl}`

### HTTP Response

A successful response only contains the 200 status code. To verify information about the request, see *[Get a Document Upload Request by Upload Id](https://docs.nelnet.io/#get-a-document-upload-request-by-uploadid)*.