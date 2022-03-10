<!--Endpoint introduction -->
## Get A Payment Schedule By ID

### GET /paymentschedules/{paymentscheduleid}

<!-- RIGHT | code samples -->

> Sample request:

```shell
curl -X GET \
  https://api.nelnet.io/loanapi/paymentschedules/ffa19140-e800-46e7-8964-4c2a317fcec3 \
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
var client = new RestClient("https://api.nelnet.io/loanapi/paymentschedules/ffa19140-e800-46e7-8964-4c2a317fcec3");
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

xhr.open("GET", "https://api.nelnet.io/loanapi/paymentschedules/ffa19140-e800-46e7-8964-4c2a317fcec3");
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

conn.request("GET", "loanapi,paymentschedules,ffa19140-e800-46e7-8964-4c2a317fcec3", payload, headers)

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
        "paymentScheduleId": "ffa19140-e800-46e7-8964-4c2a317fcec3",
        "loanId": "c2d6aa46-ab71-475d-943a-dec948f99843",
        "effectiveDate": "2020-07-23",
        "interestRate": 11.75,
        "interestMethod": "actual/actual",
        "firstPaymentDate": "2020-07-25",
        "paymentAmount": 161.16,
        "term": 96,
        "maxTerm": 96,
        "finalPaymentAmount": 159.6,
        "finalPaymentDate": "2028-06-25",
        "apr": 11.7486,
        "financeCharge": 5469.8,
        "prepaidFinanceCharge": 0,
        "totalOfPayments": 15469.8,
        "principal": 10000,
        "balanceAtRepayment": 10000,
        "accrualStartDate": "2020-06-25",
        "repayConversionDate": "2020-06-25",
        "cappedInterest": 0,
        "paymentScheduleType": "fixed term",
        "payments": [
            {
                "number": 1,
                "interest": 96.31,
                "principal": 64.85,
                "paymentAmount": 161.16,
                "paymentDueDate": "2020-07-25",
                "scheduleNumber": 1,
                "cumulativeInterest": 96.31,
                "remainingPrincipal": 9935.15,
                "cumulativePrincipal": 64.85
            },
            {
                "number": 2,
                "interest": 98.88,
                "principal": 62.28,
                "paymentAmount": 161.16,
                "paymentDueDate": "2020-08-25",
                "scheduleNumber": 1,
                "cumulativeInterest": 195.19,
                "remainingPrincipal": 9872.87,
                "cumulativePrincipal": 127.13
            },
            {
                "number": 3,
                "interest": 98.26,
                "principal": 62.9,
                "paymentAmount": 161.16,
                "paymentDueDate": "2020-09-25",
                "scheduleNumber": 1,
                "cumulativeInterest": 293.45,
                "remainingPrincipal": 9809.97,
                "cumulativePrincipal": 190.03
            },
            {
                "number": 4,
                "interest": 94.48,
                "principal": 66.68,
                "paymentAmount": 161.16,
                "paymentDueDate": "2020-10-25",
                "scheduleNumber": 1,
                "cumulativeInterest": 387.93,
                "remainingPrincipal": 9743.29,
                "cumulativePrincipal": 256.71
            }
        ],
        "createdDate": "2020-07-23T19:44:01.400Z",
        "updatedDate": "2020-07-23T19:44:01.400Z"
    }
}
```

<!-- LEFT | documentation -->

**Returns list of payment schedules for a loan, based on payment schedule ID.**

### HTTP Request

`GET https://api.nelnet.io/loanapi/paymentschedules/{paymentscheduleid}`

Parameter | Required | Type | Description
----------| -------- | ------ | -----------
paymentscheduleid | yes | string | The ID of the payment schedule to retrieve.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
data | object | The response payload.
paymentScheduleId | string | Identifier (GUID) for the payment schedule.
tenantId | string | The identifier for the tenant.
servicerId | string | The identifier for the servicer.
loanId | string | The identifier for the loan.
effectiveDate | string | The effective date for the payment schedule.
interestRate | number | The loan's interest rate at the time of calculation.
interestMethod | enum | The interest accrual method. Options are *actual/actual, 30/360, actual/365, actual/365.25*. See also [*Interest Accrual Methods*](https://docs.nelnet.io/#interest-accrual-methods).
firstPaymentDate | string | Date that the first payment will be (or was) due.
paymentAmount | number | Amount due in a payment.
term | number | The loan's term or duration, expressed in number of bi-weekly periods, number of months, number of quarters or numbers of weeks, depending on the payment frequency.
maxTerm | number | Maximum term on this loan at the time of this schedule.
finalPaymentAmount | number | Amount of the final or last payment on this schedule.
finalPaymentDate | string | Date of the final payment for this schedule.
apr | number | Calculated APR for this schedule, taking into account all payments, interest and fees.
financeCharge | number | Total finance or interest charges for this loan.
prepaidFinanceCharge | number | Any prepaid finance charges (i.e., origination fees) for this loan.
totalOfPayments | number | Sum of all the payments made on this schedule.
principal | number | Principal balance used to calculate this schedule.
balanceAtRepayment | number | (not used)
accrualStartDate | string | Date used to start accruing interest for this payment schedule.
repayConversionDate | string | Date the loan enters repayment.
cappedInterest | number | Interest amount that was capitalized and rolled into the principal balance.
paymentScheduleType | enum | The payment schedule type. Options: *fixed term*, *fixed payment*. 
payments | object | Information about individual payments within the payment schedule.
payments.number | number | Identifier for the payment within the schedule.
payments.scheduleNumber | number | Sequence number for the payment within the schedule (whether this is the first payment, second payment, etc.).
payments.paymentAmount | number | The amount due in this payment, including both the principal and interest due in this payment.
payments.principal | number | The amount of principal included in this payment.
payments.interest | number | The amount of interest included in this payment.
payments.cumulativePrincipal | number | Total amount of principal paid in the schedule to date. 
payments.cumulativeInterest | number | Total amount of interest paid in the schedule to date. 
payments.remainingPrincipal | number | The total principal that remains due following this payment.
payments.paymentDueDate | string | The due date for this payment, based on the term and payment frequency.
createdDate | date | Date on which the record was created.
updatedDate | date | Date of latest update.