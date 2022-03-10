<!--Endpoint introduction -->
## Get Maturity Details

### GET /maturitydetails

<!-- RIGHT | code samples -->

> Sample request:

```shell
curl -X GET \
  'https://api.nelnet.io/loanapi/maturitydetails?loanid=2c809e08-a5ba-4559-9c1c-4ac2555fb1e6' \
  -H 'Accept: */*' \
  -H 'Accept-Encoding: gzip, deflate' \
  -H 'Authorization: <ACCESS TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'Connection: keep-alive' \
  -H 'Host: api.nelnet.io' \
  -H 'cache-control: no-cache'
```

```csharp
var client = new RestClient("https://api.nelnet.io/loanapi/maturitydetails?loanid=2c809e08-a5ba-4559-9c1c-4ac2555fb1e6");
var request = new RestRequest(Method.GET);
request.AddHeader("cache-control", "no-cache");
request.AddHeader("Connection", "keep-alive");
request.AddHeader("Accept-Encoding", "gzip, deflate");
request.AddHeader("Host", "api.nelnet.io");
request.AddHeader("Cache-Control", "no-cache");
request.AddHeader("Accept", "*/*");
request.AddHeader("Authorization", "<ACCESS TOKEN>");
IRestResponse response = client.Execute(request);
```

```javascript
var data = null;

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("GET", "https://api.nelnet.io/loanapi/maturitydetails?loanid=2c809e08-a5ba-4559-9c1c-4ac2555fb1e6");
xhr.setRequestHeader("Authorization", "<ACCESS TOKEN>");
xhr.setRequestHeader("Accept", "*/*");
xhr.setRequestHeader("Cache-Control", "no-cache");
xhr.setRequestHeader("Host", "api.nelnet.io");
xhr.setRequestHeader("Accept-Encoding", "gzip, deflate");
xhr.setRequestHeader("Connection", "keep-alive");
xhr.setRequestHeader("cache-control", "no-cache");

xhr.send(data);
```

```python
import http.client

conn = http.client.HTTPConnection("api,nelnet,io")

payload = ""

headers = {
    'Authorization': "<ACCESS TOKEN>",
    'Accept': "*/*",
    'Cache-Control': "no-cache",
    'Host': "api.nelnet.io",
    'Accept-Encoding': "gzip, deflate",
    'Connection': "keep-alive",
    'cache-control': "no-cache"
    }

conn.request("GET", "loanapi,maturitydetails", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": {
        "tenantId": "314",
        "servicerId": "2",
        "loanId": "2c809e08-a5ba-4559-9c1c-4ac2555fb1e6",
        "paymentSchedule": {
            "firstPaymentDate": "2019-07-18",
            "finalPaymentDate": "2020-07-30",
            "term": 28,
            "maxTerm": 30
        },
        "effectiveDate": "2020-08-03",
        "maturityDate": "2020-07-30",
        "maxMaturityDate": "2020-09-30",
        "termFrequency": "bi-weekly"
    }
}
```

<!-- LEFT | documentation -->

**Returns details regarding the maturity of the loan, including term from the schedule and maturity date.**

### HTTP Request

`GET https://api.nelnet.io/loanapi/maturitydetails`

Parameter | Required | Type | Description
----------| -------- | ------ | -----------
loanid | yes | string | Loan identifier for the loan to find the payment schedules for.
effectivedate | no | string | Optional effective date for the last payment schedule.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
data | object | The response payload.
tenantId | string | The identifier for the tenant.
servicerId | string | The identifier for the servicer.
loanId | string | The identifier for the loan.
paymentSchedule | object | Information about 
paymentSchedule.firstPaymentDate | string | The first payment due date, in the *YYYY-MM-DD* format.
paymentSchedule.finalPaymentDate | string | Date of the final payment for this schedule.
paymentSchedule.term | number | The term used within the payment schedule.
paymentSchedule.maxTerm | number | Maximum term on this loan at the time of this schedule.
effectiveDate | string | The effective date for the payment schedule.
maturityDate | string | The payment due date when the loan will be paid in full. This can shift during different servicing events throughout loan repayment.
maxMaturityDate | string | The maximum that the maturity date can be. Generally, this will be the same as `maturityDate`, but sometimes a minimum payment requirement can trigger loan pay off before the full term of the loan. In this case, `maxMaturityDate` would show this extra time available.
termFrequency | enum | The term frequency of the loan. Options: *monthly, bi-weekly, weekly, quarterly*.