***Key Takeaways***:

**DAX** 

1. Use +0 at the end of a DAX measure to convert blank values to 0.
→ This helps remove blank dimensions automatically in visuals.

⚠️ Do not use this in the measure is added in detail-level tables:
→ It can cause serious performance issues.
→ The visual may fail to load and time out.

✅ Recommended only in summary-level visuals (e.g., cards, charts, aggregated tables).

Example:
```
Trend Past Due E&O lines = 
CALCULATE(
    SUM(ExcessAndObsolete[Line Items]),
    ExcessAndObsolete[IsActionDatePast] = 1
) + 0
```
![image](https://github.com/user-attachments/assets/2b623ef3-497d-45b4-ac86-72903eaccb9c)

2. To avoid displaying customers not related to a specific plant, we can add a measure-based filter.

→ Customers come from vw_ProfitCenterHierarchy

→ Plants come from vw_PlantHierarchy

→ Line items are stored in ExcessAndObsolete

When developing the report, if we want to retain customers with 0 line items (but only if they are actually related to the selected plant), we should apply a measure like the one below to filter out unrelated combinations:

```
Valid Customer by Plant =
IF (
    CALCULATE (
        COUNTROWS (ExcessAndObsolete),
        ALLEXCEPT(ExcessAndObsolete, ExcessAndObsolete[Customer], ExcessAndObsolete[Plant])
    ) > 0,
    1,
    0
)
```
Then use this measure as a visual-level filter:
Show items when ‘Valid Customer by Plant’ = 1
   

![image](https://github.com/user-attachments/assets/8fe1e9b1-ea67-4afe-b401-124acfb53d4c)

3. add value to sort based on the last columns in metric table
```
Sorted Trend E&O Execution% Value = 
 IF(
    ISINSCOPE(ExcessAndObsolete[Snapshot Date]),
    [Trend E&O RC Execution Value %],
    CALCULATE([Trend E&O RC Execution Value %],ExcessAndObsolete[Snapshot Date]=max(ExcessAndObsolete[Snapshot Date])
    )
    )
```
**Functionality**

**Filter**

1.To avoid show filter elements which don't have any data under it，Add **filtering measures** in right side filters

2.Using Button filter to interact between above KPI cards and bottom table
