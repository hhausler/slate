# Calculators

The Calculators service maintains all the algorithms regarding loan financials, including interest accruals. It calculates payment schedules based on a loan’s principal, rate, and term. Our calculators support actual/actual, 30/360, actual/365, and actual/365.25 interest accrual calculation methods. 

Use the `amortization` endpoint to create amortization schedules for immediate-repayment loans based on a loan's principal, rate and term. You can calculate a basic amortization schedule, a fixed-payment amortization schedule or a custom amortization schedule.

Use the `interest` endpoint to calculate interest accrued between specified dates.
