<!--Endpoint introduction -->
## Get A Loan Modification Setting by ID

### GET /loanmodificationsettings/{loanmodificationsettingid}

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl --location --request GET 'https://api.nelnet.io/loanmodificationapi/loanmodificationsettings/9c37ad0b-8658-4cf3-abe2-c2f8575f0be2' \
--header 'tenantid: 314' \
--header 'servicerid: 2' \
--header 'Authorization: Bearer <ACCESS TOKEN>' \
--data-raw ''
```

```csharp
var client = new RestClient("https://api.nelnet.io/loanmodificationapi/loanmodificationsettings/9c37ad0b-8658-4cf3-abe2-c2f8575f0be2");
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

xhr.open("GET", "https://api.nelnet.io/loanmodificationapi/loanmodificationsettings/9c37ad0b-8658-4cf3-abe2-c2f8575f0be2");
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
conn.request("GET", "/loanmodificationapi/loanmodificationsettings/9c37ad0b-8658-4cf3-abe2-c2f8575f0be2", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": {
        "loanModificationSettingId": "9c37ad0b-8658-4cf3-abe2-c2f8575f0be2",
        "tenantId": "314",
        "servicerId": "2",
        "loanProgramId": "50023379-ef51-4262-b428-84865cd20f41",
        "description": "Permanent Int Rate Change 7%",
        "isActive": true,
        "interestRateReduction": {
            "type": "flat rate",
            "amount": 7
        },
        "paymentAmountReduction": {
            "type": "dollar",
            "amount": 0
        },
        "isBackdatedAllowed": true,
        "isTemporary": false,
        "bringLoanCurrent": true,
        "reamRequired": "start",
        "capInterest": true,
        "createdDate": "2020-07-08T15:55:37.382Z",
        "createdBy": {},
        "updatedDate": "2020-07-08T15:55:37.382Z",
        "updatedBy": {}
    }
}
```

<!-- LEFT: documentation -->

**Returns a loan modification setting for a loan program.**

### HTTP Request

`GET https://api.nelnet.io/loanmodificationapi/loanmodificationsettings/{loanmodificationsettingid}`

Parameter | Required | Type   | Description
----------| -------- | ------ | -----------
loanmodificationsettingid | yes | string (path parameter) | The identifier for the loan modification settings.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
loanModificationSettingId | string | The identifier for the loan modification settings.
tenantId | string | The identifier for the tenant.
servicerId | string | The identifier for the servicer.
loanProgramId | string | The identifier for the loan program.
description | string | 
isActive | boolean | 
interestRateReduction | object |
interestRateReduction.type | enum | 
interestRateReduction.amount | number | 
paymentAmountReduction | object |
paymentAmountReduction.type | enum |
paymentAmountReduction.amount | number | 
isBackdatedAllowed | boolean | 
isTemporary | boolean | 
duration | number | 
bringLoanCurrent | boolean | 
reamRequired | enum | 
capInterest | boolean | 
createdDate | date | 
createdBy | object |
updatedDate | date | 
updatedBy | object | 