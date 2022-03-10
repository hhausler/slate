<!--Endpoint introduction -->
## Get Current Billing Cycles

### GET /loanaccounting/billingcycles/current

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl -X GET \
  'https://api.nelnet.io/loanaccountingapi/billingcycles/current?loanid=c2d6aa46-ab71-475d-943a-dec948f99843' \
  -H 'Accept: */*' \
  -H 'Accept-Encoding: gzip, deflate' \
  -H 'Authorization: <ACCESS TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'Connection: keep-alive' \
  -H 'Host: api.nelnet.io' \
  -H 'cache-control: no-cache' \
  -H 'servicerid: 2' \
  -H 'tenantid: 314'
```

```csharp
var client = new RestClient("https://api.nelnet.io/loanaccountingapi/billingcycles/current?loanid=c2d6aa46-ab71-475d-943a-dec948f99843");
var request = new RestRequest(Method.GET);
request.AddHeader("cache-control", "no-cache");
request.AddHeader("Connection", "keep-alive");
request.AddHeader("Accept-Encoding", "gzip, deflate");
request.AddHeader("Host", "api.nelnet.io");
request.AddHeader("Cache-Control", "no-cache");
request.AddHeader("Accept", "*/*");
request.AddHeader("Authorization", "<ACCESS TOKEN>");
request.AddHeader("servicerid", "2");
request.AddHeader("tenantid", "314");
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

xhr.open("GET", "https://api.nelnet.io/loanaccountingapi/billingcycles/current?loanid=c2d6aa46-ab71-475d-943a-dec948f99843");
xhr.setRequestHeader("tenantid", "314");
xhr.setRequestHeader("servicerid", "2");
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
    'tenantid': "314",
    'servicerid': "2",
    'Authorization': "<ACCESS TOKEN>",
    'Accept': "*/*",
    'Cache-Control': "no-cache",
    'Host': "api.nelnet.io",
    'Accept-Encoding': "gzip, deflate",
    'Connection': "keep-alive",
    'cache-control': "no-cache"
    }

conn.request("GET", "loanaccountingapi,billingcycles,current", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": {
        "cycleStart": "2020-08-26",
        "cycleEnd": "2020-09-25",
        "regularPaymentAmount": 161.16,
        "isPaidAhead": true,
        "countCyclesPastDue": 0,
        "paidToDate": "2020-10-25"
    }
}
```

<!-- LEFT: documentation -->

**Get the current billing cycle start and end date, along with the regular payment amount for this cycle.**

### HTTP Request

`GET https://api.nelnet.io/lonccountingapi/billingcycles/current`

Parameter | Required | Type   | Description
----------| -------- | ------ | -----------
loanid | yes | string | The GUID identifier for the loan within Velocity.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
data | object | The response payload.
cycleStart | string | The beginning date of the billing cycle for this loan.
cycleEnd | string | The end date of the billing cycle for this loan. This is also the due date for the current billing cycle.
regularPaymentAmount | number | The regular payment amount due each payment, as determined by the loan schedule.
isPaidAhead | boolean | Indicates whether the loan is paid ahead, i.e., an overpayment has been made.
countCyclesPastDue | number | Number of cycles that the loan has been past-due (i.e., number of cycles required to bring current), if any.
paidToDate | string | The billing cycle date at which the loan is paid to, i.e., the last unpaid due date.