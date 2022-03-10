<!--You can make edits and remove comments if desired, but be sure to check your work as some formatting changes in this source file can affect how the end product builds. -->
<!--Endpoint introduction -->

## Get Document List By Borrower ID

### GET /documents/borrower-documents/{borrowerId}

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl -X GET \
 'https://api.nelnet.io/documentmanagerapi/documents/borrower-documents/{{borrowerId}}' \
  -H 'accept: application/json' \
  -H 'authorization: <ACCESS TOKEN>''
```

```csharp
var client = new RestClient("https://api.nelnet.io/documentmanagerapi/documents/borrower-documents/{BorrowerId}");
client.Timeout = -1;
var request = new RestRequest(Method.GET);
request.AddHeader("cache-control", "no-cache");
request.AddHeader("Connection", "keep-alive");
request.AddHeader("Accept-Encoding", "gzip, deflate");
request.AddHeader("Host", "api.nelnet.io");
request.AddHeader("Cache-Control", "no-cache");
request.AddHeader("Accept", "*/*");
request.AddHeader("Authorization", "<ACCESS TOKEN>");
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```

```javascript
var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open(
  "GET",
  "https://api.nelnet.io/documentmanagerapi/documents/borrower-documents/{BorrowerId}"
);
xhr.setRequestHeader("Authorization", "<ACCESS TOKEN>");
xhr.setRequestHeader("Accept", "*/*");
xhr.setRequestHeader("Cache-Control", "no-cache");
xhr.setRequestHeader("Host", "api.nelnet.io");
xhr.setRequestHeader("Accept-Encoding", "gzip, deflate");
xhr.setRequestHeader("Connection", "keep-alive");
xhr.setRequestHeader("cache-control", "no-cache");

xhr.send();
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

conn.request("GET", "/documentmanagerapi/documents/borrower-documents/{BorrowerId}", headers=headers)

res = conn.getresponse()
data = res.read()

```

> JSON returned:

```json
{
  "data": [
    {
      "documentId": "string",
      "documentDate": "string",
      "contentSize": "string",
      "mimeType": "string",
      "documentCode": "string",
      "letterType": "string",
      "fileName": "string",
      "borrowerId": "string",
      "borrowerExternalId": "string",
      "borrowerNumber": "string",
      "documentType": "string",
      "documentTitle": "string",
      "firstName": "string",
      "lastName": "string",
      "lender": "string",
      "lenderId": "string",
      "loanExternalId": "string",
      "loanId": "string",
      "loanNumber": "string",
      "source": "string",
      "ssn": "string",
      "read": true,
      "hidden": true
    }
  ]
}
```

<!-- LEFT: documentation -->

**Returns document list for entered borrower ID.**

Use the `/documents/borrower-documents/{borrowerId}` read-only endpoint to view a list of document meta data for the borrower ID entered.

### HTTP Request

`GET https://api.nelnet.io/documentmanagerapi/documents/borrower-documents/{borrowerId}`

`VERB https://api.nelnet.io/`

| Parameter  | Required | Type | Description      |
| ---------- | -------- | ---- | ---------------- |
| borrowerId | true     | GUID | The Borrower ID. |

### HTTP Response

| Field Name     | Type    | Description                                        |
| -------------- | ------- | -------------------------------------------------- |
| documentId     | string  | GUID identifying document.                         |
| documentDate   | string  | Date document was stored.                          |
| contentSize    | string  | Byte size of document.                             |
| mimeType       | string  | Mime type of document.                             |
| documentCode   | string  | Document code of document.                         |
| letterType     | string  | Letter type of document.                           |
| fileName       | string  | File name of document.                             |
| borrowerId     | string  | Borrower Id of document.                           |
| documentType   | string  | Document type of document.                         |
| documentTitle  | string  | Title of document.                                 |
| firstName      | string  | First Name of borrower.                            |
| lastName       | string  | Last Name of borrower.                             |
| lender         | string  | Lender of document.                                |
| lenderId       | string  | Lender ID of document.                             |
| loanExternalId | string  | External reference value of document.              |
| loanId         | string  | Loan ID of document.                               |
| loanNumber     | string  | Loan number of document.                           |
| source         | string  | Source location of document.                       |
| ssn            | string  | SSN of borrower.                                   |
| read           | boolean | Determines if document has been read by borrower.  |
| hidden         | boolean | Determines if document should be returned in list. |
