# Energy-Analytics-System
The Smart Energy Analytics Platform is designed to monitor, analyze and optimize energy consumption in real-time for residential and commercial environments. This PowerBI report provides actionable insights to help users reduce energy waste, improve efficiency and make data-driven decisions.

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
This project is structured into three dashboards, each targeting a different decision-making layer:
<ol>
    <li>Executive Revenue Overview - This dashboard provides a high-level financial and performance summary for leadership and strategic decision-makers.</li>
    <li>Operational & Billing Analytics - This dashboard focuses on billing efficiency, payment performance, and operational health.</li>
    <li>Customer Intelligence- This dashboard provides customer-level performance insights and segmentation.</li>
</ol>

## Preview
Below is the preview of the PowerBI report.
1. Executive Revenue Overview </br>
![Dashboard 1](https://github.com/user-attachments/assets/2959fc23-5359-4b92-90fc-b3d2575c67ab) 
2. Operational & Billing Analytics </br>
![Dashboard 2](https://github.com/user-attachments/assets/4eb0ccab-7e84-439b-a6c6-71704711f748) 
3. Customer Intelligence </br>
![Dashboard 3](https://github.com/user-attachments/assets/eecd76aa-e38c-47f2-a3be-2d87657b5119)









