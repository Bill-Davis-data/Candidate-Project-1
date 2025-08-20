# All Orders append
```
MEASURE 'All Orders append'[Count of SO Number by Status] = 
VAR SelectedStatus = SELECTEDVALUE('StatusFilter'[SO Status])
RETURN
CALCULATE(
    COUNT('All Orders append'[SO Number]),
    'All Orders append'[SO Status] = SelectedStatus
)
MEASURE 'All Orders append'[IsUnderperforming] = 
VAR DistQty =
    CALCULATE(SUM('All Orders append'[SOD Qty]))
VAR Threshold =
    CALCULATE(
        PERCENTILEX.INC(
            VALUES('All Orders append'[Distributor]),
            CALCULATE(SUM('All Orders append'[SOD Qty])),
            'Dashboard Target'[Underperforming Threshold]
        ),
        REMOVEFILTERS('All Orders append'[Distributor])
    )
RETURN
    IF(NOT ISBLANK(DistQty) && DistQty <= Threshold, 1, 0)

MEASURE 'All Orders append'[Percent of Status by Year] = 
DIVIDE(
    COUNT('All Orders append'[SO Number]),
    CALCULATE(
        COUNT('All Orders append'[SO Number]),
        REMOVEFILTERS('All Orders append'[SO Status])
    )
)

MEASURE 'All Orders append'[Percent Total SO Number by Status] = 
DIVIDE(
    [Count of SO Number by Status],
    COUNT('All Orders append'[SO Number])
)
MEASURE 'All Orders append'[Void Reason Count] = 
CALCULATE(
    COUNTROWS('All Orders append'),
    USERELATIONSHIP('All Orders append'[SOV Voided Date], 'DateTable'[Date])
)
MEASURE 'All Orders append'[Void Reason Rank by Year] = 
RANKX(
    ALLSELECTED('All Orders append'[SOV Void Reason]),
    CALCULATE(
        COUNTROWS('All Orders append'),
        USERELATIONSHIP('All Orders append'[SOV Voided Date], 'DateTable'[Date])
    ),
    ,
    DESC,
    DENSE
)
```
