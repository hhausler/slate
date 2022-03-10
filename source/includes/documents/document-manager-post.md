<!--Endpoint introduction -->
## Create a Document Upload Request

### POST /documents/upload

<!-- RIGHT: code samples -->
> Sample request:

```shell
curl -X POST \
  https://api.nelnet.io/documentmanagerapi/documents/upload \
  -H 'Accept: */*' \
  -H 'Accept-Encoding: gzip, deflate' \
  -H 'Authorization: <ACCESS TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'Connection: keep-alive' \
  -H 'Content-Length: 646' \
  -H 'Content-Type: application/json' \
  -H 'Host: api.nelnet.io' \
  -H 'cache-control: no-cache' \
  -d '{
  "fileName": "string",
  "documentType": "PROMISSORY NOTE",
  "documentTitle": "string",
  "lender": "string",
  "lenderId": "string",
  "firstName": "string",
  "lastName": "string",
  "borrowerId": "string",
  "borrowerExternalId": "string",
  "borrowerNumber": "string",
  "ssn": "string",
  "loanId": "string",
  "loanExternalId": "string",
  "loanNumber": "string",
  "source": "string"
}'
```

```csharp
var client = new RestClient("https://api.nelnet.io/documentmanagerapi/documents/upload");
var request = new RestRequest(Method.POST);
request.AddHeader("cache-control", "no-cache");
request.AddHeader("Connection", "keep-alive");
request.AddHeader("Content-Length", "646");
request.AddHeader("Accept-Encoding", "gzip, deflate");
request.AddHeader("Host", "api.nelnet.io");
request.AddHeader("Cache-Control", "no-cache");
request.AddHeader("Accept", "*/*");
request.AddHeader("Authorization", "<ACCESS TOKEN>");
request.AddHeader("Content-Type", "application/json");
request.AddParameter("undefined", "{\n  \"fileName\": \"string\",\n  \"documentType\": \"PROMISSORY NOTE\",\n  \"documentTitle\": \"string\",\n  \"lender\": \"string\",\n  \"lenderId\": \"string\",\n  \"firstName\": \"string\",\n  \"lastName\": \"string\",\n  \"borrowerId\": \"string\",\n  \"borrowerExternalId\": \"string\",\n  \"borrowerNumber\": \"string\",\n  \"ssn\": \"string\",\n  \"loanId\": \"string\",\n  \"loanExternalId\": \"string\",\n  \"loanNumber\": \"string\",\n  \"source\": \"string\"\n}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```javascript
var data = JSON.stringify({
  "fileName": "string",
  "documentType": "PROMISSORY NOTE",
  "documentTitle": "string",
  "lender": "string",
  "lenderId": "string",
  "firstName": "string",
  "lastName": "string",
  "borrowerId": "string",
  "borrowerExternalId": "string",
  "borrowerNumber": "string",
  "ssn": "string",
  "loanId": "string",
  "loanExternalId": "string",
  "loanNumber": "string",
  "source": "string"
});
 
var xhr = new XMLHttpRequest();
xhr.withCredentials = true;
 
xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});
 
xhr.open("POST", "https://api.nelnet.io/documentmanagerapi/documents/upload");
xhr.setRequestHeader("Content-Type", "application/json");
xhr.setRequestHeader("Authorization", "<ACCESS TOKEN>");
xhr.setRequestHeader("Accept", "*/*");
xhr.setRequestHeader("Cache-Control", "no-cache");
xhr.setRequestHeader("Host", "api.nelnet.io");
xhr.setRequestHeader("Accept-Encoding", "gzip, deflate");
xhr.setRequestHeader("Content-Length", "646");
xhr.setRequestHeader("Connection", "keep-alive");
xhr.setRequestHeader("cache-control", "no-cache");
 
xhr.send(data);
```

```python
import http.client
 
conn = http.client.HTTPConnection("api,nelnet,io")
 
payload = "{\n  \"fileName\": \"string\",\n  \"documentType\": \"PROMISSORY NOTE\",\n  \"documentTitle\": \"string\",\n  \"lender\": \"string\",\n  \"lenderId\": \"string\",\n  \"firstName\": \"string\",\n  \"lastName\": \"string\",\n  \"borrowerId\": \"string\",\n  \"borrowerExternalId\": \"string\",\n  \"borrowerNumber\": \"string\",\n  \"ssn\": \"string\",\n  \"loanId\": \"string\",\n  \"loanExternalId\": \"string\",\n  \"loanNumber\": \"string\",\n  \"source\": \"string\"\n}"
 
headers = {
    'Content-Type': "application/json",
    'Authorization': "<ACCESS TOKEN>",
    'Accept': "*/*",
    'Cache-Control': "no-cache",
    'Host': "api.nelnet.io",
    'Accept-Encoding': "gzip, deflate",
    'Content-Length': "646",
    'Connection': "keep-alive",
    'cache-control': "no-cache"
    }
 
conn.request("POST", "documentmanagerapi,documents,upload", payload, headers)
 
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
    "createdDate": "2020-01-06T20:30:44.750Z",
    "createdBy": {},
    "updatedDate": "2020-01-06T20:30:44.750Z",
    "updatedBy": {}
  }
}
```
<!--LEFT: Documentation -->

**Creates a document upload request, generating a response that can be used to uploads a file associated with a borrower and/or loan.**

Use the `/documents/upload` endpoint to create a document upload request. The response payload includes a URL to a temporary storage location where you can then upload the document or file to be added to Velocity.

### HTTP Request

`POST https://api.nelnet.io/documentmanagerapi/documents/upload/`

**Request Body Parameters**

The object `body` is required and should contain values for all of the following required parameters. 

**Note:** The request must also include a valid value for at least one of the borrower or loan parameter to ensure that the document get associated with a borrower and/or loan. In other words, you must have a value for at least one of the following borrower parameters: `borrowerId`, `borrowerExternalId`, `borrowerNumber`, `ssn` OR at least one of the following loan parameters: `loanExternalId`, `loanId`, `loanNumber`.

Parameter | Required | Type | Description
-------- | -------- | ---------  | -----------
fileName | yes | string | The file name for the document to be uploaded.
documentType | yes | enum | The type of document or file to be uploaded. Can be either *PROMISSORY NOTE* or *INCOMING CORRESPONDENCE FROM BORROWER*.
documentTitle | yes | string | A title for the document or file to be uploaded.
lender | yes | string | The name of the lender associated with the loan that the document or file is associated with.
lenderId | yes | string | The identifier for the lender associated with the loan that the document or file is associated with.
firstName | yes | string | The borrower's first name.
lastName | yes | string | The borrower's last name.
borrowerId | no (see the note above) | string | The identifier (within Velocity) for the borrower.
borrowerExternalId | no | string | The external identifier for a borrower, such as the ID from the loan origination system.
borrowerNumber | no | string | The "friendly ID" for the borrower within Velocity (not the GUID).
ssn | no | string | The borrower's Social Security number. Adding this associates the document at the borrower level.
loanExternalId | no | string | The external identifier for a loan, such as the ID from the loan origination system.
loanId | no | string | The GUID identifier for the loan within Velocity.
loanNumber | no | string | The "friendly ID" for the loan within Velocity.
source | yes | string | The source of the document. (Open text field.)

### HTTP Response

Data | Type | Description
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
data.metadata.borrowerNumber | string | The borrower "friendly ID."
data.metadata.documentType | string | The document type.
data.metadata.documentCode | string | The document type, as generated from the document type.
data.metadata.documentTitle | string | The document title.
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
data.url | string | A generated unique URL for a repository where the document or file can be uploaded. This link remains valid for 300 seconds following the POST call (upload request). Upload the document or file to this URL to add it to Velocity. *See [Upload a Document via URL](https://docs.nelnet.io/#upload-a-document-via-url) for more information.*
data.uploadDate | string | The date on which the document upload request was created.
data.imageId | string | Velocity uses a third-party imaging system called FileNet. `imageId` is the identifier from the imaging system.
data.imageDate | string | The date that the document or file was processed by the imaging system.
data.errors | object | Any error responses returned.
data.createdDate | string ($date-time) | The date and time that the document upload request was created. Note: The URL used for uploading documents is valid for 300 seconds following its creation.
data.createdBy | object | The identifier for the token associated with the document upload.
data.updatedDate | string ($date-time) | The date that the request was updated, if applicable.
data.updatedBy | object | The identifier for the token associated with the latest update, if any.