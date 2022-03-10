<!--Endpoint introduction -->
## Get the Remaining Term for a Loan

### GET /term

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl -X GET \
  'https://api.nelnet.io/termapi/term?loanid=c2d6aa46-ab71-475d-943a-dec948f99843' \
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
var client = new RestClient("https://api.nelnet.io/termapi/term?loanid=c2d6aa46-ab71-475d-943a-dec948f99843");
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

xhr.open("GET", "https://api.nelnet.io/termapi/term?loanid=c2d6aa46-ab71-475d-943a-dec948f99843");
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

conn.request("GET", "termapi,term", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": {
        "firstPaymentDate": "2020-09-25",
        "effectiveDate": "2020-08-03",
        "maturityDate": "2028-09-25",
        "remainingTerm": 97,
        "maxMaturityDate": "2028-09-25",
        "remainingMaxTerm": 97,
        "termFrequency": "monthly"
    }
}
```

<!-- LEFT: documentation -->

**Returns the remaining term of a given loan, based on loan ID.**

### HTTP Request

`GET https://api.nelnet.io/termapi/term`

Parameter | Required | Type   | Description
----------| -------- | ------ | -----------
loanid | yes | string | The ID of the loan to retrieve.
effectivedate | no | string | The effective date of the term.
nextduedate | no | string | The next due date of the term.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
data | object | The response payload. All of the following is contained within `data`.
firstPaymentDate | string | The first payment due date for the loan.
maturityDate | string | The date that the loan matures.
effectiveDate | string | Date that the remaining-term information is effective.
remainingTerm | number | The remaining number of payments due.
MaxMaturityDate | string | The latest date (furthest in the future) that the loan can mature to. A loan with a minimum payment (or paid ahead) might have an expected maturity date that is sooner than this max date.
remainingMaxTerm | number | The remaining time until the max term is hit.
termFrequency | enum | The term frequency of the loan. Options: *monthly, bi-weekly, weekly, quarterly*.