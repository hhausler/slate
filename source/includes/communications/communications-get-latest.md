<!--Endpoint introduction -->
## Get Latest Communications Suppression Info

### GET /communications/suppression/latest/{loanId}

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl --location --request GET 'https://api.nelnet.io/communicationsapi/communications/suppression/latest/c2d6aa46-ab71-475d-943a-dec948f99843' \
--header 'tenantid: 314' \
--header 'servicerid: 2' \
--header 'Authorization: Bearer <ACCESS TOKEN>' \
--data-raw ''
```

```csharp
var client = new RestClient("https://api.nelnet.io/communicationsapi/communications/suppression/latest/c2d6aa46-ab71-475d-943a-dec948f99843");
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

xhr.open("GET", "https://api.nelnet.io/communicationsapi/communications/suppression/latest/c2d6aa46-ab71-475d-943a-dec948f99843");
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
conn.request("GET", "/communicationsapi/communications/suppression/latest/c2d6aa46-ab71-475d-943a-dec948f99843", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.de
```

> JSON returned:

```json
{
    "data": {
        "communicationSuppressionId": "29eecbb8-58b7-4baa-aa5b-d6c7adf29237",
        "tenantId": "314",
        "servicerId": "2",
        "loanId": "c2d6aa46-ab71-475d-943a-dec948f99843",
        "lenderId": "bbfc1a01-61d4-4556-afac-3f98b970e397",
        "isSuppressed": false,
        "suppressionType": null,
        "communicationType": null,
        "createdDate": "2020-08-06T12:59:24.680Z",
        "createdBy": {}
    }
}
```

<!-- LEFT: documentation -->

**Returns the current communication suppression state for a loan.**

### HTTP Request

`GET https://api.nelnet.io/communicationsapi/communications/suppression/latest/{loanId}`

Parameter | Required | Type   | Description
----------| -------- | ------ | -----------
loanid | yes | string (path parameter) | The identifier for the loan to return records for.
suppressiontype | no | string | The suppression type.
communicationtype | no | string | The communications type.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
data | object | The response payload. All of the following is contained within `data`.
communicationSuppressionId | string | The identifier for the communications suppression.
tenantId | string | The identifier for the tenant.
servicerId | string | The identifier for the servicer.
loanId | string | The identifier for the loan.
lenderId | string | The identifier for the lender.
effectiveDate | string | The effective date for the communications suppression setting.
suppressionType | enum | The suppression type.
suppressionReason | enum | The suppression reason.
isSuppressed | boolean | Indicates whether communicationss are suppressed for the loan.
createdDate | date | The date that the suppression setting was created.
createdBy | object | Information about the user who created the suppression setting.