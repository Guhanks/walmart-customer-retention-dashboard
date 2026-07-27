# Key DAX Measures

```dax
Churn Rate =
DIVIDE(
    CALCULATE(COUNTROWS(dim_Churn), dim_Churn[Churn_Flag] = 1),
    COUNTROWS(dim_Churn)
)

Total Customers = DISTINCTCOUNT(dim_Demographics[Customer_ID])

Avg Transaction Amount = AVERAGE(fact_Transactions[Amount])

Promotion Lift =
VAR AvgWithPromo =
    CALCULATE(AVERAGE(fact_Transactions[Amount]), fact_Transactions[Promotion_Applied] = "Yes")
VAR AvgWithoutPromo =
    CALCULATE(AVERAGE(fact_Transactions[Amount]), fact_Transactions[Promotion_Applied] = "No")
RETURN AvgWithPromo - AvgWithoutPromo

Redemption Rate =
DIVIDE(SUM(dim_Loyalty[Points_Redeemed]), SUM(dim_Loyalty[Points_Earned]))

Churn Rate by Tier =
CALCULATE(
    [Churn Rate],
    ALLEXCEPT(dim_Loyalty, dim_Loyalty[Loyalty_Tier])
)
```

## Notes
- All churn-related measures key off `dim_Churn[Churn_Flag]`, joined 1:1 to `dim_Demographics` on `Customer_ID`.
- `Promotion Lift` was the measure that surfaced the near-zero difference ($516 vs $516) between promoted and non-promoted transactions.
- Region- and tier-level breakdowns reuse `[Churn Rate]` with `ALLEXCEPT` / slicer context rather than separate hardcoded measures, keeping the model DRY.
