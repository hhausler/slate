<!--Endpoint introduction -->
## Get Loan Modification Settings

### GET /loanmodificationsettings

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl --location --request GET 'https://api.nelnet.io/loanmodificationapi/loanmodificationsettings?loanprogramid=50023379-ef51-4262-b428-84865cd20f41' \
--header 'tenantid: 314' \
--header 'servicerid: 2' \
--header 'Authorization: Bearer <ACCESS TOKEN>' \
--data-raw ''
```

```csharp
var client = new RestClient("https://api.nelnet.io/loanmodificationapi/loanmodificationsettings?loanprogramid=50023379-ef51-4262-b428-84865cd20f41");
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

xhr.open("GET", "https://api.nelnet.io/loanmodificationapi/loanmodificationsettings?loanprogramid=50023379-ef51-4262-b428-84865cd20f41");
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
conn.request("GET", "/loanmodificationapi/loanmodificationsettings?loanprogramid=50023379-ef51-4262-b428-84865cd20f41", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": [
        {
            "loanModificationSettingId": "2e222844-5ddb-4b70-8bf6-c554cd5e5f53",
            "tenantId": "314",
            "servicerId": "2",
            "loanProgramId": "50023379-ef51-4262-b428-84865cd20f41",
            "description": "Permanent Int Rate Change 13%",
            "isActive": true,
            "interestRateReduction": {
                "type": "flat rate",
                "amount": 13
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
            "createdDate": "2020-07-08T15:27:44.002Z",
            "createdBy": {},
            "updatedDate": "2020-07-08T15:27:44.002Z",
            "updatedBy": {}
        },
        {
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
    ],
    "paging": {
        "rows": 0,
        "pages": 0,
        "offset": 0,
        "limit": 20,
        "links": {
            "first": "/loanmodificationsettings?offset=0&limit=20&loanprogramid=50023379-ef51-4262-b428-84865cd20f41&isactive=undefined",
            "last": "/loanmodificationsettings?offset=0&limit=20&loanprogramid=50023379-ef51-4262-b428-84865cd20f41&isactive=undefined"
        }
    }
}
```

<!-- LEFT: documentation -->

**Returns a list of loan modification settings for a loan program.**

### HTTP Request

`GET https://api.nelnet.io/loanmodificationapi/loanmodificationsettings`

Parameter | Required | Type   | Description
----------| -------- | ------ | -----------
loanprogramid | yes | string | The ID for the loan program.
isactive | no | boolean | The optional parameter for active loan modifications.
offset | no | number | Use to set which record to start with in the response. Defaults to 0.
limit | no | number | Use to limit the number of records returned in the response. Defaults to 20.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
paging | object | Information about the paging of the results returned, within the total results available.
paging.rows | string | Rows included in the records returned.
paging.pages | string | Pages included in the records returned.
paging.offset | number | The starting record in the return - the offset between the records returned and list of total records.
paging.limit | number | The number of records per page. 
paging.links | object | Information about the pagination and links in the response.
paging.links.first | string | A link to the first page of records returned.
paging.links.last | string | A link to the last page of records returned.
paging.links.previous | string | A link to the previous page in the list of records returned.
paging.links.next | string | A link to the next page in the list of records returned.
data | object | The response payload. All of the following is contained within `data`.
loanModificationSettingId | string | The identifier for the loan modification setting.
tenantId | string | The identifier for the tenant.
servicerId | string | The identifier for the servicer.
loanProgramId | string | The identifier for the loan program.
description | string | A description of the loan modification.
isActive | boolean | Indicates whether the loan modification is currently active.
interestRateReduction | object | Information about interest rate reductions.
interestRateReduction.type | enum | The interest rate reduction type.
interestRateReduction.amount | number | The interest rate reduction amount.
paymentAmountReduction | object | Information about payment amount reductions.
paymentAmountReduction.type | enum | The payment amount reduction type.
paymentAmountReduction.amount | number | The payment amount reduction amount.
isBackdatedAllowed | boolean | Indicates whether the loan modification can be back-dated.
isTemporary | boolean | Indicates whether the loan modification is temporary (true) or permanent (false).
duration | number | If the loan modification is temporary, the duration in number of billing cycles.
bringLoanCurrent | boolean | Indicates whether, when the loan modification is applied, this brings the loan current.
reamRequired | enum | Indicates whether, when the loan modification is applied, a reamortization is required.
capInterest | boolean | Indicates whether, when the loan modification is applied, the interest should be capped.
createdDate | date | The date that the record was created.
createdBy | object | The user who created the record.
updatedDate | date | The date that the record was last updated.
updatedBy | object | The user who last updated the record.