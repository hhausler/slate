<!--Endpoint introduction -->
## Calculate Interest

### POST calculators/interest

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl -X POST \
  https://api.nelnet.io/calculatorapi/interest \
  -H 'Accept: */*' \
  -H 'Cache-Control: no-cache' \
  -H 'Connection: keep-alive' \
  -H 'Content-Type: application/json' \
  -H 'Host: api.nelnet.io' \
  -H 'accept-encoding: gzip, deflate' \
  -H 'cache-control: no-cache' \
  -H 'content-length: 152' \
  -d '{
  "BeginDate": "2019-08-20",
  "EndDate": "2019-09-03",
  "InterestRate": 36,
  "CurrentPrincipalBalance": 2000,
  "InterestMethod": "actual/actual"
}'
```
```csharp
var client = new RestClient("https://api.nelnet.io/calculatorapi/interest");
var request = new RestRequest(Method.POST);
request.AddHeader("cache-control", "no-cache");
request.AddHeader("Connection", "keep-alive");
request.AddHeader("content-length", "152");
request.AddHeader("accept-encoding", "gzip, deflate");
request.AddHeader("Host", "api.nelnet.io");
request.AddHeader("Cache-Control", "no-cache");
request.AddHeader("Accept", "*/*");
request.AddHeader("Content-Type", "application/json");
request.AddParameter("undefined", "{\n  \"BeginDate\": \"2019-08-20\",\n  \"EndDate\": \"2019-09-03\",\n  \"InterestRate\": 36,\n  \"CurrentPrincipalBalance\": 2000,\n  \"InterestMethod\": \"actual/actual\"\n}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```
``` javascript
var data = JSON.stringify({
  "BeginDate": "2019-08-20",
  "EndDate": "2019-09-03",
  "InterestRate": 36,
  "CurrentPrincipalBalance": 2000,
  "InterestMethod": "actual/actual"
});

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://api.nelnet.io/calculatorapi/interest");
xhr.setRequestHeader("Content-Type", "application/json");
xhr.setRequestHeader("Accept", "*/*");
xhr.setRequestHeader("Cache-Control", "no-cache");
xhr.setRequestHeader("Host", "api.nelnet.io");
xhr.setRequestHeader("accept-encoding", "gzip, deflate");
xhr.setRequestHeader("content-length", "152");
xhr.setRequestHeader("Connection", "keep-alive");
xhr.setRequestHeader("cache-control", "no-cache");

xhr.send(data);
```
```python
import http.client

conn = http.client.HTTPConnection("api,nelnet,io")

payload = "{\n  \"BeginDate\": \"2019-08-20\",\n  \"EndDate\": \"2019-09-03\",\n  \"InterestRate\": 36,\n  \"CurrentPrincipalBalance\": 2000,\n  \"InterestMethod\": \"actual/actual\"\n}"

headers = {
    'Content-Type': "application/json",
    'Accept': "*/*",
    'Cache-Control': "no-cache",
    'Host': "api.nelnet.io",
    'accept-encoding': "gzip, deflate",
    'content-length': "152",
    'Connection': "keep-alive",
    'cache-control': "no-cache"
    }

conn.request("POST", "calculatorapi,interest", payload, headers)

res = conn.getresponse()
data = res.read()
```
> JSON returned:

```json
{
    "amount": 27.62
}
```

<!-- LEFT: documentation -->

**Calculates interest accrued between specified dates.**

Use this endpoint to calculate simple interest accrual.

### HTTP Request

`POST https://api.nelnet.io/calculatorapi/interest/`

<!--
Header Key | Info
---------- | -------
Authorization | Velocity Bearer Token
-->

Parameter | Required |  Type | Description
---------- | ------- | ------- | -------
BeginDate | yes | string (date-time) | The start of the interest-accrual period to calculate.
EndDate | yes | string (date-time) | The end of the interest-accrual period to calculate.
InterestRate | yes | double | The loan's interest rate at the time of calculation.
CurrentPrincipalBalance	| yes | double | The total balance of principal due at the time of calculation.
InterestMethod | yes | string (enum) | The interest accrual method. Options are *actual/actual, 30/360, actual/365, actual/365.25*. See also [*Interest Accrual Methods*](https://docs.nelnet.io/#interest-accrual-methods).

### HTTP Response
Field Name | Type | Description
---- | ---- | ------- 
amount | double | The dollar-amount value of the interest accrued over the period of time included in the request.