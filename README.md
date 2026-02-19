# Energy-Analytics-System
The Smart Energy Analytics Platform is designed to monitor, analyze and optimize energy consumption in real-time for residential and commercial environments. This PowerBI report provides actionable insights to help users reduce energy waste, improve efficiency and make data-driven decisions.

## Conceptual Data Model
Given below is a Conceptual Data Model representing the core entities and relationships. </br>
![Conceptual Data Model](https://github.com/user-attachments/assets/1ce1e9f0-cac3-4abc-8e2c-02b5aeb120f5)

## Logical and Physical Data Modelling
The model is normalised up to the 3rd Normal Form (3NF) to avoid redundancy, ensure data integrity, and prepare for efficient storage. 

### Schema Design
<ol>
    <li>Customer(customer_id)</li>
    <li>Meter(meter_id)</li>
    <li> Tariff(tariff_id)</li>
    <li>Billing(billing_id)</li>
    <li>Consumption(consumption_id)</li>
    <li>Location(location_id)</li>
    <li>Allocation(allocation_id)</li>
</ol>
</br>

The ER Diagram includes the entities with their attributes and the relationships between them. </br>
![ER_Diagram](https://github.com/user-attachments/assets/fc3dda74-fdaa-4986-963f-1a74517cd27e)</br>

Datasets were simulated using Python.

## PowerBI report
Designed a normalized snowflake schema initially for structured data storage, then refactored the model into a star schema to optimize analytical performance and simplify BI reporting in Power BI. </br>
This project is structured into three dashboards, each targeting a different decision-making layer,
<ol>
    <li>Executive Revenue Overview - This dashboard provides a high-level financial and performance summary for leadership and strategic decision-makers.</li>
    <li>Operational & Billing Analytics - This dashboard focuses on billing efficiency, payment performance, and operational health.</li>
    <li>Customer Intelligence- This dashboard provides customer-level performance insights and segmentation.</li>
</ol>

## Key DAX Measures and Calculated Columns
The following DAX measures power the analytical layer of the dashboard. They were developed to calculate core KPIs, enable time-based comparisons and support interactive filtering across customers, regions and billing status. </br>

1. Core Aggregation Measures
    * Total Energy (kWh)
    ```dax
    Total Energy (kWh) = SUM(Fact_Consumption[consumption_kwh])
    ```
    * Total Revenue
    ```dax
    Total Revenue = SUMX(
    Fact_Billing,
    Fact_Billing[total_kwh] *
    RELATED(Dim_Tariff[rate_per_kwh]))
    ```
    * Revenue per kWh
    ```dax
    Revenue per kWh = DIVIDE([Total Revenue], [Total Energy (kWh)])
    ```
    </br>
2. Customer & Billing KPIs
    * Active Meters
    ```dax
    Active Meters = DISTINCTCOUNT(Dim_Meter[meter_id])
    ```
    * Total Bills
    ```dax
    Total Bills = COUNT(Fact_Billing[billing_id])
    ```
    * Total Customers
    ```dax
    Total Customers = DISTINCTCOUNT(Dim_Customer[customer_id])
    ```
    * Completed Bills
    ```dax
    Completed Bills =
    CALCULATE(
    COUNT(Fact_Billing[billing_id]),
    Fact_Billing[billing_status] = "Paid")
    ```
    * Billing Completion %
    ```dax
    Billing Completion % =
    DIVIDE(
    [Completed Bills],
    [Total Bills])
    ```
    </br>
3. Time Intelligence Measures
    * Monthly Revenue
    ```dax
    Monthly Revenue = [Total Revenue]
    ```
    * Previous Month Revenue
    ```dax
    Previous Month Revenue =
    CALCULATE(
    [Total Revenue],
    DATEADD(Date_Table[Date], -1, MONTH))
    ```
    * Revenue MoM %
    ```dax
    Revenue MoM % =
    DIVIDE(
    [Total Revenue] - [Previous Month Revenue],
    [Previous Month Revenue])
    ```
    </br>
4. Average Metrics
    * Avg Energy per Bill
    ```dax
    Avg Energy per Bill =
    DIVIDE(
    [Total Energy (kWh)],
    [Total Bills])
    ```
    * Avg Energy per Customer
    ```dax
    Avg Energy per Customer =
    DIVIDE(
    [Total Energy (kWh)],
    DISTINCTCOUNT(Dim_Customer[customer_id]))
    ```
    * Avg Revenue per Customer
    ```dax
    Avg Revenue per Customer =
    DIVIDE(
    [Total Revenue],
    DISTINCTCOUNT(Dim_Customer[customer_id]))
    ```
    </br>
5. Customer Segmentation
    * Customer Total Energy
    ```dax
    Customer Total Energy =
    CALCULATE(
    SUM(Fact_Consumption[consumption_kwh]))
    ```
    * Usage Segment
    ```dax
    Usage Segment =
    SWITCH(
    TRUE(),
    [Customer Total Energy] < 2000, "Low Usage",
    [Customer Total Energy] < 6000, "Medium Usage",
    "High Usage")
    ```
    </br>
6. Calculated Column
    * YearMonthSort
    ```dax
    YearMonthSort = YEAR('date_table'[Date]) * 100 + MONTH('date_table'[Date])
    ```
    
## Preview
Below is the preview of the PowerBI report. </br>
1. Executive Revenue Overview </br>
![Dashboard 1](https://github.com/user-attachments/assets/2959fc23-5359-4b92-90fc-b3d2575c67ab) </br>
2. Operational & Billing Analytics </br>
![Dashboard 2](https://github.com/user-attachments/assets/4eb0ccab-7e84-439b-a6c6-71704711f748) </br>
3. Customer Intelligence </br>
![Dashboard 3](https://github.com/user-attachments/assets/eecd76aa-e38c-47f2-a3be-2d87657b5119) 









