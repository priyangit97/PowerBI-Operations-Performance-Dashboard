1. Total Tasks
Total_Tasks =
SUM ( Operations_Data[Tasks_Handled] )
Purpose: Calculates total tasks handled based on filter context.


2. Total Errors
Total_Errors =
SUM ( Operations_Data[Errors] )
Purpose: Aggregates total errors across shifts and employees.

3. Error Rate %
Error_Rate_Percent =
DIVIDE ( [Total_Errors], [Total_Tasks], 0 ) * 100
Purpose: Calculates error percentage safely using DIVIDE to avoid divide-by-zero errors.

4. Productivity Rate
Productivity_Rate =
DIVIDE (
    [Total_Tasks],
    DISTINCTCOUNT ( Operations_Data[Date] ),
    0
)
Purpose: Measures average productivity per day

5. Attendance %
Attendance_Percent =
DIVIDE (
    CALCULATE (
        COUNTROWS ( Operations_Data ),
        Operations_Data[Attendance] = "Present"
    ),
    COUNTROWS ( Operations_Data ),
    0
) * 100
Purpose: Calculates attendance rate across selected filters.

6. Rework Rate %
Rework_Rate_Percent =
DIVIDE ( [Total_Rework], [Total_Tasks], 0 ) * 100
Purpose: Measures rework impact on productivity.

