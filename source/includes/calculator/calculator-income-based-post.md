<!--Endpoint introduction -->
## Calculate An Income-Based Repayment Plan

### POST /incomebased/paymentschedule

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl --location --request POST 'https://api.nelnet.io/calculatorapi/incomebased/paymentschedule' \
--header 'accept: text/plain' \
--header 'Content-Type: application/json-patch+json' \
--data-raw '{​ "AnnualIncome": 0, "IncomeSharePercent": 0, "AnnualIncomeGrowthRate": 0, "InterestRate": 0, "InterestCalculationType": "compound", "CompoundFrequency": "daily", "Term": 0, "TermFrequency": "monthly", "IncomeFloor": 0, "Disbursements": [ {​ "Principal": 0, "DisbursementDate": "2021-06-23T19:43:01.274Z", "Fees": 0, "FeeType": "capped" }​ ], "Periods": [ {​ "StartDate": "2021-06-23T19:43:01.274Z", "PaymentType": "none", "FirstPaymentDate": "2021-06-23T19:43:01.274Z", "FixedPaymentAmount": 0 }​ ]}​'
```

```csharp
var client = new RestClient("https://api.nelnet.io/calculatorapi/incomebased/paymentschedule");
client.Timeout = -1;
var request = new RestRequest(Method.POST);
request.AddHeader("accept", "text/plain");
request.AddHeader("Content-Type", "application/json-patch+json");
var body = @"{ ""AnnualIncome"": 0, ""IncomeSharePercent"": 0, ""AnnualIncomeGrowthRate"": 0, ""InterestRate"": 0, ""InterestCalculationType"": ""compound"", ""CompoundFrequency"": ""daily"", ""Term"": 0, ""TermFrequency"": ""monthly"", ""IncomeFloor"": 0, ""Disbursements"": [ { ""Principal"": 0, ""DisbursementDate"": ""2021-06-23T19:43:01.274Z"", ""Fees"": 0, ""FeeType"": ""capped"" } ], ""Periods"": [ { ""StartDate"": ""2021-06-23T19:43:01.274Z"", ""PaymentType"": ""none"", ""FirstPaymentDate"": ""2021-06-23T19:43:01.274Z"", ""FixedPaymentAmount"": 0 } ]}";
request.AddParameter("application/json-patch+json", body,  ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```

```javascript
var myHeaders = new Headers();
myHeaders.append("accept", "text/plain");
myHeaders.append("Content-Type", "application/json-patch+json");
var raw = JSON.stringify({
  "AnnualIncome": 0,
  "IncomeSharePercent": 0,
  "AnnualIncomeGrowthRate": 0,
  "InterestRate": 0,
  "InterestCalculationType": "compound",
  "CompoundFrequency": "daily",
  "Term": 0,
  "TermFrequency": "monthly",
  "IncomeFloor": 0,
  "Disbursements": [
    {
      "Principal": 0,
      "DisbursementDate": "2021-06-23T19:43:01.274Z",
      "Fees": 0,
      "FeeType": "capped"
    }
  ],
  "Periods": [
    {
      "StartDate": "2021-06-23T19:43:01.274Z",
      "PaymentType": "none",
      "FirstPaymentDate": "2021-06-23T19:43:01.274Z",
      "FixedPaymentAmount": 0
    }
  ]
});
var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};
fetch("https://api.nelnet.io/calculatorapi/incomebased/paymentschedule", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

```python
import http.client
import json
conn = http.client.HTTPSConnection("api.nelnet.io")
payload = json.dumps({
  "AnnualIncome": 0,
  "IncomeSharePercent": 0,
  "AnnualIncomeGrowthRate": 0,
  "InterestRate": 0,
  "InterestCalculationType": "compound",
  "CompoundFrequency": "daily",
  "Term": 0,
  "TermFrequency": "monthly",
  "IncomeFloor": 0,
  "Disbursements": [
    {
      "Principal": 0,
      "DisbursementDate": "2021-06-23T19:43:01.274Z",
      "Fees": 0,
      "FeeType": "capped"
    }
  ],
  "Periods": [
    {
      "StartDate": "2021-06-23T19:43:01.274Z",
      "PaymentType": "none",
      "FirstPaymentDate": "2021-06-23T19:43:01.274Z",
      "FixedPaymentAmount": 0
    }
  ]
})
headers = {
  'accept': 'text/plain',
  'Content-Type': 'application/json-patch+json'
}
conn.request("POST", "/calculatorapi/incomebased/paymentschedule", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

> JSON returned:

```json
{
  "Apr": 0,
  "EffectiveDate": "2021-06-23T20:34:55.679Z",
  "InterestRate": 0,
  "InterestMethod": "string",
  "PaymentAmount": 0,
  "FirstPaymentDate": "2021-06-23T20:34:55.679Z",
  "FinalPaymentAmount": 0,
  "FinalPaymentDate": "2021-06-23T20:34:55.679Z",
  "TermLength": 0,
  "MaxTerm": 0,
  "FinanceCharge": 0,
  "PrepaidFinanceCharge": 0,
  "TotalOfPayments": 0,
  "Amount": 0,
  "AccrualStartDate": "2021-06-23T20:34:55.679Z",
  "Payments": [
    {
      "Number": 0,
      "PaymentAmount": 0,
      "Principal": 0,
      "Interest": 0,
      "CumulativePrincipal": 0,
      "CumulativeInterest": 0,
      "RemainingPrincipal": 0,
      "PaymentDueDate": "2021-06-23T20:34:55.679Z",
      "PaymentType": "string",
      "ReduceTerm": true
    }
  ],
  "Incomes": [
    {
      "beginDate": "2021-06-23T20:34:55.679Z",
      "endDate": "2021-06-23T20:34:55.679Z",
      "income": 0
    }
  ]
}
```

**Use to calculate an income-based repayment schedule.**

### HTTP Request

`POST https://api.nelnet.io/calculatorapi/calculators/incomebased/paymentschedule`

The body object `incomeBasedDetails` should contain all the following. All fields are required.

Parameter | Required | Type   | Description
----------| -------- | ------ | -----------
AnnualIncome | yes | number($double) | The borrower's annual income (estimated or verified).
IncomeSharePercent | yes | number($double) | The income-share percentage used to calculate the payment amount, expressed as a whole number (example: 9.13%).
AnnualIncomeGrowthRate | yes | number($double) | The estimated annual income increase, expressed as a whole number (example: 3%).
InterestRate | yes | number($double) | The loan's interest rate or daily growth rate, expressed as a whole number (example: 4.3%).
InterestCalculationType | yes | string (enum) | The method used to accrue interest. Options: *simple, compound*.
CompoundFrequency | yes | string(enum) | For compound interest, frequency at which interest is compounded. Options: *daily*.
Term | yes | integer($int32) | The length of the loan based on the term frequency.
TermFrequency | yes | string(enum) | The unit of measurement for the term of the loan. Options: *monthly*.
IncomeFloor | yes | number($double) | The minimum annual income below which no payment is required.
Disbursements | yes | object | Information about one or more disbursements.
Disbursements.Principal | yes | number($double) | The disbursement amount.
Disbursements.DisbursementDate | yes | string($date-time) | The disbursement date.
Disbursements.Fees | no | number($double) | The optional origination fee amount.
Disbursements.FeeType | no | string(enum) | The optional origination fee type (i.e., whether deducted from or capped onto disbursement. Options: *capped, deducted*.
Periods | yes | object | Information about one or more periods.
Periods.StartDate | yes | string($date-time) | The start date for this period.
Periods.PaymentType | yes | string(enum) | The type of payment required during this period, if payments are required. Options: *none, interestonly, incomeshare, fixed*.
Periods.FirstPaymentDate | yes | string($date-time) | The date the first payment is due for this period (if payments are required).
Periods.FixedPaymentAmount | yes | number($double) | The payment amount, if this period requires a fixed payment amount to be paid.

### HTTP Response

The body object `IncomeBasedPaymentSchedule` contains the following.

Field Name | Type | Description
---------- | ------- | -------
Apr | number($double) | The annual percentage rate 
EffectiveDate | string($date-time) | The effective date for the schedule.
InterestRate | number($double) | The interest rate used in the schedule.
InterestMethod | string | The interest method used in calculating the schedule.
FirstPaymentDate | string($date-time) | The date of the first payment in the schedule.
FinalPaymentAmount | number($double) | The total amount due in the final payment.
FinalPaymentDate | string($date-time) | The date that the final payment in the schedule is due.
MaxInterestRate | number($double) | The maximum interest rate over the term of the loan.
TermLength | integer($int32) | The actual term used to payoff the loan.
MaxTerm | integer($int32) | The maximum term allowed on the loan.
FinanceCharge | number($double) | The total finance charges (i.e., interest accrued).
PrepaidFinanceCharge | number($double) | The total prepaid finance charges (i.e., origination fees).
TotalOfPayments | number($double) | The total of all payments on the schedule.
Amount | number($double) | The total funded amount (not including interest or fees).
AccrualStartDate | string($date-time) | The date that interest starts to accrue on the loan.
Payments | object | A detailed list of all payments on the schedule.
Payments.Number | integer($int32) | Identifier for the payment.
Payments.PaymentAmount | number($double) | The total payment amount.
Payments.Principal | number($double) | The portion of payment that goes towards principal.
Payments.Interest | number($double) | The portion of payment that goes towards interest.
Payments.CumulativePrincipal | number($double) | The total principal paid as of the payment date.
Payments.CumulativeInterest | number($double) | The total interest accrued as of the payment date.
Payments.RemainingPrincipal | number($double) | The remaining principal balance as of the payment date.
Payments.PaymentDueDate | string($date-time) | The payment due date.
Payments.PaymentType | string | The type of payment.
Payments.ReduceTerm | boolean | Whether this payment reduces the total term of the loan.
Incomes | object | A list of incomes used to calculate the schedule.
Incomes.beginDate | string($date-time) | The start date that this income is included in the schedule.
Incomes.endDate | string($date-time) | The end date that this income is no longer included in the schedule.
Incomes.income | number($double) | The income total.