<!--Endpoint introduction -->
## Pay Off a Loan

### POST /payoff/{loanid}

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl -X POST \
  https://api.nelnet.io/loanaccountingapi/payoff/2c809e08-a5ba-4559-9c1c-4ac2555fb1e6 \
  -H 'Accept: */*' \
  -H 'Accept-Encoding: gzip, deflate' \
  -H 'Authorization: <ACCESS TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'Connection: keep-alive' \
  -H 'Content-Length: 0' \
  -H 'Host: api.nelnet.io' \
  -H 'cache-control: no-cache'

```

```csharp
var client = new RestClient("https://api.nelnet.io/loanaccountingapi/payoff/2c809e08-a5ba-4559-9c1c-4ac2555fb1e6");
var request = new RestRequest(Method.POST);
request.AddHeader("cache-control", "no-cache");
request.AddHeader("Connection", "keep-alive");
request.AddHeader("Content-Length", "0");
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

xhr.open("POST", "https://api.nelnet.io/loanaccountingapi/payoff/2c809e08-a5ba-4559-9c1c-4ac2555fb1e6");
xhr.setRequestHeader("Authorization", "<ACCESS TOKEN>");
xhr.setRequestHeader("Accept", "*/*");
xhr.setRequestHeader("Cache-Control", "no-cache");
xhr.setRequestHeader("Host", "api.nelnet.io");
xhr.setRequestHeader("Accept-Encoding", "gzip, deflate");
xhr.setRequestHeader("Content-Length", "0");
xhr.setRequestHeader("Connection", "keep-alive");
xhr.setRequestHeader("cache-control", "no-cache");

xhr.send(data);

```

```python
import http.client

conn = http.client.HTTPConnection("api,nelnet,io")

headers = {
    'Authorization': "<ACCESS TOKEN>",
    'Accept': "*/*",
    'Cache-Control': "no-cache",
    'Postman-Token': "cd16a38f-b2da-4310-9072-9970c34c6f9b,5eaddcce-184c-46c9-9dc3-7771f394f4d9",
    'Host': "api.nelnet.io",
    'Accept-Encoding': "gzip, deflate",
    'Content-Length': "0",
    'Connection': "keep-alive",
    'cache-control': "no-cache"
    }

conn.request("POST", "loanaccountingapi,payoff,2c809e08-a5ba-4559-9c1c-4ac2555fb1e6", headers=headers)

res = conn.getresponse()
data = res.read()

```

> JSON returned:

```json
{
    "data": {
        "loanId": "2c809e08-a5ba-4559-9c1c-4ac2555fb1e6",
        "payoffDate": "2020-02-17",
        "payoffAmount": 2401.79,
        "principalBalance": 2000,
        "feeBalance": 30,
        "interestBalance": 371.79,
        "paymentRequestId": "20fe8a54-b1dc-44bf-9008-ad6494037785"
    }
}

```

<!-- LEFT: documentation -->

**Calculate the payoff amount for the Loan and then post a payment to pay off the loan.**

Use this endpoint to post a non-cash payment to the loan that changes the loan's status to paid in full.

### HTTP Request

`POST https://api.nelnet.io/loanaccountingapi/payoff/{loanid}`

The request has a required path parameter - `loanid` - and optional query parameter - `payoffdate`.

Parameter | Required | Type | Description
----------| -------- | ---- | -----------
loanid | yes | string (path) | The GUID identifier for the loan within Velocity.
payoffdate | no | string (query) | The payoff date for the loan. Defaults to today's date if left blank; allows for dates in the past, but not dates in the future.

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