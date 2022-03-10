<!--Endpoint introduction -->
## Get Loan Payoff Information

### GET /payoff/{loanid}

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl -X GET \
  https://api.nelnet.io/loanaccountingapi/payoff/2c809e08-a5ba-4559-9c1c-4ac2555fb1e6 \
  -H 'Accept: */*' \
  -H 'Accept-Encoding: gzip, deflate' \
  -H 'Authorization: Bearer <TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'Connection: keep-alive' \
  -H 'Host: api.nelnet.io' \
  -H 'cache-control: no-cache'

```

```csharp
var client = new RestClient("https://api.nelnet.io/loanaccountingapi/payoff/2c809e08-a5ba-4559-9c1c-4ac2555fb1e6");
var request = new RestRequest(Method.GET);
request.AddHeader("cache-control", "no-cache");
request.AddHeader("Connection", "keep-alive");
request.AddHeader("Accept-Encoding", "gzip, deflate");
request.AddHeader("Host", "api.nelnet.io");
request.AddHeader("Cache-Control", "no-cache");
request.AddHeader("Accept", "*/*");
request.AddHeader("Authorization", "Bearer <TOKEN>");
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

xhr.open("GET", "https://api.nelnet.io/loanaccountingapi/payoff/2c809e08-a5ba-4559-9c1c-4ac2555fb1e6");
xhr.setRequestHeader("Authorization", "TOKEN");
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

headers = {
    'Authorization': "Bearer <TOKEN>",
    'Accept': "*/*",
    'Cache-Control': "no-cache",
    'Host': "api.nelnet.io",
    'Accept-Encoding': "gzip, deflate",
    'Connection': "keep-alive",
    'cache-control': "no-cache"
    }

conn.request("GET", "loanaccountingapi,payoff,2c809e08-a5ba-4559-9c1c-4ac2555fb1e6", headers=headers)

res = conn.getresponse()
data = res.read()

```

> JSON returned:

```json
{
    "data": {
        "loanId": "2c809e08-a5ba-4559-9c1c-4ac2555fb1e6",
        "payoffAmount": 2401.79,
        "payoffDate": "2020-02-17",
        "principalBalance": 2000,
        "feeBalance": 30,
        "interestBalance": 371.79,
        "projectedInterestAmount": 26.3,
        "lastAccrualDate": "2020-02-01",
        "interestRate": 30,
        "totalPrincipalAmount": 2000,
        "totalInterestAmount": 374.79,
        "totalFeeAmount": 30,
        "originationFee": 0
    }
}

```

<!-- LEFT: documentation -->

**Gets the payoff information for a given loan.**

### HTTP Request

`GET https://api.nelnet.io/loanaccountingapi/payoff/{loanid}`

The request has a required path parameter - `loanid` - and optional query parameter - `payoffdate`.

Parameter | Required | Type | Description
----------| -------- | ---- | -----------
loanid | yes | string (path) | The GUID identifier for the loan within Velocity.
payoffdate | no | string (query) | The payoff date for the loan.

### HTTP Response

The response object `data` contains the following fields.

Field Name | Type | Description
---------- | ------- | -------
loanId | string | The GUID identifier for the loan within Velocity.
payoffDate | string | The payoff date for the loan. 
payoffAmount | number($double) | The amount required to pay off the loan in full, as of the payoff date.
principalBalance | number($double) | The principal balance, as of today.
feeBalance | number($double) | The total fee amount due, as of today.
interestBalance | number($double) | The total interest amount due, as of today.
projectedInterestAmount | number($double) | The projected amount of interest due, as of the payoff date.
lastAccrualDate | string | The date of the most recent accrual calculation applied to the loan.
interestRate | number($double) | The loan's current interest rate.
totalPrincipalAmount | number($double) | The amount due on the loan, as of today, minus any fees and interest.
totalInterestAmount | number($double) | The total amount paid in interest over the life of the loan.
totalFeeAmount | number($double) | The total amount charged in fees over the life of the loan.
originationFee | number($double) | The fee, if applicable, charged for originating the loan.