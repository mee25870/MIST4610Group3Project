# MIST4610 Group 3 Project
## Team Name
Sp26_61608_Group 3
## Team Members
1. Madeleine Ebert [@mee25870](https://github.com/mee25870)
2. Israel Erewa-Meggison [@israelmeggison](https://github.com/israelmeggison)
3. Cole Hauser	[@colehauser2005](https://github.com/colehauser2005)
4. Trey Hill [@treyhill277](https://github.com/treyhill277)
5. Ciara Trinh 
6. Joshua Welch
## Problem Description
## Data Model
<img width="1619" height="925" alt="Screenshot 2026-04-01 160752" src="https://github.com/user-attachments/assets/e341135b-4edc-42a6-8d45-2ddb12242410" />

## Data Dictionary

Drones

| COLUMN | DATA TYPE | ROLE |
|--------|----------|------|
| drone_id | VARCHAR(35) | PK |
| model | VARCHAR(35) |  |
| status | VARCHAR(11) |  |
| total_flight_hours | DECIMAL(7,2) |  |
| max_payload_weight | INT |  |
| current_battery_level | INT |  |

Routes

| COLUMN | DATA TYPE | ROLE |
|--------|----------|------|
| route_id | VARCHAR(35) | PK |
| origin_location | VARCHAR(45) |  |
| destination_location | VARCHAR(45) |  |
| distance_km | DECIMAL(10,2) |  |
| estimated_duration | VARCHAR(45) |  |

Packages

| COLUMN | DATA TYPE | ROLE |
|--------|----------|------|
| package_id | VARCHAR(45) | PK |
| customer_id | VARCHAR(35) | FK |
| delivery_id | VARCHAR(45) | FK |
| weight | DECIMAL(5,2) |  |
| dimensions | VARCHAR(45) |  |
| package_status | VARCHAR(15) |  |

Customers

| COLUMN | DATA TYPE | ROLE |
|--------|----------|------|
| customer_id | VARCHAR(35) | PK |
| name | VARCHAR(45) |  |
| phone | VARCHAR(45) |  |
| email | VARCHAR(45) |  |
| delivery_address | VARCHAR(45) |  |

Deliveries

| COLUMN | DATA TYPE | ROLE |
|--------|----------|------|
| delivery_id | VARCHAR(45) | PK |
| drone_id | VARCHAR(35) | FK |
| route_id | VARCHAR(35) | FK |
| customer_id | VARCHAR(35) | FK |
| start_time | DATETIME |  |
| end_time | DATETIME |  |
| delivery_status | VARCHAR(25) |  |

Flight_Logs

| COLUMN | DATA TYPE | ROLE |
|--------|----------|------|
| flight_log_id | VARCHAR(45) | PK |
| drone_id | VARCHAR(35) | FK |
| route_id | VARCHAR(35) | FK |
| flight_start_time | DATETIME |  |
| flight_end_time | DATETIME |  |
| flight_duration_hours | DECIMAL(6,2) |  |

Maintenance_Logs

| COLUMN | DATA TYPE | ROLE |
|--------|----------|------|
| maintenance_log_id | VARCHAR(45) | PK |
| drone_id | VARCHAR(35) | FK |
| lead_technician_id | VARCHAR(35) | FK |
| maintenance_date | DATETIME |  |
| maintenance_type | VARCHAR(45) |  |
| description | VARCHAR(99) |  |
| total_flight_hours_at_service | DECIMAL(5,2) |  |

Technicians

| COLUMN | DATA TYPE | ROLE |
|--------|----------|------|
| technician_id | VARCHAR(35) | PK |
| name | VARCHAR(35) |  |
| specialization | VARCHAR(45) |  |
| phone | VARCHAR(45) |  |
| email | VARCHAR(45) |  |

Maintenance_Parts

| COLUMN | DATA TYPE | ROLE |
|--------|----------|------|
| part_id | VARCHAR(45) | PK |
| maintenance_log_id | VARCHAR(45) | FK |
| part_name | VARCHAR(45) |  |
| quantity | INT |  |
| cost | DECIMAL(8,2) |  |

Charging_Stations

| COLUMN | DATA TYPE | ROLE |
|--------|----------|------|
| station_id | VARCHAR(35) | PK |
| location | VARCHAR(45) |  |
| station_status | VARCHAR(45) |  |

Battery_Usage

| COLUMN | DATA TYPE | ROLE |
|--------|----------|------|
| battery_usage_current | DECIMAL(4,2) | PK |
| drone_id | VARCHAR(35) | FK |
| station_id | VARCHAR(35) | FK |
| charge_start_time | DATETIME |  |
| charge_end_time | DATETIME |  |
| battery_level_before | INT |  |
| battery_level_after | INT |  |

## Query
1. Query 1.
2. Query 2.
3. Query 3.
4. Query 4.
5. Query 5.
6. Query 6.
7. Query 7.
8. Query 8.
   <img width="1852" height="786" alt="Screenshot 2026-04-01 155233" src="https://github.com/user-attachments/assets/14bfdc81-9035-4fde-ac50-7de1dc905bd7" />
   
10. Query 9.
    <img width="1256" height="658" alt="Screenshot 2026-04-01 155644" src="https://github.com/user-attachments/assets/df02b65c-8f47-43d4-95af-e272e4ab14a7" />
    
12. Query 10.
    <img width="1846" height="798" alt="Screenshot 2026-04-01 155733" src="https://github.com/user-attachments/assets/219a1279-4999-466b-9e6c-05ac315d07da" />

## Database Information
Name of the database: ns_Sp_61608_Group3

Additional information: Each query listed above is marked in the database using stored procedures which can be called using the following format: CALL TP_Q1();
