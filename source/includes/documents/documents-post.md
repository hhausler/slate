<!--Endpoint introduction -->
## Upload a Document

### POST /documents/upload

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl -X POST \
  https://api.nelnet.io/documentapi/documents/upload \
  -H 'Accept: */*' \
  -H 'Accept-Encoding: gzip, deflate' \
  -H 'Authorization: <ACCESS TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'Connection: keep-alive' \
  -H 'Content-Length: 7140' \
  -H 'Content-Type: multipart/form-data; boundary=--------------------------732216431004460821813039' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -H 'lettertype: 20' \
  -F file=@/Users/user/Pictures/SkateBoard1.jpeg  
```
```csharp
var client = new RestClient("https://api.nelnet.io/documentapi/documents/upload");
var request = new RestRequest(Method.POST);
request.AddHeader("cache-control", "no-cache");
request.AddHeader("Connection", "keep-alive");
request.AddHeader("Content-Length", "7140");
request.AddHeader("Accept-Encoding", "gzip, deflate");
request.AddHeader("Content-Type", "multipart/form-data; boundary=--------------------------419035496828744567458696");
request.AddHeader("Cache-Control", "no-cache");
request.AddHeader("Accept", "*/*");
request.AddHeader("Authorization", "<ACCESS TOKEN>");
request.AddHeader("lettertype", "20");
request.AddHeader("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW");
request.AddParameter("multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW", "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"file\"; filename=\"SkateBoard1.jpeg\"\r\nContent-Type: image/jpeg\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```
```javascript
var form = new FormData();
form.append("file", "/Users/user/Pictures/SkateBoard1.jpeg");

var settings = {
  "async": true,
  "crossDomain": true,
  "url": "https://api.nelnet.io/documentapi/documents/upload",
  "method": "POST",
  "headers": {
    "lettertype": "20",
    "Authorization": "<ACCESS TOKEN>",
    "Accept": "*/*",
    "Cache-Control": "no-cache",
    "Content-Type": "multipart/form-data; boundary=--------------------------419035496828744567458696",
    "Accept-Encoding": "gzip, deflate",
    "Content-Length": "7140",
    "Connection": "keep-alive",
    "cache-control": "no-cache"
  },
  "processData": false,
  "contentType": false,
  "mimeType": "multipart/form-data",
  "data": form
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```
```python
import http.client

conn = http.client.HTTPConnection("api,nelnet,io")

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"file\"; filename=\"SkateBoard1.jpeg\"\r\nContent-Type: image/jpeg\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"

headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'lettertype': "20",
    'Authorization': "<ACCESS TOKEN>",
    'Accept': "*/*",
    'Cache-Control': "no-cache",
    'Content-Type': "multipart/form-data; boundary=--------------------------419035496828744567458696",
    'Accept-Encoding': "gzip, deflate",
    'Content-Length': "7140",
    'Connection': "keep-alive",
    'cache-control': "no-cache"
    }

conn.request("POST", "documentapi,documents,upload", payload, headers)

res = conn.getresponse()
data = res.read()
```

> JSON returned:

```json
{
    "data": {
        "documentId": "6013d6bf-20ab-ceb4-8680-6dbc47400000",
        "file": {
            "originalname": "SkateBoard1.jpeg",
            "encoding": "7bit",
            "mimetype": "image/jpeg",
            "size": 6926,
            "metadata": {
                "documentCode": "20",
                "ssn": "999999999"
            }
        }
    }
}
```

<!-- LEFT: documentation -->

**Uploads a file that can be associated with a borrower and/or loan.**

Use the `/documents/upload` endpoint to upload and save supporting loan documentation for loans that are already onboarded onto the Velocity platform.

### HTTP Request

`POST https://api.nelnet.io/documentapi/documents/upload/`

**Header Parameters**

Parameter | Required | Type | Max Length | Description
-------- | -------- | --------- | ---------- | -----------
borrowerextid | no | UUID | 50 | The external reference ID for the borrower.
borrowerid | no | UUID | 36 | The identifier for the borrower associated with the document. (Must match an existing borrower - a borrowerid that has been onboarded to the system.)
borrowernumber | no | string | 50 | Borrower number associated with the document. 
documentcode | yes | string | 10 | Code associated with the document type. Defaults to *FMORIG*.
documenttitle  | no | string | 255 | Title of the document being uploaded. 
firstname | no | string | 35 | The first name of the borrower associated with this document.
lastname | no | string | 35 | The first name of the borrower associated with this document.
lender | no | string | 255 | The name of the lender who provided the document to the borrower.
lenderid | no | UUID | 36 | The identifier for the associated lender.
lettertype | no | string | 10 | Type of document being uploaded. Use *20* when sending promissory notes. Use *35* for correspondence from a borrower.
loanextid | no | UUID | 50 | The external reference number for the loan associated with the document being uploaded.
loanid | no | UUID | 36 | The identifier for the loan that this document is associated with.
loannumber | no | string | 36 | The loan number associated with the document.
source | no | string | 32 | Description of the document source.
ssn | no | string | 9 | The borrower's Social Security number. Defaults to *999999999* if not supplied.

**Body Parameters**

Parameter | Required | Type | Description
-------- | -------- | --------- | -----------
file | yes | multipart form data | The file to be uploaded.

### HTTP Response
Data | Type | Description
---- | ---- | ----
documentId | UUID | The identifier for the file/document uploaded.
file | object | Information about the file/document uploaded.
file.originalname | string | The name of the file/document uploaded.
file.encoding | string | Type of encoding used in the upload process.
file.mimetype | string | The file's MIME type.
file.size | number | The file's size.
file.metadata | object | The information saved in the FileNet system (document repository) about the file.
file.metadata.borrowerId | UUID | The identifier for the borrower associated with the file.
file.metadata.documentCode | string | The code associated with the document type.
file.metadata.letterType | string | The type of letter uploaded/saved.
file.metadata.ssn | string | The borrower's Social Security number.