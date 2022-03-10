<!--Endpoint introduction -->
## Calculate A Custom Amortization Schedule

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
    {
      "Number": 2,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 53.90,
      "Interest": 87.39,
      "CumulativePrincipal": 107.34,
      "CumulativeInterest": 175.24,
      "RemainingPrincipal": 10264.24,
      "PaymentDueDate": "2020-09-01"
    },
    {
      "Number": 3,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 57.16,
      "Interest": 84.13,
      "CumulativePrincipal": 164.50,
      "CumulativeInterest": 259.37,
      "RemainingPrincipal": 10207.08,
      "PaymentDueDate": "2020-10-01"
    },
    {
      "Number": 4,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 54.84,
      "Interest": 86.45,
      "CumulativePrincipal": 219.34,
      "CumulativeInterest": 345.82,
      "RemainingPrincipal": 10152.24,
      "PaymentDueDate": "2020-11-01"
    },
    {
      "Number": 5,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 58.07,
      "Interest": 83.22,
      "CumulativePrincipal": 277.41,
      "CumulativeInterest": 429.04,
      "RemainingPrincipal": 10094.17,
      "PaymentDueDate": "2020-12-01"
    },
    {
      "Number": 6,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 55.79,
      "Interest": 85.50,
      "CumulativePrincipal": 333.20,
      "CumulativeInterest": 514.54,
      "RemainingPrincipal": 10038.38,
      "PaymentDueDate": "2021-01-01"
    },
    {
      "Number": 7,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 56.03,
      "Interest": 85.26,
      "CumulativePrincipal": 389.23,
      "CumulativeInterest": 599.80,
      "RemainingPrincipal": 9982.35,
      "PaymentDueDate": "2021-02-01"
    },
    {
      "Number": 8,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 64.71,
      "Interest": 76.58,
      "CumulativePrincipal": 453.94,
      "CumulativeInterest": 676.38,
      "RemainingPrincipal": 9917.64,
      "PaymentDueDate": "2021-03-01"
    },
    {
      "Number": 9,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 57.06,
      "Interest": 84.23,
      "CumulativePrincipal": 511.00,
      "CumulativeInterest": 760.61,
      "RemainingPrincipal": 9860.58,
      "PaymentDueDate": "2021-04-01"
    },
    {
      "Number": 10,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 60.24,
      "Interest": 81.05,
      "CumulativePrincipal": 571.24,
      "CumulativeInterest": 841.66,
      "RemainingPrincipal": 9800.34,
      "PaymentDueDate": "2021-05-01"
    },
    {
      "Number": 11,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 58.05,
      "Interest": 83.24,
      "CumulativePrincipal": 629.29,
      "CumulativeInterest": 924.90,
      "RemainingPrincipal": 9742.29,
      "PaymentDueDate": "2021-06-01"
    },
    {
      "Number": 12,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 61.22,
      "Interest": 80.07,
      "CumulativePrincipal": 690.51,
      "CumulativeInterest": 1004.97,
      "RemainingPrincipal": 9681.07,
      "PaymentDueDate": "2021-07-01"
    },
    {
      "Number": 13,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 59.07,
      "Interest": 82.22,
      "CumulativePrincipal": 749.58,
      "CumulativeInterest": 1087.19,
      "RemainingPrincipal": 9622.00,
      "PaymentDueDate": "2021-08-01"
    },
    {
      "Number": 14,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 59.57,
      "Interest": 81.72,
      "CumulativePrincipal": 809.15,
      "CumulativeInterest": 1168.91,
      "RemainingPrincipal": 9562.43,
      "PaymentDueDate": "2021-09-01"
    },
    {
      "Number": 15,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 62.69,
      "Interest": 78.60,
      "CumulativePrincipal": 871.84,
      "CumulativeInterest": 1247.51,
      "RemainingPrincipal": 9499.74,
      "PaymentDueDate": "2021-10-01"
    },
    {
      "Number": 16,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 60.61,
      "Interest": 80.68,
      "CumulativePrincipal": 932.45,
      "CumulativeInterest": 1328.19,
      "RemainingPrincipal": 9439.13,
      "PaymentDueDate": "2021-11-01"
    },
    {
      "Number": 17,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 63.71,
      "Interest": 77.58,
      "CumulativePrincipal": 996.16,
      "CumulativeInterest": 1405.77,
      "RemainingPrincipal": 9375.42,
      "PaymentDueDate": "2021-12-01"
    },
    {
      "Number": 18,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 61.66,
      "Interest": 79.63,
      "CumulativePrincipal": 1057.82,
      "CumulativeInterest": 1485.40,
      "RemainingPrincipal": 9313.76,
      "PaymentDueDate": "2022-01-01"
    },
    {
      "Number": 19,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 62.19,
      "Interest": 79.10,
      "CumulativePrincipal": 1120.01,
      "CumulativeInterest": 1564.50,
      "RemainingPrincipal": 9251.57,
      "PaymentDueDate": "2022-02-01"
    },
    {
      "Number": 20,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 70.32,
      "Interest": 70.97,
      "CumulativePrincipal": 1190.33,
      "CumulativeInterest": 1635.47,
      "RemainingPrincipal": 9181.25,
      "PaymentDueDate": "2022-03-01"
    },
    {
      "Number": 21,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 63.31,
      "Interest": 77.98,
      "CumulativePrincipal": 1253.64,
      "CumulativeInterest": 1713.45,
      "RemainingPrincipal": 9117.94,
      "PaymentDueDate": "2022-04-01"
    },
    {
      "Number": 22,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 66.35,
      "Interest": 74.94,
      "CumulativePrincipal": 1319.99,
      "CumulativeInterest": 1788.39,
      "RemainingPrincipal": 9051.59,
      "PaymentDueDate": "2022-05-01"
    },
    {
      "Number": 23,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 64.41,
      "Interest": 76.88,
      "CumulativePrincipal": 1384.40,
      "CumulativeInterest": 1865.27,
      "RemainingPrincipal": 8987.18,
      "PaymentDueDate": "2022-06-01"
    },
    {
      "Number": 24,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 67.42,
      "Interest": 73.87,
      "CumulativePrincipal": 1451.82,
      "CumulativeInterest": 1939.14,
      "RemainingPrincipal": 8919.76,
      "PaymentDueDate": "2022-07-01"
    },
    {
      "Number": 25,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 65.53,
      "Interest": 75.76,
      "CumulativePrincipal": 1517.35,
      "CumulativeInterest": 2014.90,
      "RemainingPrincipal": 8854.23,
      "PaymentDueDate": "2022-08-01"
    },
    {
      "Number": 26,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 66.09,
      "Interest": 75.20,
      "CumulativePrincipal": 1583.44,
      "CumulativeInterest": 2090.10,
      "RemainingPrincipal": 8788.14,
      "PaymentDueDate": "2022-09-01"
    },
    {
      "Number": 27,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 69.06,
      "Interest": 72.23,
      "CumulativePrincipal": 1652.50,
      "CumulativeInterest": 2162.33,
      "RemainingPrincipal": 8719.08,
      "PaymentDueDate": "2022-10-01"
    },
    {
      "Number": 28,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 67.24,
      "Interest": 74.05,
      "CumulativePrincipal": 1719.74,
      "CumulativeInterest": 2236.38,
      "RemainingPrincipal": 8651.84,
      "PaymentDueDate": "2022-11-01"
    },
    {
      "Number": 29,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 70.18,
      "Interest": 71.11,
      "CumulativePrincipal": 1789.92,
      "CumulativeInterest": 2307.49,
      "RemainingPrincipal": 8581.66,
      "PaymentDueDate": "2022-12-01"
    },
    {
      "Number": 30,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 68.40,
      "Interest": 72.89,
      "CumulativePrincipal": 1858.32,
      "CumulativeInterest": 2380.38,
      "RemainingPrincipal": 8513.26,
      "PaymentDueDate": "2023-01-01"
    },
    {
      "Number": 31,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 68.99,
      "Interest": 72.30,
      "CumulativePrincipal": 1927.31,
      "CumulativeInterest": 2452.68,
      "RemainingPrincipal": 8444.27,
      "PaymentDueDate": "2023-02-01"
    },
    {
      "Number": 32,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 76.51,
      "Interest": 64.78,
      "CumulativePrincipal": 2003.82,
      "CumulativeInterest": 2517.46,
      "RemainingPrincipal": 8367.76,
      "PaymentDueDate": "2023-03-01"
    },
    {
      "Number": 33,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 70.22,
      "Interest": 71.07,
      "CumulativePrincipal": 2074.04,
      "CumulativeInterest": 2588.53,
      "RemainingPrincipal": 8297.54,
      "PaymentDueDate": "2023-04-01"
    },
    {
      "Number": 34,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 73.09,
      "Interest": 68.20,
      "CumulativePrincipal": 2147.13,
      "CumulativeInterest": 2656.73,
      "RemainingPrincipal": 8224.45,
      "PaymentDueDate": "2023-05-01"
    },
    {
      "Number": 35,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 71.44,
      "Interest": 69.85,
      "CumulativePrincipal": 2218.57,
      "CumulativeInterest": 2726.58,
      "RemainingPrincipal": 8153.01,
      "PaymentDueDate": "2023-06-01"
    },
    {
      "Number": 36,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 74.28,
      "Interest": 67.01,
      "CumulativePrincipal": 2292.85,
      "CumulativeInterest": 2793.59,
      "RemainingPrincipal": 8078.73,
      "PaymentDueDate": "2023-07-01"
    },
    {
      "Number": 37,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 72.68,
      "Interest": 68.61,
      "CumulativePrincipal": 2365.53,
      "CumulativeInterest": 2862.20,
      "RemainingPrincipal": 8006.05,
      "PaymentDueDate": "2023-08-01"
    },
    {
      "Number": 38,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 73.29,
      "Interest": 68.00,
      "CumulativePrincipal": 2438.82,
      "CumulativeInterest": 2930.20,
      "RemainingPrincipal": 7932.76,
      "PaymentDueDate": "2023-09-01"
    },
    {
      "Number": 39,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 76.09,
      "Interest": 65.20,
      "CumulativePrincipal": 2514.91,
      "CumulativeInterest": 2995.40,
      "RemainingPrincipal": 7856.67,
      "PaymentDueDate": "2023-10-01"
    },
    {
      "Number": 40,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 74.56,
      "Interest": 66.73,
      "CumulativePrincipal": 2589.47,
      "CumulativeInterest": 3062.13,
      "RemainingPrincipal": 7782.11,
      "PaymentDueDate": "2023-11-01"
    },
    {
      "Number": 41,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 77.33,
      "Interest": 63.96,
      "CumulativePrincipal": 2666.80,
      "CumulativeInterest": 3126.09,
      "RemainingPrincipal": 7704.78,
      "PaymentDueDate": "2023-12-01"
    },
    {
      "Number": 42,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 75.85,
      "Interest": 65.44,
      "CumulativePrincipal": 2742.65,
      "CumulativeInterest": 3191.53,
      "RemainingPrincipal": 7628.93,
      "PaymentDueDate": "2024-01-01"
    },
    {
      "Number": 43,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 76.67,
      "Interest": 64.62,
      "CumulativePrincipal": 2819.32,
      "CumulativeInterest": 3256.15,
      "RemainingPrincipal": 7552.26,
      "PaymentDueDate": "2024-02-01"
    },
    {
      "Number": 44,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 81.45,
      "Interest": 59.84,
      "CumulativePrincipal": 2900.77,
      "CumulativeInterest": 3315.99,
      "RemainingPrincipal": 7470.81,
      "PaymentDueDate": "2024-03-01"
    },
    {
      "Number": 45,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 78.01,
      "Interest": 63.28,
      "CumulativePrincipal": 2978.78,
      "CumulativeInterest": 3379.27,
      "RemainingPrincipal": 7392.80,
      "PaymentDueDate": "2024-04-01"
    },
    {
      "Number": 46,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 80.69,
      "Interest": 60.60,
      "CumulativePrincipal": 3059.47,
      "CumulativeInterest": 3439.87,
      "RemainingPrincipal": 7312.11,
      "PaymentDueDate": "2024-05-01"
    },
    {
      "Number": 47,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 79.36,
      "Interest": 61.93,
      "CumulativePrincipal": 3138.83,
      "CumulativeInterest": 3501.80,
      "RemainingPrincipal": 7232.75,
      "PaymentDueDate": "2024-06-01"
    },
    {
      "Number": 48,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 82.01,
      "Interest": 59.28,
      "CumulativePrincipal": 3220.84,
      "CumulativeInterest": 3561.08,
      "RemainingPrincipal": 7150.74,
      "PaymentDueDate": "2024-07-01"
    },
    {
      "Number": 49,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 80.72,
      "Interest": 60.57,
      "CumulativePrincipal": 3301.56,
      "CumulativeInterest": 3621.65,
      "RemainingPrincipal": 7070.02,
      "PaymentDueDate": "2024-08-01"
    },
    {
      "Number": 50,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 81.41,
      "Interest": 59.88,
      "CumulativePrincipal": 3382.97,
      "CumulativeInterest": 3681.53,
      "RemainingPrincipal": 6988.61,
      "PaymentDueDate": "2024-09-01"
    },
    {
      "Number": 51,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 84.01,
      "Interest": 57.28,
      "CumulativePrincipal": 3466.98,
      "CumulativeInterest": 3738.81,
      "RemainingPrincipal": 6904.60,
      "PaymentDueDate": "2024-10-01"
    },
    {
      "Number": 52,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 82.81,
      "Interest": 58.48,
      "CumulativePrincipal": 3549.79,
      "CumulativeInterest": 3797.29,
      "RemainingPrincipal": 6821.79,
      "PaymentDueDate": "2024-11-01"
    },
    {
      "Number": 53,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 85.37,
      "Interest": 55.92,
      "CumulativePrincipal": 3635.16,
      "CumulativeInterest": 3853.21,
      "RemainingPrincipal": 6736.42,
      "PaymentDueDate": "2024-12-01"
    },
    {
      "Number": 54,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 84.23,
      "Interest": 57.06,
      "CumulativePrincipal": 3719.39,
      "CumulativeInterest": 3910.27,
      "RemainingPrincipal": 6652.19,
      "PaymentDueDate": "2025-01-01"
    },
    {
      "Number": 55,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 84.79,
      "Interest": 56.50,
      "CumulativePrincipal": 3804.18,
      "CumulativeInterest": 3966.77,
      "RemainingPrincipal": 6567.40,
      "PaymentDueDate": "2025-02-01"
    },
    {
      "Number": 56,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 90.91,
      "Interest": 50.38,
      "CumulativePrincipal": 3895.09,
      "CumulativeInterest": 4017.15,
      "RemainingPrincipal": 6476.49,
      "PaymentDueDate": "2025-03-01"
    },
    {
      "Number": 57,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 86.28,
      "Interest": 55.01,
      "CumulativePrincipal": 3981.37,
      "CumulativeInterest": 4072.16,
      "RemainingPrincipal": 6390.21,
      "PaymentDueDate": "2025-04-01"
    },
    {
      "Number": 58,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 88.77,
      "Interest": 52.52,
      "CumulativePrincipal": 4070.14,
      "CumulativeInterest": 4124.68,
      "RemainingPrincipal": 6301.44,
      "PaymentDueDate": "2025-05-01"
    },
    {
      "Number": 59,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 87.77,
      "Interest": 53.52,
      "CumulativePrincipal": 4157.91,
      "CumulativeInterest": 4178.20,
      "RemainingPrincipal": 6213.67,
      "PaymentDueDate": "2025-06-01"
    },
    {
      "Number": 60,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 90.22,
      "Interest": 51.07,
      "CumulativePrincipal": 4248.13,
      "CumulativeInterest": 4229.27,
      "RemainingPrincipal": 6123.45,
      "PaymentDueDate": "2025-07-01"
    },
    {
      "Number": 61,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 89.28,
      "Interest": 52.01,
      "CumulativePrincipal": 4337.41,
      "CumulativeInterest": 4281.28,
      "RemainingPrincipal": 6034.17,
      "PaymentDueDate": "2025-08-01"
    },
    {
      "Number": 62,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 90.04,
      "Interest": 51.25,
      "CumulativePrincipal": 4427.45,
      "CumulativeInterest": 4332.53,
      "RemainingPrincipal": 5944.13,
      "PaymentDueDate": "2025-09-01"
    },
    {
      "Number": 63,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 92.43,
      "Interest": 48.86,
      "CumulativePrincipal": 4519.88,
      "CumulativeInterest": 4381.39,
      "RemainingPrincipal": 5851.70,
      "PaymentDueDate": "2025-10-01"
    },
    {
      "Number": 64,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 91.59,
      "Interest": 49.70,
      "CumulativePrincipal": 4611.47,
      "CumulativeInterest": 4431.09,
      "RemainingPrincipal": 5760.11,
      "PaymentDueDate": "2025-11-01"
    },
    {
      "Number": 65,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 93.95,
      "Interest": 47.34,
      "CumulativePrincipal": 4705.42,
      "CumulativeInterest": 4478.43,
      "RemainingPrincipal": 5666.16,
      "PaymentDueDate": "2025-12-01"
    },
    {
      "Number": 66,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 93.17,
      "Interest": 48.12,
      "CumulativePrincipal": 4798.59,
      "CumulativeInterest": 4526.55,
      "RemainingPrincipal": 5572.99,
      "PaymentDueDate": "2026-01-01"
    },
    {
      "Number": 67,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 93.96,
      "Interest": 47.33,
      "CumulativePrincipal": 4892.55,
      "CumulativeInterest": 4573.88,
      "RemainingPrincipal": 5479.03,
      "PaymentDueDate": "2026-02-01"
    },
    {
      "Number": 68,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 99.26,
      "Interest": 42.03,
      "CumulativePrincipal": 4991.81,
      "CumulativeInterest": 4615.91,
      "RemainingPrincipal": 5379.77,
      "PaymentDueDate": "2026-03-01"
    },
    {
      "Number": 69,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 95.60,
      "Interest": 45.69,
      "CumulativePrincipal": 5087.41,
      "CumulativeInterest": 4661.60,
      "RemainingPrincipal": 5284.17,
      "PaymentDueDate": "2026-04-01"
    },
    {
      "Number": 70,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 97.86,
      "Interest": 43.43,
      "CumulativePrincipal": 5185.27,
      "CumulativeInterest": 4705.03,
      "RemainingPrincipal": 5186.31,
      "PaymentDueDate": "2026-05-01"
    },
    {
      "Number": 71,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 97.24,
      "Interest": 44.05,
      "CumulativePrincipal": 5282.51,
      "CumulativeInterest": 4749.08,
      "RemainingPrincipal": 5089.07,
      "PaymentDueDate": "2026-06-01"
    },
    {
      "Number": 72,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 99.46,
      "Interest": 41.83,
      "CumulativePrincipal": 5381.97,
      "CumulativeInterest": 4790.91,
      "RemainingPrincipal": 4989.61,
      "PaymentDueDate": "2026-07-01"
    },
    {
      "Number": 73,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 98.91,
      "Interest": 42.38,
      "CumulativePrincipal": 5480.88,
      "CumulativeInterest": 4833.29,
      "RemainingPrincipal": 4890.70,
      "PaymentDueDate": "2026-08-01"
    },
    {
      "Number": 74,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 99.75,
      "Interest": 41.54,
      "CumulativePrincipal": 5580.63,
      "CumulativeInterest": 4874.83,
      "RemainingPrincipal": 4790.95,
      "PaymentDueDate": "2026-09-01"
    },
    {
      "Number": 75,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 101.91,
      "Interest": 39.38,
      "CumulativePrincipal": 5682.54,
      "CumulativeInterest": 4914.21,
      "RemainingPrincipal": 4689.04,
      "PaymentDueDate": "2026-10-01"
    },
    {
      "Number": 76,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 101.47,
      "Interest": 39.82,
      "CumulativePrincipal": 5784.01,
      "CumulativeInterest": 4954.03,
      "RemainingPrincipal": 4587.57,
      "PaymentDueDate": "2026-11-01"
    },
    {
      "Number": 77,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 103.58,
      "Interest": 37.71,
      "CumulativePrincipal": 5887.59,
      "CumulativeInterest": 4991.74,
      "RemainingPrincipal": 4483.99,
      "PaymentDueDate": "2026-12-01"
    },
    {
      "Number": 78,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 103.21,
      "Interest": 38.08,
      "CumulativePrincipal": 5990.80,
      "CumulativeInterest": 5029.82,
      "RemainingPrincipal": 4380.78,
      "PaymentDueDate": "2027-01-01"
    },
    {
      "Number": 79,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 104.08,
      "Interest": 37.21,
      "CumulativePrincipal": 6094.88,
      "CumulativeInterest": 5067.03,
      "RemainingPrincipal": 4276.70,
      "PaymentDueDate": "2027-02-01"
    },
    {
      "Number": 80,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 108.48,
      "Interest": 32.81,
      "CumulativePrincipal": 6203.36,
      "CumulativeInterest": 5099.84,
      "RemainingPrincipal": 4168.22,
      "PaymentDueDate": "2027-03-01"
    },
    {
      "Number": 81,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 105.89,
      "Interest": 35.40,
      "CumulativePrincipal": 6309.25,
      "CumulativeInterest": 5135.24,
      "RemainingPrincipal": 4062.33,
      "PaymentDueDate": "2027-04-01"
    },
    {
      "Number": 82,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 107.90,
      "Interest": 33.39,
      "CumulativePrincipal": 6417.15,
      "CumulativeInterest": 5168.63,
      "RemainingPrincipal": 3954.43,
      "PaymentDueDate": "2027-05-01"
    },
    {
      "Number": 83,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 107.70,
      "Interest": 33.59,
      "CumulativePrincipal": 6524.85,
      "CumulativeInterest": 5202.22,
      "RemainingPrincipal": 3846.73,
      "PaymentDueDate": "2027-06-01"
    },
    {
      "Number": 84,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 109.67,
      "Interest": 31.62,
      "CumulativePrincipal": 6634.52,
      "CumulativeInterest": 5233.84,
      "RemainingPrincipal": 3737.06,
      "PaymentDueDate": "2027-07-01"
    },
    {
      "Number": 85,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 109.55,
      "Interest": 31.74,
      "CumulativePrincipal": 6744.07,
      "CumulativeInterest": 5265.58,
      "RemainingPrincipal": 3627.51,
      "PaymentDueDate": "2027-08-01"
    },
    {
      "Number": 86,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 110.48,
      "Interest": 30.81,
      "CumulativePrincipal": 6854.55,
      "CumulativeInterest": 5296.39,
      "RemainingPrincipal": 3517.03,
      "PaymentDueDate": "2027-09-01"
    },
    {
      "Number": 87,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 112.38,
      "Interest": 28.91,
      "CumulativePrincipal": 6966.93,
      "CumulativeInterest": 5325.30,
      "RemainingPrincipal": 3404.65,
      "PaymentDueDate": "2027-10-01"
    },
    {
      "Number": 88,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 112.37,
      "Interest": 28.92,
      "CumulativePrincipal": 7079.30,
      "CumulativeInterest": 5354.22,
      "RemainingPrincipal": 3292.28,
      "PaymentDueDate": "2027-11-01"
    },
    {
      "Number": 89,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 114.23,
      "Interest": 27.06,
      "CumulativePrincipal": 7193.53,
      "CumulativeInterest": 5381.28,
      "RemainingPrincipal": 3178.05,
      "PaymentDueDate": "2027-12-01"
    },
    {
      "Number": 90,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 114.30,
      "Interest": 26.99,
      "CumulativePrincipal": 7307.83,
      "CumulativeInterest": 5408.27,
      "RemainingPrincipal": 3063.75,
      "PaymentDueDate": "2028-01-01"
    },
    {
      "Number": 91,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 115.34,
      "Interest": 25.95,
      "CumulativePrincipal": 7423.17,
      "CumulativeInterest": 5434.22,
      "RemainingPrincipal": 2948.41,
      "PaymentDueDate": "2028-02-01"
    },
    {
      "Number": 92,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 117.93,
      "Interest": 23.36,
      "CumulativePrincipal": 7541.10,
      "CumulativeInterest": 5457.58,
      "RemainingPrincipal": 2830.48,
      "PaymentDueDate": "2028-03-01"
    },
    {
      "Number": 93,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 117.32,
      "Interest": 23.97,
      "CumulativePrincipal": 7658.42,
      "CumulativeInterest": 5481.55,
      "RemainingPrincipal": 2713.16,
      "PaymentDueDate": "2028-04-01"
    },
    {
      "Number": 94,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 119.05,
      "Interest": 22.24,
      "CumulativePrincipal": 7777.47,
      "CumulativeInterest": 5503.79,
      "RemainingPrincipal": 2594.11,
      "PaymentDueDate": "2028-05-01"
    },
    {
      "Number": 95,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 119.32,
      "Interest": 21.97,
      "CumulativePrincipal": 7896.79,
      "CumulativeInterest": 5525.76,
      "RemainingPrincipal": 2474.79,
      "PaymentDueDate": "2028-06-01"
    },
    {
      "Number": 96,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 121.00,
      "Interest": 20.29,
      "CumulativePrincipal": 8017.79,
      "CumulativeInterest": 5546.05,
      "RemainingPrincipal": 2353.79,
      "PaymentDueDate": "2028-07-01"
    },
    {
      "Number": 97,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 121.35,
      "Interest": 19.94,
      "CumulativePrincipal": 8139.14,
      "CumulativeInterest": 5565.99,
      "RemainingPrincipal": 2232.44,
      "PaymentDueDate": "2028-08-01"
    },
    {
      "Number": 98,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 122.38,
      "Interest": 18.91,
      "CumulativePrincipal": 8261.52,
      "CumulativeInterest": 5584.90,
      "RemainingPrincipal": 2110.06,
      "PaymentDueDate": "2028-09-01"
    },
    {
      "Number": 99,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 123.99,
      "Interest": 17.30,
      "CumulativePrincipal": 8385.51,
      "CumulativeInterest": 5602.20,
      "RemainingPrincipal": 1986.07,
      "PaymentDueDate": "2028-10-01"
    },
    {
      "Number": 100,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 124.47,
      "Interest": 16.82,
      "CumulativePrincipal": 8509.98,
      "CumulativeInterest": 5619.02,
      "RemainingPrincipal": 1861.60,
      "PaymentDueDate": "2028-11-01"
    },
    {
      "Number": 101,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 126.03,
      "Interest": 15.26,
      "CumulativePrincipal": 8636.01,
      "CumulativeInterest": 5634.28,
      "RemainingPrincipal": 1735.57,
      "PaymentDueDate": "2028-12-01"
    },
    {
      "Number": 102,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 126.59,
      "Interest": 14.70,
      "CumulativePrincipal": 8762.60,
      "CumulativeInterest": 5648.98,
      "RemainingPrincipal": 1608.98,
      "PaymentDueDate": "2029-01-01"
    },
    {
      "Number": 103,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 127.62,
      "Interest": 13.67,
      "CumulativePrincipal": 8890.22,
      "CumulativeInterest": 5662.65,
      "RemainingPrincipal": 1481.36,
      "PaymentDueDate": "2029-02-01"
    },
    {
      "Number": 104,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 129.93,
      "Interest": 11.36,
      "CumulativePrincipal": 9020.15,
      "CumulativeInterest": 5674.01,
      "RemainingPrincipal": 1351.43,
      "PaymentDueDate": "2029-03-01"
    },
    {
      "Number": 105,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 129.81,
      "Interest": 11.48,
      "CumulativePrincipal": 9149.96,
      "CumulativeInterest": 5685.49,
      "RemainingPrincipal": 1221.62,
      "PaymentDueDate": "2029-04-01"
    },
    {
      "Number": 106,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 131.25,
      "Interest": 10.04,
      "CumulativePrincipal": 9281.21,
      "CumulativeInterest": 5695.53,
      "RemainingPrincipal": 1090.37,
      "PaymentDueDate": "2029-05-01"
    },
    {
      "Number": 107,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 132.03,
      "Interest": 9.26,
      "CumulativePrincipal": 9413.24,
      "CumulativeInterest": 5704.79,
      "RemainingPrincipal": 958.34,
      "PaymentDueDate": "2029-06-01"
    },
    {
      "Number": 108,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 133.41,
      "Interest": 7.88,
      "CumulativePrincipal": 9546.65,
      "CumulativeInterest": 5712.67,
      "RemainingPrincipal": 824.93,
      "PaymentDueDate": "2029-07-01"
    },
    {
      "Number": 109,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 134.28,
      "Interest": 7.01,
      "CumulativePrincipal": 9680.93,
      "CumulativeInterest": 5719.68,
      "RemainingPrincipal": 690.65,
      "PaymentDueDate": "2029-08-01"
    },
    {
      "Number": 110,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 135.42,
      "Interest": 5.87,
      "CumulativePrincipal": 9816.35,
      "CumulativeInterest": 5725.55,
      "RemainingPrincipal": 555.23,
      "PaymentDueDate": "2029-09-01"
    },
    {
      "Number": 111,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 136.73,
      "Interest": 4.56,
      "CumulativePrincipal": 9953.08,
      "CumulativeInterest": 5730.11,
      "RemainingPrincipal": 418.50,
      "PaymentDueDate": "2029-10-01"
    },
    {
      "Number": 112,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 137.74,
      "Interest": 3.55,
      "CumulativePrincipal": 10090.82,
      "CumulativeInterest": 5733.66,
      "RemainingPrincipal": 280.76,
      "PaymentDueDate": "2029-11-01"
    },
    {
      "Number": 113,
      "ScheduleNumber": 1,
      "PaymentAmount": 141.29,
      "Principal": 138.98,
      "Interest": 2.31,
      "CumulativePrincipal": 10229.80,
      "CumulativeInterest": 5735.97,
      "RemainingPrincipal": 141.78,
      "PaymentDueDate": "2029-12-01"
    },
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
Term | yes | integer($int32) | the length of the loan based on the Term Frequency
TermFrequency | yes | string(enum) | the unit of measurement for Term of the loan. Options: *bi-weekly*, *monthly*, *quarterly*, *weekly*
Disbursements | yes | object | one or more disbursements
Disbursements.DisbursementDetails | yes | object | Information about disbursements.
Disbursements.DisbursementDetails.Principal | yes | number($double) | the disbursement amount
Disbursements.DisbursementDetails.DisbursementDate | yes | string($date-time) | The date that the disbursement occurs.
Disbursements.DisbursementDetails.Fees | no | number($double) | An optional origination fee amount.
Disbursements.DisbursementDetails.FeeType | no | string(enum) | the optional origination fee type (i.e., whether deducted from or capped onto disbursement). Options: *default*, *capped*, *repayment*, *deducted*
Periods | yes | object | one or more periods (i.e., a deferred or interest-only period and then a principal and interest period)
Periods.PeriodDetails | yes | object | Information about the loan periods.
Periods.PeriodDetails.StartDate | yes | string($date-time) | the start date for this period
Periods.PeriodDetails.PaymentType | yes | string(enum) | the type of payment required during this period (or none) Options: *none*, *interestonly*, *principalinterest*
Periods.PeriodDetails.InterestRate | yes | number ($double) | the interest rate charged during this period
Periods.PeriodDetails.InterestMethod | yes | string(enum) | the accrual method used to accrue interest during this period Options: *actual/actual*, *30/360*, *actual/365*, *actual/365.25*
Periods.PeriodDetails.PaymentFrequency | no | string(enum) | the frequency of payments during this period Options: *bi-weekly*, *monthly*, *quarterly*, *weekly*
Periods.PeriodDetails.ReduceTerm | no | boolean | whether this period reduces the term of the loan
Periods.PeriodDetails.FirstPaymentDate | no | string($date-time) | the date the first payment is due for this period (if payments are required)
Periods.PeriodDetails.CapAtBegin | no | boolean | whether interest should be capped onto the principal at the start of this period
Periods.PeriodDetails.FeeAmount | no | number($double) | any optional fee amount assessed when this period begins
Periods.PeriodDetails.FeeType | no | string(enum) | the type for any optional fee assessed when this period begin Options: *percentage*, *amount*
Periods.PeriodDetails.FeeBasedOn | no | string(enum) | the basis for any optional fee assessed when this period begin (when fee type is percentage) Options: *principalinterest*, *currentcpb*
Periods.PeriodDetails.FixedPaymentAmount | no | number($double) | whether this period requires a fixed payment amount to be paid
Periods.PeriodDetails.MinimumPaymentAmount | no | number($double) | the optional minimum payment amount required during this period (if payments are required)
OutstandingInterest | no | number($double) | optional amount of outstanding unpaid interest (for a loan being re-amortized)

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------

