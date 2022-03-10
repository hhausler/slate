<!--Endpoint introduction -->
## Get Statement Suppression History for a Loan

### GET /statements/suppression/history/{loanid}

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl --location --request GET 'https://api.nelnet.io/loanaccountingapi/statements/suppression/history/c2d6aa46-ab71-475d-943a-dec948f99843' \
--header 'tenantid: 314' \
--header 'servicerid: 2' \
--header 'Authorization: Bearer <ACCESS TOKEN>' \
--data-raw ''
```

```csharp
var client = new RestClient("https://api.nelnet.io/loanaccountingapi/statements/suppression/history/c2d6aa46-ab71-475d-943a-dec948f99843");
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

xhr.open("GET", "https://api.nelnet.io/loanaccountingapi/statements/suppression/history/c2d6aa46-ab71-475d-943a-dec948f99843");
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
conn.request("GET", "/loanaccountingapi/statements/suppression/history/c2d6aa46-ab71-475d-943a-dec948f99843", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": [
        {
            "loanaccountingSuppressionId": "9a0b409c-a581-42ea-b55a-cb155d44f389",
            "tenantId": "314",
            "servicerId": "2",
            "loanId": "c2d6aa46-ab71-475d-943a-dec948f99843",
            "lenderId": "bbfc1a01-61d4-4556-afac-3f98b970e397",
            "effectiveDate": "2020-06-25",
            "suppressionType": "STATEMENT",
            "suppressionReason": null,
            "isSuppressed": false,
            "createdDate": "2020-08-06T12:59:24.661Z",
            "createdBy": {
                "aud": "6kmr3v065tfji6ed0nhhf8ljs8",
                "exp": 1596722330,
                "iat": 1596718730,
                "iss": "https://cognito-idp.us-west-2.amazonaws.com/us-west-2_UiGMVxT0F",
                "sub": "d397e845-6b67-4b93-8924-28ebc0d89b7a",
                "email": "mei-chun.ho@nelnet.net",
                "groups": [
                    "admin"
                ],
                "region": "us-west-2",
                "eventId": "810f932e-7f0b-4d07-b4d5-71280c5bdc73",
                "lenders": [
                    "00000000-0000-0000-0000-000000000000"
                ],
                "authTime": 1596718730,
                "clientId": "0",
                "tenantId": "0",
                "tokenUse": "id",
                "userName": "serviceadmin",
                "borrowerId": null,
                "servicerId": "0",
                "userPoolId": "us-west-2_UiGMVxT0F",
                "phoneNumber": "+13036964303",
                "poolClientId": "6kmr3v065tfji6ed0nhhf8ljs8",
                "emailVerified": true,
                "phoneNumberVerified": true
            }
        }
    ],
    "paging": {
        "rows": 1,
        "pages": 1,
        "offset": 0,
        "limit": 20,
        "links": {
            "first": "/loanaccountingapi/statements/suppression/history?offset=0&limit=20",
            "last": "/loanaccountingapi/statements/suppression/history?offset=0&limit=20"
        }
    }
}
```

<!-- LEFT: documentation -->

**Returns the history of statement suppression for a loan.**

### HTTP Request

`VERB https://api.nelnet.io/loanaccountingapi/statements/suppression/history/{loanid}`

Parameter | Required | Type   | Description
----------| -------- | ------ | -----------
loanid | yes | string | The identifier for the loan.
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
loanaccountingSuppressionId | string | The identifier for the statement suppression
tenantId | string | The identifier for the tenant.
servicerId | string | The identifier for the servicer.
loanId | string | The identifier for the loan.
lenderId | string | The identifier for the lender.
effectiveDate | string | The effective date for the statement suppression setting.
suppressionType | enum | The suppression type.
suppressionReason | enum | The suppression reason.
isSuppressed | boolean | Indicates whether statements are suppressed for the loan.
createdDate | date | The date that the suppression setting was created.
createdBy | object | Information about the user who created the suppression setting.