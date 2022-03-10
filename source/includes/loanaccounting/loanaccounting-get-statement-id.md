<!--Endpoint introduction -->
## Get a Statement by ID

### GET /statements/{statementId}

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl --location --request GET 'https://api.nelnet.io/loanaccountingapi/statements/c713985a-9645-4880-913f-1230cf4e4d6b' \
--header 'tenantid: 314' \
--header 'servicerid: 2' \
--header 'Authorization: Bearer <ACCESS TOKEN>' \
--data-raw ''
```

```csharp
var client = new RestClient("https://api.nelnet.io/loanaccountingapi/statements/c713985a-9645-4880-913f-1230cf4e4d6b");
client.Timeout = -1;
var request = new RestRequest(Method.GET);
request.AddHeader("tenantid", "314");
request.AddHeader("servicerid", "2");
request.AddHeader("Authorization", "Bearer <ACCESS TOKEN>");
request.AddParameter("text/plain", "",  ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```

```javascript
var data = "";

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function() {
  if(this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("GET", "https://api.nelnet.io/loanaccountingapi/statements/c713985a-9645-4880-913f-1230cf4e4d6b");
xhr.setRequestHeader("tenantid", "314");
xhr.setRequestHeader("servicerid", "2");
xhr.setRequestHeader("Authorization", "Bearer <ACCESS TOKEN>");

xhr.send(data);
```

```python
import http.client
import mimetypes
conn = http.client.HTTPSConnection("api.nelnet.io")
payload = ''
headers = {
  'tenantid': '314',
  'servicerid': '2',
  'Authorization': 'Bearer <ACCESS TOKEN>'
}
conn.request("GET", "/loanaccountingapi/statements/c713985a-9645-4880-913f-1230cf4e4d6b", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": {
        "statementId": "c713985a-9645-4880-913f-1230cf4e4d6b",
        "tenantId": "314",
        "servicerId": "2",
        "loanId": "2c809e08-a5ba-4559-9c1c-4ac2555fb1e6",
        "statementDate": "2020-01-31",
        "nextDueDate": "2020-02-13",
        "currentAmountDue": 85,
        "pastAmountDue": 1272,
        "feeAmountDue": 15,
        "totalAmountDue": 1372,
        "createdDate": "2020-01-31T11:01:33.919Z",
        "updatedDate": "2020-01-31T11:01:33.919Z",
        "scanline": "5625577569840964620200213001372001"
    }
}
```

<!-- LEFT: documentation -->

**Returns a specific statement.**

### HTTP Request

`GET https://api.nelnet.io/loanaccountingapi/statements/{statementId}`

Parameter | Required | Type   | Description
----------| -------- | ------ | -----------
statementId | yes | | string (path parameter) | The identifier for the statement to retrieve.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
data | object | The response payload.
tenantId | string | The identifier for the tenant.
servicerId | string | The identifier for the servicer.
statementId | string | The identifier for the statement.
loanId | string | The identifier for the loan.
statementDate | string | The next statement date for the loan.
nextDueDate | string | The next payment due date for the loan.
currentAmountDue | number | Amount due on the next due date.
pastAmountDue | number | Past amount due.
feeAmountDue | number | Fee amount due.
totalAmountDue | number | Total amount due.
scanline | string | A unique identifier for the statement, used to associate a statement and payment.
createdDate | date | The date that the statement records were created.
updatedDate | date | The date that the statement records were last updated.