<!--Endpoint introduction -->
## Calculate an Amortization Schedule

### POST /calculators/amortization

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl -X POST \
  https://api.nelnet.io/calculatorapi/amortization \
  -H 'Accept: */*' \
  -H 'Cache-Control: no-cache' \
  -H 'Connection: keep-alive' \
  -H 'Content-Type: application/json' \
  -H 'Host: api.nelnet.io' \
  -H 'accept-encoding: gzip, deflate' \
  -H 'cache-control: no-cache' \
  -H 'content-length: 197' \
  -d '{
  "Principal": 2000,
  "InterestRate": 36,
  "Term": 30,
  "InterestMethod": "actual/365",
  "AccrualStartDate": "2019-08-20",
  "FirstPaymentDate": "2019-09-03",
  "PaymentFrequency": "bi-weekly"
}'
```
```csharp
var client = new RestClient("https://api.nelnet.io/calculatorapi/amortization");
var request = new RestRequest(Method.POST);
request.AddHeader("cache-control", "no-cache");
request.AddHeader("Connection", "keep-alive");
request.AddHeader("content-length", "197");
request.AddHeader("accept-encoding", "gzip, deflate");
request.AddHeader("Host", "api.nelnet.io");
request.AddHeader("Cache-Control", "no-cache");
request.AddHeader("Accept", "*/*");
request.AddHeader("Content-Type", "application/json");
request.AddParameter("undefined", "{\n  \"Principal\": 2000,\n  \"InterestRate\": 36,\n  \"Term\": 30,\n  \"InterestMethod\": \"actual/365\",\n  \"AccrualStartDate\": \"2019-08-20\",\n  \"FirstPaymentDate\": \"2019-09-03\",\n  \"PaymentFrequency\": \"bi-weekly\"\n}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```
```javascript
var data = JSON.stringify({
  "Principal": 2000,
  "InterestRate": 36,
  "Term": 30,
  "InterestMethod": "actual/365",
  "AccrualStartDate": "2019-08-20",
  "FirstPaymentDate": "2019-09-03",
  "PaymentFrequency": "bi-weekly"
});

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://api.nelnet.io/calculatorapi/amortization");
xhr.setRequestHeader("Content-Type", "application/json");
xhr.setRequestHeader("Accept", "*/*");
xhr.setRequestHeader("Cache-Control", "no-cache");
xhr.setRequestHeader("Host", "api.nelnet.io");
xhr.setRequestHeader("accept-encoding", "gzip, deflate");
xhr.setRequestHeader("content-length", "197");
xhr.setRequestHeader("Connection", "keep-alive");
xhr.setRequestHeader("cache-control", "no-cache");

xhr.send(data);
```
```python
import http.client

conn = http.client.HTTPConnection("api,nelnet,io")

payload = "{\n  \"Principal\": 2000,\n  \"InterestRate\": 36,\n  \"Term\": 30,\n  \"InterestMethod\": \"actual/365\",\n  \"AccrualStartDate\": \"2019-08-20\",\n  \"FirstPaymentDate\": \"2019-09-03\",\n  \"PaymentFrequency\": \"bi-weekly\"\n}"

headers = {
    'Content-Type': "application/json",
    'Accept': "*/*",
    'Cache-Control': "no-cache",
    'Host': "api.nelnet.io",
    'accept-encoding': "gzip, deflate",
    'content-length': "197",
    'Connection': "keep-alive",
    'cache-control': "no-cache"
    }

conn.request("POST", "calculatorapi,amortization", payload, headers)

res = conn.getresponse()
data = res.read()
```
> JSON returned:

```json
{
    "EffectiveDate": "2019-08-20",
    "InterestRate": 36,
    "InterestMethod": "actual/365",
    "FirstPaymentDate": "2019-09-03",
    "AmortizedPaymentAmount": 81.92,
    "AmortizedPaymentTerm": 30,
    "FinalPaymentAmount": 80.36,
    "FinalPaymentDate": "2020-10-13",
    "MaxInterestRate": 0,
    "TermLength": 30,
    "MaxTerm": 30,
    "Apr": 35.900100000000037,
    "FinanceCharge": 456.04,
    "PrepaidFinanceCharge": 0,
    "PostRepaymentFees": 0,
    "TotalOfPayments": 2456.04,
    "Principal": 2000,
    "BalanceAtRepayment": 2000,
    "AccrualStartDate": "2019-08-20",
    "RepayConversionDate": "2019-08-20",
    "CappedInterest": 0,
    "Payments": [
        {
            "Number": 1,
            "ScheduleNumber": 1,
            "PaymentAmount": 81.92,
            "Principal": 54.3,
            "Interest": 27.62,
            "CumulativePrincipal": 54.3,
            "CumulativeInterest": 27.62,
            "RemainingPrincipal": 1945.7,
            "PaymentDueDate": "2019-09-03"
        },
        ... Items 2-29 removed for brevity
        {
            "Number": 30,
            "ScheduleNumber": 1,
            "PaymentAmount": 80.36,
            "Principal": 79.27,
            "Interest": 1.09,
            "CumulativePrincipal": 2000,
            "CumulativeInterest": 456.04,
            "RemainingPrincipal": 0,
            "PaymentDueDate": "2020-10-13"
       }
    ],
    "PrepaidFinanceCharges": {
        "OR": 0
    }
}
```

<!-- LEFT: documentation -->

**Calculates a basic amortization schedule based on a loan's principal, rate, and term.**

An amortization schedule generates a fixed payment amount over the term of a loan. Using the loan's starting principal balance, starting interest rate, term/duration, interest accrual method and payment frequency, the `/amortization` endpoint can generate a schedule of even payments, also known as an amortization schedule.

<aside class="warning">
This amortization calculator only works for loans that immediately enter into repayment upon disbursement.
</aside>

This endpoint returns the amortized payment amount, APR, finance cost and final payment amount, and more - all useful in displaying a complete and accurate amortization schedule for a given loan.

### HTTP Request

`POST https://api.nelnet.io/calculatorapi/amortization/`

The input body is `loanDetails`, which has the following parameters.

Parameter | Required | Type | Description
---------- | ------- | ------- | -------
Principal | yes | double | The starting balance of the loan.
InterestRate | yes | double | The interest rate for the loan at the time of amortization.
Term | yes | int32 | The loan's term or duration, expressed in number of bi-weekly periods, number of months, number of quarters or numbers of weeks, depending on the value entered for `PaymentFrequency`. **Example:** A value of *10* entered for `Term` will generate a 10-week payment schedule if `PaymentFrequency` is set to *weekly*. If `Term` is set to *10* and `PaymentFrequency` to *monthly*, the calculator will generate a 10-month schedule.
InterestMethod | yes | string | The interest accrual method. Options: *actual/actual, 30/360, actual/365, actual/365.25*. See also [Interest Accrual Methods](https://docs.nelnet.io/#interest-accrual-methods).
AccrualStartDate | yes | string (date-time) | The date that interest accrual begins.
FirstPaymentDate | yes | string (date-time) | Date that the first payment will be due.
PaymentFrequency | yes | string | The frequency of required payments over the term of the loan, used in determining the payment amount. Options: bi-weekly, monthly, quarterly, weekly. **Note** that this field affects `Term` as a bi-weekly payment frequency, for example, means that the term should be expressed as number of a bi-weekly periods (and not as the number of months or years, for example).
MinimumPaymentAmount | no | double | An optional parameter for use if the loan terms require that no payment over the life of the loan be less than a given amount.
OutstandingInterest | no | double | An optional parameter for use if the amortization schedule is being generated for a loan that has outstanding interest.
OriginationFee | no | double | An optional parameter for use if the loan has an origination fee that has been financed and thus should be included in the amortization schedule.

<aside class="notification">
The response body contains the general amortization schedule, plus an object with information about each payment within the schedule. 
Example: A 12-month, monthly-payment amortization would have 12 Payments.
</aside>

### HTTP Response
Field Name | Type | Description
----- | ----- | ----
EffectiveDate | string  (date-time) | Date the schedule is effective.
InterestRate | double | Interest rate used to calculate the schedule.
InterestMethod | string | Interest accrual method used to calculate the schedule.
FirstPaymentDate | string  (date-time) | Date the first payment is due for this schedule.
AmortizedPaymentAmount | double | Regular payment amount for this schedule.
AmortizedPaymentTerm | double | Actual term or number of payments remaining on the loan for this schedule.
FinalPaymentAmount | double | Amount of the final or last payment on this schedule.
FinalPaymentDate | string  (date-time) | Date of the final payment for this schedule.
MaxInterestRate | double | (not used)
TermLength | double | Term used on this schedule to payoff the loan.
MaxTerm | int32 | Maximum term on this loan at the time of this schedule.
Apr | double | Calculated APR for this schedule, taking into account all payments, interest and fees.
FinanceCharge | double | Total finance or interest charges for this loan
PrepaidFinanceCharge | double | Any prepaid finance charges (i.e., origination fees) for this loan.
PostRepaymentFees | double | (not used)
TotalOfPayments	| double | Sum of all the payments made on this schedule.
Principal | double | Principal balance used to calculate this schedule.
BalanceAtRepayment | double | (not used)
AccrualStartDate | string  (date-time) | Date used to start accruing interest for this payment schedule.
RepayConversionDate | string  (date-time) | Date the loan enters repayment.
CappedInterest | double | Interest amount that was capitalized and rolled into the principal balance.
Payments | object | Information about each payment in the amortization schedule. Payments is an array of payments that is as large as the total number of payments in the amortization schedule. 
Payments.Number | int32 | Identifier for the payment within the schedule.
Payments.ScheduleNumber | int32 | Sequence number for the payment within the schedule (whether this is the first payment, second payment, etc.).
Payments.PaymentAmount | double | The amount due in this payment, including both the principal and interest due in this payment.
Payments.Principal | double | The amount of principal included in this payment.
Payments.Interest | double | The amount of interest included in this payment.
Payments.CumulativePrincipal | double | Total amount of principal paid in the schedule to date. 
Payments.CumulativeInterest | double | Total amount of interest paid in the schedule to date. 
Payments.RemainingPrincipal | double | The total principal that remains due following this payment.
Payments.PaymentDueDate | string (date-time) | The due date for this payment, based on the term and payment frequency.

### Service-Specific Response Codes
In addition to the general error codes used by the Velocity API, the `/calculatorapi` service returns the following response codes.

Code | Description
----- | ----------
200 | Amortization schedule calculation completed successfully
400 | loanDetails has missing/invalid values
500 | Error occurred calculating amortization schedule