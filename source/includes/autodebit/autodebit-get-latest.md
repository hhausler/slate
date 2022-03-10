<!--Endpoint introduction -->
## Get Latest Auto Debit Configuration

### GET /autodebit/config/loanid/latest/{loanId}

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl --location --request GET 'https://api.nelnet.io/autodebitapi/autodebit/config/loanid/latest/c2d6aa46-ab71-475d-943a-dec948f99843' \
--header 'tenantid: 314' \
--header 'servicerid: 2' \
--header 'Authorization: Bearer <ACCESS TOKEN>' \
--data-raw ''
```

```csharp
var client = new RestClient("https://api.nelnet.io/autodebitapi/autodebit/config/loanid/latest/c2d6aa46-ab71-475d-943a-dec948f99843");
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

xhr.open("GET", "https://api.nelnet.io/autodebitapi/autodebit/config/loanid/latest/c2d6aa46-ab71-475d-943a-dec948f99843");
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
conn.request("GET", "/autodebitapi/autodebit/config/loanid/latest/c2d6aa46-ab71-475d-943a-dec948f99843", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": {
        "autoDebitId": "90c407d2-0988-4ff7-9634-1e94b3599280",
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
        "onboardingId": null,
        "terms": null,
        "customAmount": 161.16,
        "reason": null,
        "createdDate": "2020-08-06T12:58:15.130Z",
        "updatedDate": "2020-08-06T12:58:15.130Z",
        "createdBy": {},
        "updatedBy": {},
        "walletId": null
    }
}
```

<!-- LEFT: documentation -->

**Get the latest auto debit config by loan id.**

### HTTP Request

`GET https://api.nelnet.io/autodebitapi/autodebit/config/loanid/latest/{loanId}`

Parameter | Required | Type   | Description
----------| -------- | ------ | -----------
autoDebitId | yes | string (path parameter) | The ID of the auto debit config to retrieve.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
data | object | The response payload. 
autoDebitId | string | The identifier for the auto debit config.
tenantId | string | The identifier for the tenant.
servicerId | string | The identifier for the servicer.
borrowerId | string | The identifier for the borrower.
loanId | string | The identifier for the loan.
routingNumber | string | The 9-digit routing number for the account that's set up to be automatically debited for payments on this loan.
accountNumber | string | The account number for the account that's set up to be automatically debited for payments on this loan. Can be between 4 and 17 digits long.
accountType | enum | Account type for the account used by auto debit. Options: *Checking*, *Saving*.
accountHolderFirstName | string | The account holder's first name.
accountHolderLastName | string | The account holder's last name.
isActive | boolean | Set to *true* to onboard a loan with an active auto debit profile. Set to *false* to onboard a loan with auto debit information that not currently in use - the result will be that the borrower has an auto debit profile associated, but that auto debit will not be used to collect payment unless it's activated.
onboardingId | string | A system-generated identifier for the onboarding request.
terms | object | The terms and conditions for auto debit agreed to by the borrower.
createdDate | date | The date that the record was created.
updatedDate | date | The date that the record was last updated.
createdBy | object | Information about the user account used to create the record.
updatedBy | object | Information about the user account used to update the record.
customAmount | number | Additional payment amount, if configured.
reason | string | If a borrower enrolls or unenrolls in auto debit, an optional reason can be added.
walletId | string | The identifier for the bank profile.