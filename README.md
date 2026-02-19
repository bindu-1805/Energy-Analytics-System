# Energy-Analytics-System
The Smart Energy Analytics Platform is designed to monitor, analyze and optimize energy consumption in real-time for residential and commercial environments. This PowerBI report provides actionable insights to help users reduce energy waste, improve efficiency and make data-driven decisions.

## Entities and relationships
Given below is a Conceptual Data Model representing the core entities and relationships.
![Conceptual Data Model]("C:\Users\Bindu Madhavi V\OneDrive\Desktop\Cognizant\TechAcademy\GCP\Sprint 1\SPRINT SUBMISSION\Conceptual_Data_Model.png")

## Logical and Physical Data Modelling
The model is normalised up to the 3rd Normal Form (3NF) to avoid redundancy, ensure data integrity, and prepare for efficient storage. 

### Schema Design
Tables and keys:
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

The ER Diagram includes the entities with their attributes and the relationship between them.
![ERD]("C:\Users\Bindu Madhavi V\OneDrive\Desktop\Cognizant\TechAcademy\GCP\Sprint 1\SPRINT SUBMISSION\ER_Diagram.jpg")

> Datasets were simulater using Python.

## PowerBI report
This project is structured into three dashboards, each targeting a different decision-making layer:
<ol>
    <li>Executive Revenue Overview - This dashboard provides a high-level financial and performance summary for leadership and strategic decision-makers.</li>
    <li>Operational & Billing Analytics - This dashboard focuses on billing efficiency, payment performance, and operational health.</li>
    <li>Customer Intelligence - This dashboard provides customer-level performance insights and segmentation.</li>
</ol>






