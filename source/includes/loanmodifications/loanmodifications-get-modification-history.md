<!--Endpoint introduction -->
## Get Loan Modifications History by ID

### GET /loanmodifications/history/{loanmodificationid}

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl --location --request GET 'https://api.nelnet.io/loanmodificationapi/loanmodifications/history?loanid=c2d6aa46-ab71-475d-943a-dec948f99843' \
--header 'tenantid: 314' \
--header 'servicerid: 2' \
--header 'Authorization: Bearer <ACCESS TOKEN>' \
--data-raw ''
```

```csharp
var client = new RestClient("https://api.nelnet.io/loanmodificationapi/loanmodifications/history?loanid=c2d6aa46-ab71-475d-943a-dec948f99843");
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

xhr.open("GET", "https://api.nelnet.io/loanmodificationapi/loanmodifications/history?loanid=c2d6aa46-ab71-475d-943a-dec948f99843");
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
conn.request("GET", "/loanmodificationapi/loanmodifications/history?loanid=c2d6aa46-ab71-475d-943a-dec948f99843", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

> JSON returned:

```json
```

<!-- LEFT: documentation -->

**Returns a list of loan modifications for a loan.**

### HTTP Request

`GET https://api.nelnet.io/loanmodificationapi/loanmodifications/history`

Parameter | Required | Type | Description
----------| -------- | ------ | -----------
loanid | yes | string | The identifier for the loan to return loan modification history for.
status | no | string | Active, Inactive, Processing, Failure (leave blank to get all)
effectivedate | no | string | Effective Date of the Loan Modifications
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
loanModificationId | string | The identifer for the loan modification.
tenantId | string | The identifier for the tenant.
servicerId | string | The identifier for the servicer.
loanId | string | The identifier for the loan.
effectiveDate | string | The effective date for the loan modification.
endDate | string | The end date for the loan modification.
settings | object | Information about the loan modification settings.
settings.loanModificationSettingId | string | The identifier for the loan modification setting.
settings.loanProgramId | string | The identifier for the loan program.
settings.description | string | The description for the loan modification setting.
settings.isActive | boolean | Indicates whether the loan modification setting is active.
settings.interestRateReduction | object | Information about the interest rate reduction.
settings.interestRateReduction.type | enum | The type of interest rate reduction. Options: *flat rate*, *percentage*.
settings.interestRateReduction.amount | number | The interest rate reduction amount.
settings.paymentAmountReduction | object | The payment reduction amount.
settings.paymentAmountReduction.type | enum | The payment reduction type. Options: *flat rate*, *percentage*.
settings.paymentAmountReduction.amount | number | The payment reduction amount.
settings.isBackdatedAllowed | boolean | Indicates whether the loan modification can be back-dated.
settings.isTemporary | boolean | Indicates whether the loan modification is temporary (true) or permanent (false).
settings.duration | number | If the loan modification is temporary, the duration in number of billing cycles.
settings.bringLoanCurrent | boolean | Indicates whether, when the loan modification is applied, this brings the loan current.
settings.reamRequired | enum | Indicates whether, when the loan modification is applied, a reamortization is required.
settings.capInterest | boolean | Indicates whether, when the loan modification is applied, the interest should be capped.
status | string | The loan modification status.
createdDate | date | The date that the record was created.
updatedDate | date | The latest date that the record was last updated.
createdBy | object | Information about the account that created the record.
updatedBy | object | Information about the account that last updated the record.