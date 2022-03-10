<!--Endpoint introduction -->
## Get a Document Upload Request by ID

### GET /documents/upload/{uploadid}

<!-- RIGHT | code samples -->
> Sample request:

```shell
curl -X GET \
  https://api.nelnet.io/documentmanagerapi/documents/upload/<UPLOADID> \
  -H 'Accept: */*' \
  -H 'Accept-Encoding: gzip, deflate' \
  -H 'Authorization: <ACCESS TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'Connection: keep-alive' \
  -H 'Host: api.nelnet.io' \
  -H 'cache-control: no-cache'
```

```csharp
var client = new RestClient("https://api.nelnet.io/documentmanagerapi/documents/upload/<UPLOADID>");
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
 
xhr.open("GET", "https://api.nelnet.io/documentmanagerapi/documents/upload/<UPLOADID>");
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
 
conn.request("GET", "documentmanagerapi,documents,upload,<UPLOADID>", headers=headers)
 
res = conn.getresponse()
data = res.read()
```

> JSON returned:

```json
{
  "data": {
    "uploadId": "string",
    "tenantId": "string",
   "servicerId": "string",
    "lenderId": "string",
    "metadata": {
      "fileName": "string",
      "borrowerId": "string",
      "borrowerExternalId": "string",
      "borrowerNumber": "string",
      "documentType": "string",
      "documentCode": "string",
      "documentTitle": "string",
      "firstName": "string",
      "lastName": "string",
      "lender": "string",
      "letterType": "string",
      "loanExternalId": "string",
      "loanId": "string",
      "loanNumber": "string",
      "source": "string",
      "ssn": "string",
      "mimeType": "string"
    },
    "url": "string",
    "uploadDate": "string",
    "imageId": "string",
    "imageDate": "string",
    "errors": {},
    "createdDate": "2020-01-06T21:20:53.084Z",
    "createdBy": {},
    "updatedDate": "2020-01-06T21:20:53.084Z",
    "updatedBy": {}
  }
}
```

<!--LEFT | Documentation -->

**Returns a document upload request based on uploadid.**

Use the `/documents/upload` read-only endpoint to view all upload requests to the Document Manager's `/documents/upload` POST endpoint.

### HTTP Request

`GET https://api.nelnet.io/documentmanagerapi/documents/upload/`

**Request Body Parameters**

Parameter | Required | Type | Description
-------- | -------- | ----- | -----------
uploadid | yes | string | The identifier for the upload request.

### HTTP Response
Field Name | Type | Description
---- | ---- | ----
data | object | The response payload.
data.uploadId | string | The identifier for the upload request.
data.tenantId | string | The tenant ID associated with the upload request.
data.servicerId | string | The identifier for the servicer.
data.lenderId | string | The identifier for the lender.
data.metadata | object | Information about the upload request.
data.metadata.fileName | string | The file name for the document to be uploaded.
data.metadata.borrowerId | string | The borrower ID.
data.metadata. borrowerExternalId | string | The external identifier or reference number for the borrower.
data.metadata. borrowerNumber | string | The borrower "friendly ID."
data.metadata. documentType | string | The document type.
data.metadata. documentCode | string | The document type, as generated from the document type.
data.metadata. documentTitle | string | The document title.
data.metadata.firstName | string | The borrower's first name.
data.metadata.lastName | string | The borrower's last name.
data.metadata.lender | string | The "friendly ID" for the lender associated with the document.
data.metadata.letterType | string | The letter type.
data.metadata. loanExternalId | string | The external or reference ID for the loan.
data.metadata.loanId | string | The GUID loan identifier (in Velocity).
data.metadata.loanNumber | string | The "friendly ID" for the loan (in Velocity).
data.metadata.source | string | The document source.
data.metadata.ssn | string | The borrower's Social Security number.
data.metadata. mimeType | string | The MIME type for the document or file, as generated by its file extension.
data.url | string | A generated unique URL for a repository where the document or file can be uploaded. This link remains valid for 30 minutes following the `POST` call (upload request). Upload the document or file to this URL to add it to Velocity. *See [Upload a Document via URL](https://docs.nelnet.io/#upload-a-document-via-url) for more information.*
data.uploadDate | string | The date on which the document upload request was created.
data.imageId | string | Velocity uses a third-party imaging system called FileNet. `imageId` is the identifier from the imaging system.
data.imageDate | string | The date that the document or file was processed by the imaging system.
data.errors | object | Any error responses returned.
data.createdDate | string ($date-time) | The date and time that the document upload request was created. Note: The URL used for uploading documents is valid for 300 seconds following its creation.
data.createdBy | object | The identifier for the token associated with the document upload.
data.updatedDate | string ($date-time) | The date that the request was updated, if applicable.
data.updatedBy | object | The identifier for the token associated with the latest update, if any.