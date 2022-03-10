<!--Endpoint introduction -->
## Calculate Compound Interest

### POST calculators/interest/compound

<!-- RIGHT: code samples -->

> Sample request:

```shell
```

```csharp
```

``` javascript
```

```python
```
> JSON returned:

```json
```

<!-- LEFT: documentation -->

**Calculates compound interest accrued between specified dates.**

Use this endpoint to calculate compound interest accrual.

### HTTP Request

`POST https://api.nelnet.io/calculatorapi/interest/compound`

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
CompoundFrequency | yes | string (enum) | The frequency at which interest is compounded. Options are *daily*.

### HTTP Response
Field Name | Type | Description
---- | ---- | -------
amount | double | The dollar-amount value of the interest accrued over the period of time included in the request.
newPrincipalBalance | number | The principal balance after accrual.
