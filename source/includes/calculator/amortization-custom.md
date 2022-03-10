<!--Endpoint introduction -->
## Calculate a Custom Amortization Schedule

### POST /amortization/custom

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl --location --request POST 'api.nelnet.io/calculatorapi/amortization/custom' \
--header 'Accept: application/json' \
--header 'Content-Type: application/json' \
--data-raw '{
 "Term": 120,
 "TermFrequency": "monthly",
 "Disbursements": [
    {
      "Principal": 5000,
      "DisbursementDate": "2020-01-01"
    },
    {
      "Principal": 5000,
      "DisbursementDate": "2020-04-01"
    }
  ],
  "Periods": [
    {
      "StartDate": "2020-01-01",
      "PaymentType": "none",
      "InterestRate": 10,
      "InterestMethod": "actual/actual",
      "ReduceTerm": true
    },
    {
      "StartDate": "2020-07-01",
      "PaymentType": "principalinterest",
      "InterestRate": 10,
      "InterestMethod": "actual/actual",
      "PaymentFrequency": "monthly",
      "ReduceTerm": true,
      "FirstPaymentDate": "2020-08-01",
      "CapAtBegin": true
    }
  ]
}'
```

```csharp
var client = new RestClient("api.nelnet.io/calculatorapi/amortization/custom");
client.Timeout = -1;
var request = new RestRequest(Method.POST);
request.AddHeader("Accept", "application/json");
request.AddHeader("Content-Type", "application/json");
request.AddParameter("application/json", "{\r\n \"Term\": 120,\r\n \"TermFrequency\": \"monthly\",\r\n \"Disbursements\": [\r\n    {\r\n      \"Principal\": 5000,\r\n      \"DisbursementDate\": \"2020-01-01\"\r\n    },\r\n    {\r\n      \"Principal\": 5000,\r\n      \"DisbursementDate\": \"2020-04-01\"\r\n    }\r\n  ],\r\n  \"Periods\": [\r\n    {\r\n      \"StartDate\": \"2020-01-01\",\r\n      \"PaymentType\": \"none\",\r\n      \"InterestRate\": 10,\r\n      \"InterestMethod\": \"actual/actual\",\r\n      \"ReduceTerm\": true\r\n    },\r\n    {\r\n      \"StartDate\": \"2020-07-01\",\r\n      \"PaymentType\": \"principalinterest\",\r\n      \"InterestRate\": 10,\r\n      \"InterestMethod\": \"actual/actual\",\r\n      \"PaymentFrequency\": \"monthly\",\r\n      \"ReduceTerm\": true,\r\n      \"FirstPaymentDate\": \"2020-08-01\",\r\n      \"CapAtBegin\": true\r\n    }\r\n  ]\r\n}",  ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```

```javascript
var data = JSON.stringify({"Term":120,"TermFrequency":"monthly","Disbursements":[{"Principal":5000,"DisbursementDate":"2020-01-01"},{"Principal":5000,"DisbursementDate":"2020-04-01"}],"Periods":[{"StartDate":"2020-01-01","PaymentType":"none","InterestRate":10,"InterestMethod":"actual/actual","ReduceTerm":true},{"StartDate":"2020-07-01","PaymentType":"principalinterest","InterestRate":10,"InterestMethod":"actual/actual","PaymentFrequency":"monthly","ReduceTerm":true,"FirstPaymentDate":"2020-08-01","CapAtBegin":true}]});

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function() {
  if(this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "api.nelnet.io/calculatorapi/amortization/custom");
xhr.setRequestHeader("Accept", "application/json");
xhr.setRequestHeader("Content-Type", "application/json");

xhr.send(data);
```

```python
import http.client

conn = http.client.HTTPSConnection("api.nelnet.io")
payload = "{\r\n \"Term\": 120,\r\n \"TermFrequency\": \"monthly\",\r\n \"Disbursements\": [\r\n    {\r\n      \"Principal\": 5000,\r\n      \"DisbursementDate\": \"2020-01-01\"\r\n    },\r\n    {\r\n      \"Principal\": 5000,\r\n      \"DisbursementDate\": \"2020-04-01\"\r\n    }\r\n  ],\r\n  \"Periods\": [\r\n    {\r\n      \"StartDate\": \"2020-01-01\",\r\n      \"PaymentType\": \"none\",\r\n      \"InterestRate\": 10,\r\n      \"InterestMethod\": \"actual/actual\",\r\n      \"ReduceTerm\": true\r\n    },\r\n    {\r\n      \"StartDate\": \"2020-07-01\",\r\n      \"PaymentType\": \"principalinterest\",\r\n      \"InterestRate\": 10,\r\n      \"InterestMethod\": \"actual/actual\",\r\n      \"PaymentFrequency\": \"monthly\",\r\n      \"ReduceTerm\": true,\r\n      \"FirstPaymentDate\": \"2020-08-01\",\r\n      \"CapAtBegin\": true\r\n    }\r\n  ]\r\n}"
headers = {
  'Accept': 'application/json',
  'Content-Type': 'application/json'
}
conn.request("POST", "/calculatorapi/amortization/custom", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

> JSON returned:

```json
{
  "EffectiveDate": "2021-02-25",
  "InterestRate": 10.0,
  "InterestMethod": "actual/actual",
  "FirstPaymentDate": "2020-08-01",
  "AmortizedPaymentAmount": 141.29,
  "AmortizedPaymentTerm": 114,
  "FinalPaymentAmount": 142.98,
  "FinalPaymentDate": "2030-01-01",
  "MaxInterestRate": 0.0,
  "TermLength": 120,
  "MaxTerm": 120,
  "Apr": 9.9806279999999887,
  "FinanceCharge": 6108.75,
  "PrepaidFinanceCharge": 0.0,
  "PostRepaymentFees": 0.0,
  "TotalOfPayments": 16107.06,
  "Principal": 10000.0,
  "BalanceAtRepayment": 10371.58,
  "AccrualStartDate": "2020-01-01",
  "RepayConversionDate": "2020-07-01",
  "CappedInterest": 371.58,
  "Payments": [
    {
      "Number": 1,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 53.44,
      "Interest": 87.85,
      "CumulativePrincipal": 53.44,
      "CumulativeInterest": 87.85,
      "RemainingPrincipal": 10318.14,
      "PaymentDueDate": "2020-08-01"
    },
    // ... Items 2 - 113 removed for brevity
    {
      "Number": 114,
      "ScheduleNumber": 1,
      "PaymentAmount": 142.98,
      "Principal": 141.78,
      "Interest": 1.20,
      "CumulativePrincipal": 10371.58,
      "CumulativeInterest": 5737.17,
      "RemainingPrincipal": 0.0,
      "PaymentDueDate": "2030-01-01"
    }
  ],
  "PrepaidFinanceCharges": {
    "OR": 0.0
  }
}
```

<!-- LEFT: documentation -->

**Calculates a custom amortization schedule based on term and with multiple disbursements and/or loan periods.**

<!-- Use <aside class="notice"></aside> to add notices if needed -->

### HTTP Request

`POST https://api.nelnet.io/calculatorapi/amortization/custom`

The input body is `AmortizationDetails`, which has the following parameters. Some parameters are required.

Parameter | Required | Type   | Description
----------| -------- | ------ | -----------
Term | yes | integer($int32) | The length of the loan based on the term frequency.
TermFrequency | yes | string(enum) | The unit of measurement for term of the loan. Options: *bi-weekly*, *monthly*, *quarterly*, *weekly*
Disbursements | yes | object | Information about one or more disbursements.
Disbursements. DisbursementDetails | yes | object | Information about disbursements.
Disbursements. DisbursementDetails. Principal | yes | number($double) | The amount to be disbursed.
Disbursements. DisbursementDetails. DisbursementDate | yes | string($date-time) | The date that the disbursement occurs.
Disbursements. DisbursementDetails. Fees | no | number($double) | An optional origination fee amount.
Disbursements. DisbursementDetails. FeeType | no | string(enum) | the optional origination fee type (i.e., whether deducted from or capped onto disbursement). Options: *default*, *capped*, *repayment*, *deducted*
Periods | yes | object | One or more periods (i.e., a deferred or interest-only period and then a principal and interest period).
Periods.PeriodDetails | yes | object | Information about the loan periods.
Periods.PeriodDetails. StartDate | yes | string($date-time) | The start date for this period.
Periods.PeriodDetails. PaymentType | yes | string(enum) | The type of payment required during this period. Options: *none*, *interestonly*, *principalinterest*
Periods.PeriodDetails. InterestRate | yes | number ($double) | The interest rate charged during this period.
Periods.PeriodDetails. InterestMethod | yes | string(enum) | The accrual method used to accrue interest during this period. Options: *actual/actual*, *30/360*, *actual/365*, *actual/365.25*
Periods.PeriodDetails. PaymentFrequency | no | string(enum) | The frequency of payments during this period. Options: *bi-weekly*, *monthly*, *quarterly*, *weekly*
Periods.PeriodDetails. ReduceTerm | no | boolean | Whether this period reduces the term of the loan.
Periods.PeriodDetails. FirstPaymentDate | no | string($date-time) | The date the first payment is due for this period (if payments are required).
Periods.PeriodDetails. CapAtBegin | no | boolean | Whether interest should be capped onto the principal at the start of this period.
Periods.PeriodDetails. FeeAmount | no | number($double) | Any optional fee amount assessed when this period begins.
Periods.PeriodDetails. FeeType | no | string(enum) | The type for any optional fee assessed when this period begins. Options: *percentage*, *amount*
Periods.PeriodDetails. FeeBasedOn | no | string(enum) | The basis for any optional fee assessed when this period begins (when fee type is percentage). Options: *principalinterest*, *currentcpb*
Periods.PeriodDetails. FixedPaymentAmount | no | number($double) | Whether this period requires a fixed payment amount to be paid.
Periods.PeriodDetails. MinimumPaymentAmount | no | number($double) | The optional minimum payment amount required during this period (if payments are required).
OutstandingInterest | no | number($double) | Optional amount of outstanding unpaid interest (for a loan being re-amortized).

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
EffectiveDate | string(date-time) | Date the schedule is effective.
InterestRate | double | Interest rate used to calculate the schedule.
InterestMethod | string | Interest accrual method used to calculate the schedule.
FirstPaymentDate | string(date-time) | Date the first payment is due for this schedule.
AmortizedPaymentAmount | double | Regular payment amount for this schedule.
AmortizedPaymentTerm | double | Actual term or number of payments remaining on the loan for this schedule.
FinalPaymentAmount | double | Amount of the final or last payment on this schedule.
FinalPaymentDate | string(date-time) | Date of the final payment for this schedule.
MaxInterestRate | double | The maximum interest date, if set.
TermLength | double | Term used on this schedule to payoff the loan.
MaxTerm | number (int32) | Maximum term on this loan at the time of this schedule.
Apr | double | Calculated APR for this schedule, taking into account all payments, interest, and fees.
FinanceCharge | double | Total finance or interest charges for this loan.
PrepaidFinanceCharge | double | Any prepaid finance charges (i.e., origination fees) for this loan.
PostRepaymentFees | double | Fees assessed after payment (if any).
TotalOfPayments	| double | Sum of all the payments made on this schedule.
Principal | double | Principal balance used to calculate this schedule.
BalanceAtRepayment | double | The loan balance at repayment time.
AccrualStartDate | string(date-time) | Date used to start accruing interest for this payment schedule.
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