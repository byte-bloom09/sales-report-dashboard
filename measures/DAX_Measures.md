# 📐 DAX Measures – Sales Report Dashboard

This file documents key DAX measures used in the Superstore Revenue Analysis dashboard.

---
## Margin Calculations
```
DAX tech margin = 
CALCULATE(
    DIVIDE(SUM('Sample - Superstore'[Profit]), SUM('Sample - Superstore'[Sales])),
    'Sample - Superstore'[Category] = "Technology"
)
Furniture Margin = 
CALCULATE(
    DIVIDE(SUM('Sample - Superstore'[Profit]), SUM('Sample - Superstore'[Sales])),
    'Sample - Superstore'[Category] = "Furniture"
)
office Margin = 
CALCULATE(
    DIVIDE(SUM('Sample - Superstore'[Profit]), SUM('Sample - Superstore'[Sales])),
    'Sample - Superstore'[Category] = "Office Supplies"
)
```
## Top region calculation
```
Top Region = 
VAR TopRegionTable = 
    TOPN(
        1, 
        SUMMARIZE(
            'Sample - Superstore', 
            'Sample - Superstore'[Region],  -- Correct grouping column
            "TotalSales", SUM('Sample - Superstore'[Sales])
        ), 
        [TotalSales], 
        DESC
    )
RETURN
    SELECTCOLUMNS(TopRegionTable, "Region", 'Sample - Superstore'[Region])

```






