<!--Endpoint introduction -->
## Get Auto Debit Configuration by Loan ID

### GET /autodebit/config/loanid/history/{loanId}

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl --location --request GET 'https://api.nelnet.io/autodebitapi/autodebit/config/loanid/history/c2d6aa46-ab71-475d-943a-dec948f99843' \
--header 'tenantid: 314' \
--header 'servicerid: 2' \
--header 'Authorization: Bearer <ACCESS TOKEN>' \
--data-raw ''
```

```csharp
var client = new RestClient("https://api.nelnet.io/autodebitapi/autodebit/config/loanid/history/c2d6aa46-ab71-475d-943a-dec948f99843");
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

xhr.open("GET", "https://api.nelnet.io/autodebitapi/autodebit/config/loanid/history/c2d6aa46-ab71-475d-943a-dec948f99843");
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
conn.request("GET", "/autodebitapi/autodebit/config/loanid/history/c2d6aa46-ab71-475d-943a-dec948f99843", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": [
        {
            "autoDebitId": "3ae7c909-ce05-4bea-9a0d-87e88cbc8ef7",
            "tenantId": "314",
            "servicerId": "2",
            "borrowerId": "7f471f43-e4fc-458a-b5f6-037bd5b10a2b",
            "loanId": "c2d6aa46-ab71-475d-943a-dec948f99843",
            "routingNumber": "091000022",
            "accountNumber": "123456782",
            "accountType": "Checking",
            "accountHolderFirstName": "Alex",
            "accountHolderLastName": "Summers",
            "isActive": true,
            "onboardingId": "e3a22729-6a74-4465-be13-fa5f3e6983a1",
            "terms": {
                "type": "HTML",
                "content": "string"
            },
            "customAmount": null,
            "reason": null,
            "createdDate": "2020-07-23T19:43:54.156Z",
            "updatedDate": "2020-07-23T19:43:54.156Z",
            "createdBy": {},
            "updatedBy": {},
            "walletId": null,
            "autoDebitConfigHistoryId": "404e9dbd-87ef-40e4-a3bd-70df5c7f8784"
        }
    ],
    "paging": {
        "offset": 0,
        "limit": 20,
        "links": {
            "first": "/autodebit/config/c2d6aa46-ab71-475d-943a-dec948f99843/history/?offset=0&limit=20",
            "last": "/autodebit/config/c2d6aa46-ab71-475d-943a-dec948f99843/history/?offset=0&limit=20"
        }
    }
}
```

<!-- LEFT: documentation -->

**Returns the configuration for a given auto debit setup.**

### HTTP Request

`GET https://api.nelnet.io/autodebitapi/autodebit/config/loanid/history/{loanId}`

Parameter | Required | Type   | Description
----------| -------- | ------ | -----------
autoDebitId | yes | string (path parameter) | The ID of the auto debit config to retrieve.
offset | no | number | Use to set which record to start with in the response. Defaults to 0.
limit | no | number | Use to limit the number of records returned in the response. Defaults to 20.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
data | object | The response payload. 
autoDebitId | string | The identifier for the auto debit record.
tenantId | string | The identifier for the tenant.
servicerId | string | The identifier for the servicer.
borrowerId | string | The identifier for the borrower.
loanId | string | The identifier for the loan.
routingNumber | string | The 9-digit routing number for the account that's set up to be automatically debited for payments on this loan.
accountNumber | string | The account number for the account that's set up to be automatically debited for payments on this loan. Can be between 4 and 17 digits long.
accountType | enum | Account type for the account used by auto debit. Options: *Checking*, *Saving*.
accountHolderFirstName | string | The account holder's first name.
accountHolderLastName | string | The account holder's last name.
isActive | boolean | Set to *true* to onboard a loan with an active auto debit profile. Set to *false* to onboard a loan with auto debit information that not currently in use - the result will be that the borrower has an auto debit profile associated, but that auto ebit will not be used to collect payment unless it's activated.
onboardingId | string | A system-generated identifier for the onboarding request.
terms | object | The terms and conditions for auto debit agreed to by the borrower.
createdDate | date | The date that the record was created.
updatedDate | date | The date that the record was last updated.
createdBy | object | Information about the user account used to create the record.
updatedBy | object | Information about the user account used to update the record.
customAmount | number | Additional payment amount, if configured.
reason | string | If a borrower enrolls or unenrolls in auto debit, an optional reason can be added.
bankProfileId | string | The identifier for the bank profile.
autoDebitConfigHistoryId | string | The identifier for the auto debit history record.
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