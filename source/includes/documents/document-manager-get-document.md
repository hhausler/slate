<!--You can make edits and remove comments if desired, but be sure to check your work as some formatting changes in this source file can affect how the end product builds. -->
<!--Endpoint introduction -->

## Get Document Byte Array for Document ID

### GET /documents/document/{documentId}

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl -X GET \
  'https://api.nelnet.io/documentmanagerapi/documents/document/{documentId}' \
  -H 'Accept: */*' \
  -H 'Accept-Encoding: gzip, deflate' \
  -H 'Authorization: <ACCESS TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'Connection: keep-alive' \
  -H 'Host: api.nelnet.io' \
  -H 'cache-control: no-cache'
```

```csharp
var client = new RestClient("https://api.nelnet.io/documentmanagerapi/documents/document/{documentId}");
var request = new RestRequest(Method.GET);
request.AddHeader("cache-control", "no-cache");
request.AddHeader("Connection", "keep-alive");
request.AddHeader("Accept-Encoding", "gzip, deflate");
request.AddHeader("Host", "api.nelnet.io");
request.AddHeader("Cache-Control", "no-cache");
request.AddHeader("Accept", "*/*");
request.AddHeader("Authorization", "<ACCESS TOKEN>");
IRestResponse response = client.Execute(request);
```

```javascript
var data = null;

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open(
  "GET",
  "https://api.nelnet.io/documentmanagerapi/documents/document/{documentId}"
);
xhr.setRequestHeader("Authorization", "<ACCESS TOKEN>");
xhr.setRequestHeader("Accept", "*/*");
xhr.setRequestHeader("Cache-Control", "no-cache");
xhr.setRequestHeader("Host", "api.nelnet.io");
xhr.setRequestHeader("Accept-Encoding", "gzip, deflate");
xhr.setRequestHeader("Connection", "keep-alive");
xhr.setRequestHeader("cache-control", "no-cache");

xhr.send(data);
```

```python
import http.client

conn = http.client.HTTPConnection("api,nelnet,io")

headers = {
    'Authorization': "<ACCESS TOKEN>",
    'Accept': "*/*",
    'Cache-Control': "no-cache",
    'Host': "api.nelnet.io",
    'Accept-Encoding': "gzip, deflate",
    'Connection': "keep-alive",
    'cache-control': "no-cache"
    }

conn.request("GET", "documentmanagerapi,documents,document,{documentId}", headers=headers)

res = conn.getresponse()
data = res.read()
```

> JSON returned:

```json
{
  "data": {
    "isbase64Document": true,
    "document": "string",
    "mimeType": "string",
    "fileExtension": "string"
  }
}
```

<!-- LEFT: documentation -->

**Returns document byte array and file extension and mime type.**

Use the `/documents/document` read-only endpoint to view the document byte array and data to determine the file type.

### HTTP Request

`GET https://api.nelnet.io/documentmanagerapi/documents/document/{documentId}`

**Request Header Parameters**

| Parameter  | Required | Type   | Description                             |
| ---------- | -------- | ------ | --------------------------------------- |
| documentId | true     | string | GUID uniquely identifying the document. |

### HTTP Response

| Field Name       | Type    | Description                                             |
| ---------------- | ------- | ------------------------------------------------------- |
| isBase64Document | boolean | Identifies if document byte array is in Base 64 format. |
| document         | string  | Byte array of document.                                 |
| mimeType         | string  | Mime type of document.                                  |
| fileExtension    | string  | File extension used for document type.                  |
