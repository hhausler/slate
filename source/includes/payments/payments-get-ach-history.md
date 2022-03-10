<!--Endpoint introduction -->
## Get ACH Payment Suppression History for a Loan

### GET /payments/ach/suppression/history/{loanId}

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl --location --request GET 'https://api.nelnet.io/paymentapi/payments/ach/suppression/history/4e5e4ab4-5612-4eff-a782-80ef3caea5dd' \
--header 'Content-Type: application/json' \
--header 'tenantid: 314' \
--header 'servicerid: 2' \
--header 'Authorization: Bearer <token>' \
--header 'Cookie: <cookie>' \
--data-raw ''
```

```csharp
var client = new RestClient("https://api.nelnet.io/paymentapi/payments/ach/suppression/history/4e5e4ab4-5612-4eff-a782-80ef3caea5dd");
client.Timeout = -1;
var request = new RestRequest(Method.GET);
request.AddHeader("Content-Type", "application/json");
request.AddHeader("tenantid", "314");
request.AddHeader("servicerid", "2");
request.AddHeader("Authorization", "Bearer <token>");
request.AddHeader("Cookie", "<cookie>");
var body = @"";
request.AddParameter("application/json", body,  ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```

```javascript
var client = new RestClient("https://api.nelnet.io/paymentapi/payments/ach/suppression/history/4e5e4ab4-5612-4eff-a782-80ef3caea5dd");
client.Timeout = -1;
var request = new RestRequest(Method.GET);
request.AddHeader("Content-Type", "application/json");
request.AddHeader("tenantid", "314");
request.AddHeader("servicerid", "2");
request.AddHeader("Authorization", "Bearer <token>");
request.AddHeader("Cookie", "<cookie>");
var body = @"";
request.AddParameter("application/json", body,  ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```

```python
import http.client
import json
conn = http.client.HTTPSConnection("api.nelnet.io")
payload = ''
headers = {
  'Content-Type': 'application/json',
  'tenantid': '314',
  'servicerid': '2',
  'Authorization': 'Bearer <token>',
  'Cookie': '<cookie>'
}
conn.request("GET", "/paymentapi/payments/ach/suppression/history/4e5e4ab4-5612-4eff-a782-80ef3caea5dd", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": [
        {
            "paymentSuppressionId": "fc784cc0-f3c7-40af-acde-326c7aec9ae4",
            "tenantId": 314,
            "servicerId": 2,
            "loanId": "4e5e4ab4-5612-4eff-a782-80ef3caea5dd",
            "lenderId": "bbfc1a01-61d4-4556-afac-3f98b970e397",
            "suppressionType": "ACH",
            "isSuppressed": true,
            "createdBy": {
                "email": "example@example.com",
                "groups": [
                    "admin"
                ],
                "region": "us-west-2",
                "eventId": "f5ff2920-a0cd-11e8-8a3f-d13b29ff1a62",
                "lenders": [
                    "00000000-0000-0000-0000-000000000000"
                ],
                "authTime": 1534366709,
                "clientId": "0",
                "tenantId": "0",
                "tokenUse": "id",
                "userName": "admin",
                "borrowerId": null,
                "servicerId": "0",
                "userPoolId": "us-west-2_UiGMVxT0F",
                "phoneNumber": "+13039166741",
                "poolClientId": "6kmr3v065tfji6ed0nhhf8ljs8",
                "emailVerified": true,
                "phoneNumberVerified": true
            },
            "createdDate": "2018-08-15T20:59:05.807Z"
        }
    ],
    "paging": {
        "offset": 0,
        "limit": 20,
        "links": {
            "first": "/payments/ach/suppression/history/4e5e4ab4-5612-4eff-a782-80ef3caea5dd?offset=0&limit=20",
            "last": "/payments/ach/suppression/history/4e5e4ab4-5612-4eff-a782-80ef3caea5dd?offset=0&limit=20"
        }
    }
}
```

<!-- LEFT: documentation -->

### HTTP Request

`GET https://api.nelnet.io/paymentapi/payments/ach/suppression/history/{loanId}`

Parameter | Required | Type   | Description
----------| -------- | ------ | -----------
loanid | yes | string (path parameter) | The identifier for the loan to return records for.
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
paymentSuppressionId | string | The identifier for the ACH payment suppression.
tenantId | string | The identifier for the tenant.
servicerId | string | The identifier for the servicer.
loanId | string | The identifier for the loan.
lenderId | string | The identifier for the lender.
effectiveDate | string | The effective date for the ACH payment suppression setting.
suppressionType | enum | The suppression type.
suppressionReason | enum | The suppression reason.
isSuppressed | boolean | Indicates whether ACH payments are suppressed for the loan.
createdDate | date | The date that the suppression setting was created.
createdBy | object | Information about the user who created the suppression setting.