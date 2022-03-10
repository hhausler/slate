<!--Endpoint introduction -->
## Get Latest Fee Suppression Info for a Loan

### GET /fees/suppression/latest/{loanid}

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl --location --request GET 'https://api.nelnet.io/loanaccountingapi/fees/suppression/latest/c2d6aa46-ab71-475d-943a-dec948f99843' \
--header 'tenantid: 314' \
--header 'servicerid: 2' \
--header 'Authorization: Bearer <ACCESS TOKEN>' \
--data-raw ''
```

```csharp
var client = new RestClient("https://api.nelnet.io/loanaccountingapi/fees/suppression/latest/c2d6aa46-ab71-475d-943a-dec948f99843");
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

xhr.open("GET", "https://api.nelnet.io/loanaccountingapi/fees/suppression/latest/c2d6aa46-ab71-475d-943a-dec948f99843");
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
conn.request("GET", "/loanaccountingapi/fees/suppression/latest/c2d6aa46-ab71-475d-943a-dec948f99843", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": {
        "loanaccountingSuppressionId": "8ea82776-b247-40bd-91b3-80f524f1e39c",
        "tenantId": "314",
        "servicerId": "2",
        "loanId": "c2d6aa46-ab71-475d-943a-dec948f99843",
        "lenderId": "bbfc1a01-61d4-4556-afac-3f98b970e397",
        "effectiveDate": "2020-06-25",
        "suppressionType": "FEE",
        "suppressionReason": null,
        "isSuppressed": false,
        "createdDate": "2020-08-06T12:59:24.652Z",
        "createdBy": {}
    }
}
```

<!-- LEFT: documentation -->

**Returns latest fee suppression setting for a loan.**

### HTTP Request

`GET https://api.nelnet.io/loanaccountingapi/fees/suppression/latest/{loanid}`

Parameter | Required | Type   | Description
----------| -------- | ------ | -----------
loanid | yes | string (path parameter) | The identifier for the loan to return records for.
effectivedate | no | string | The effective date for records returned.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
data | object | The response payload. All of the following is contained within `data`.
loanaccountingSuppressionId | string | The identifier for the fee suppression.
tenantId | string | The identifier for the tenant.
servicerId | string | The identifier for the servicer.
loanId | string | The identifier for the loan.
lenderId | string | The identifier for the lender.
effectiveDate | string | The effective date for the fee suppression setting.
suppressionType | enum | The suppression type.
suppressionReason | enum | The suppression reason.
isSuppressed | boolean | Indicates whether fees are suppressed for the loan.
createdDate | date | The date that the suppression setting was created.
createdBy | object | Information about the user who created the suppression setting.