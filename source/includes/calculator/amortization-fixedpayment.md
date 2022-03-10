<!--Endpoint introduction -->
## Calculate a Fixed-Payment Amortization Schedule

### POST /calculators/amortization/fixedpayment

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl --location --request POST 'https://api.nelnet.io/calculatorapi/amortization/fixedpayment' \
--header 'Content-Type: application/json' \
--data-raw '{
  "Principal": 5000,
  "InterestRate": 10,
  "PaymentAmount": 100,
  "InterestMethod": "actual/actual",
  "AccrualStartDate": "2021-01-15",
  "FirstPaymentDate": "2021-01-29",
  "TermFrequency": "bi-weekly",
  "OriginationFee": 59
}'

```

```csharp
var client = new RestClient("https://api.nelnet.io/calculatorapi/amortization/fixedpayment");
client.Timeout = -1;
var request = new RestRequest(Method.POST);
request.AddHeader("Content-Type", "application/json");
request.AddParameter("application/json", "{\n  \"Principal\": 5000,\n  \"InterestRate\": 10,\n  \"PaymentAmount\": 100,\n  \"InterestMethod\": \"actual/actual\",\n  \"AccrualStartDate\": \"2021-01-15\",\n  \"FirstPaymentDate\": \"2021-01-29\",\n  \"TermFrequency\": \"bi-weekly\",\n  \"OriginationFee\": 59\n}",  ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);

```

```javascript
var data = JSON.stringify({"Principal":5000,"InterestRate":10,"PaymentAmount":100,"InterestMethod":"actual/actual","AccrualStartDate":"2021-01-15","FirstPaymentDate":"2021-01-29","TermFrequency":"bi-weekly","OriginationFee":59});

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function() {
  if(this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://api.nelnet.io/calculatorapi/amortization/fixedpayment");
xhr.setRequestHeader("Content-Type", "application/json");

xhr.send(data);

```

```python
import http.client

conn = http.client.HTTPSConnection("api.nelnet.io")
payload = "{\n  \"Principal\": 5000,\n  \"InterestRate\": 10,\n  \"PaymentAmount\": 100,\n  \"InterestMethod\": \"actual/actual\",\n  \"AccrualStartDate\": \"2021-01-15\",\n  \"FirstPaymentDate\": \"2021-01-29\",\n  \"TermFrequency\": \"bi-weekly\",\n  \"OriginationFee\": 59\n}"
headers = {
  'Content-Type': 'application/json'
}
conn.request("POST", "/calculatorapi/amortization/fixedpayment", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))

```

> JSON returned:

```json
{
  "EffectiveDate": "2021-03-02",
  "InterestRate": 10.0,
  "InterestMethod": "actual/actual",
  "FirstPaymentDate": "2021-01-29",
  "AmortizedPaymentAmount": 100.0,
  "AmortizedPaymentTerm": 56,
  "FinalPaymentAmount": 61.83,
  "FinalPaymentDate": "2023-03-10",
  "MaxInterestRate": 0.0,
  "TermLength": 56,
  "MaxTerm": 56,
  "Apr": 11.108430000000013,
  "FinanceCharge": 561.83,
  "PrepaidFinanceCharge": 59.0,
  "PostRepaymentFees": 0.0,
  "TotalOfPayments": 5561.83,
  "Principal": 4941.0,
  "BalanceAtRepayment": 5000.0,
  "AccrualStartDate": "2021-01-15",
  "RepayConversionDate": "2021-01-15",
  "CappedInterest": 0.0,
  "Payments": [
    {
      "Number": 1,
      "ScheduleNumber": 1,
      "PaymentAmount": 100.0,
      "Principal": 80.82,
      "Interest": 19.18,
      "CumulativePrincipal": 80.82,
      "CumulativeInterest": 19.18,
      "RemainingPrincipal": 4919.18,
      "PaymentDueDate": "2021-01-29"
    },
    // Items 2 - 55 removed for brevity
    {
      "Number": 56,
      "ScheduleNumber": 1,
      "PaymentAmount": 61.83,
      "Principal": 61.59,
      "Interest": 0.24,
      "CumulativePrincipal": 5000.00,
      "CumulativeInterest": 561.83,
      "RemainingPrincipal": 0.0,
      "PaymentDueDate": "2023-03-10"
    }
  ],
  "PrepaidFinanceCharges": {
    "OR": 59.0
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

`POST https://api.nelnet.io/calculatorapi/amortization/fixedpayment`

The input body is `LoanDetailsPaymentAmount`, which has the following parameters. No parameters are required.

Parameter | Required | Type | Description
----------| -------  | ---- | -----------
Principal | yes | number($double) | The total principal amount due for the loan. Must be greater than 0.
InterestRate | yes | number($double) | The loan's interest rate.
PaymentAmount | yes | number($double) | The regular fixed payment amount due (at whatever interval indicated in `TermFrequency`). Must be greater than 0.
InterestMethod | yes | enum | Options: *actual/actual, 30/360, actual/365, actual/365.25*
AccrualStartDate | yes | string($date-time) | The date that interest accrual began for the loan.
FirstPaymentDate | yes | string($date-time) | The date that the first payment for the loan wa due.
TermFrequency | yes | enum | The interval at which payments are due. Options: *bi-weekly, monthly, quarterly, weekly.*
OutstandingInterest | no | number($double) | The outstanding (unpaid) interest on the loan.
OriginationFee | no | number($double) | The fee added to the loan-amount due at the time of origination (if applicable).

### HTTP Response

The response body object `loanDetails` contains the following.

Field Name | Type | Description
---------- | ------- | -------
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
MaxTerm | number (int32) | Maximum term on this loan at the time of this schedule.
Apr | double | Calculated APR for this schedule, taking into account all payments, interest, and fees.
FinanceCharge | double | Total finance or interest charges for this loan.
PrepaidFinanceCharge | double | Any prepaid finance charges (i.e., origination fees) for this loan.
PostRepaymentFees | double | (not used)
TotalOfPayments	| double | Sum of all the payments made on this schedule.
Principal | double | Principal balance used to calculate this schedule.
BalanceAtRepayment | double | (not used)
AccrualStartDate | string  (date-time) | Date used to start accruing interest for this payment schedule.
RepayConversionDate | string (date-time) | Date the loan enters repayment.
CappedInterest | double | Interest amount that was capitalized and rolled into the principal balance.
Payments | object | Information about each payment in the amortization schedule. Payments is an array of payments that is as large as the total number of payments in the amortization schedule. 
Payments.Number | number (int32) | Identifier for the payment within the schedule.
Payments.ScheduleNumber | number (int32) | Sequence number for the payment within the schedule (whether this is the first payment, second payment, etc.).
Payments.PaymentAmount | double | The amount due in this payment, including both the principal and interest due in this payment.
Payments.Principal | double | The amount of principal included in this payment.
Payments.Interest | double | The amount of interest included in this payment.
Payments.CumulativePrincipal | double | Total amount of principal paid in the schedule to date. 
Payments.CumulativeInterest | double | Total amount of interest paid in the schedule to date. 
Payments.RemainingPrincipal | double | The total principal that remains due following this payment.
Payments.PaymentDueDate | string (date-time) | The due date for this payment, based on the term and payment frequency.
PrepaidFinanceCharges | number | The amount prepaid, if any.

### Service-Specific Response Codes
In addition to the general error codes used by the Velocity API, the `/calculatorapi` service returns the following response codes.

Code | Description
----------| ------- 
200 | Amortization schedule calculation completed successfully
400 | loanDetails has missing/invalid values
500 | Error occurred calculating amortization schedule