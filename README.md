# MIST4610 Group 3 Project
## Team Name
Sp26_61608_Group 3
## Team Members
1. Madeleine Ebert [@mee25870](https://github.com/mee25870)
2. Israel Erewa-Meggison [@israelmeggison](https://github.com/israelmeggison)
3. Cole Hauser	[@colehauser2005](https://github.com/colehauser2005)
4. Trey Hill [@treyhill277](https://github.com/treyhill277)
5. Ciara Trinh 
6. Joshua Welch [@jew22145](https://github.com/jew22145)
## Problem Description
We are "Last Mile" Drone Logistics, a drone delivery company that specializes in transporting packages via drone to consumers living in urban areas. Our business model requires us to constantly keep track of things such as customer orders, delivery status, and drone status in order to keep our business running without hiccups and keep consumers satisfied with their deliveries. Our Data Model logs info such as Customers, Packages, Deliveries, Technicians, and Drone health information, all for the purpose of keeping track of (and retrieving specific query info from) the multiple interconnected components within our database. As a result, having a data model will save us time, money, and resources in the long run and keep our company operating efficiently.
## Data Model
<img width="1619" height="925" alt="Screenshot 2026-04-01 160752" src="https://github.com/user-attachments/assets/e341135b-4edc-42a6-8d45-2ddb12242410" />

### Explanation:
A Customer can have many Packages and many Deliveries  
A Package can only have one Delivery and one Customer  
A Delivery can have many Packages, but only one Customer, one Drone, and one Route  
A Route can have many Deliveries and many Flight Logs  
A Flight Log can only have one Drone and one Route  
A Drone can have many Deliveries, Flight Logs, and Maintenence Logs, but only one Battery  
A Battery can only have one Drone and one Charging Station  
A Charging Station can have many Batteries  
A Maintenence Log can have many Maintenence Parts, but only one Technician and one Drone  
A Technician can have many Maintenence Logs  
A Maintenence Part can only have one Maintenence Log  

## Data Dictionary

Battery_Usage

| COLUMN | DATA TYPE | ROLE | DESCRIPTION |
|--------|----------|------|-------------|
| battery_usage_current | DECIMAL(4,2) | PK | The main identifier of the current battery usage of a drone |
| drone_id | VARCHAR(35) | FK | Identifier of the drone tied to the current battery percentage number |
| station_id | VARCHAR(35) | FK | Identifier of the station tied to battery usage |
| charge_start_time | DATETIME |  | The time the charge session was initiated |
| charge_end_time | DATETIME |  | The time the charge session concluded |
| battery_level_before | INT |  | The initial battery percentage pre-charging session |
| battery_level_after | INT |  | The battery percentage post-charging session |

Charging_Stations

| COLUMN | DATA TYPE | ROLE | DESCRIPTION |
|--------|----------|------|-------------|
| station_id | VARCHAR(35) | PK | The primary identifier for a station |
| location | VARCHAR(45) |  | The location of a specific drone charging station |
| station_status | VARCHAR(45) |  | The current status of a drone charging location |

Customers

| COLUMN | DATA TYPE | ROLE | DESCRIPTION |
|--------|----------|------|-------------|
| customer_id | VARCHAR(35) | PK | Primary identifier of the customer |
| name | VARCHAR(45) |  | The name of the respective customer |
| phone | VARCHAR(45) |  | The customer's phone number |
| email | VARCHAR(45) |  | The customer's email address |
| delivery_address | VARCHAR(45) |  | The customer's delivery address of choice |

Deliveries

| COLUMN | DATA TYPE | ROLE | DESCRIPTION |
|--------|----------|------|-------------|
| delivery_id | VARCHAR(45) | PK | The main identifier for a specific delivery |
| drone_id | VARCHAR(35) | FK | Identifier for the drone assigned to respective delivery |
| route_id | VARCHAR(35) | FK | Identifier for the route assigned to respective delivery |
| customer_id | VARCHAR(35) | FK | Identifier for the customer assigned to respective delivery |
| start_time | DATETIME |  | Date at which the delivery process was initiatied |
| end_time | DATETIME |  | Date at which the delivery process concluded |
| delivery_status | VARCHAR(25) |  | Current status of a respective delivery |

Drones

| COLUMN | DATA TYPE | ROLE | DESCRIPTION |
|--------|----------|------|-------------|
| drone_id | VARCHAR(35) | PK | Main identifier for each individual drone |
| model | VARCHAR(35) |  | Displays model of respective drone |
| status | VARCHAR(11) |  | Gives insight on current operating condition |
| total_flight_hours | DECIMAL(7,2) |  | Shows flight hours for each respectve drone |
| max_payload_weight | INT |  | Displays max weight a drone can carry at one time |
| current_battery_level | INT |  | Shows what battery percent the drone is at right now |

Flight_Logs

| COLUMN | DATA TYPE | ROLE | DESCRIPTION |
|--------|----------|------|-------------|
| flight_log_id | VARCHAR(45) | PK | The primary identifier for an individual flight |
| drone_id | VARCHAR(35) | FK | Identifier for the drone assigned to the flight |
| route_id | VARCHAR(35) | FK | Identifier for the route assigned to the flight |
| flight_start_time | DATETIME |  | The time at which the flight began |
| flight_end_time | DATETIME |  | The time at which the flight concluded |
| flight_duration_hours | DECIMAL(6,2) |  | The span of time between flight start/end times |

Maintenance_Logs

| COLUMN | DATA TYPE | ROLE | DESCRIPTION |
|--------|----------|------|-------------|
| maintenance_log_id | VARCHAR(45) | PK | The main identifier for an individual maintenance session |
| drone_id | VARCHAR(35) | FK | Identifier for the drone associated with a maintenance log |
| lead_technician_id | VARCHAR(35) | FK | Identifier for the lead technician associated with a maintenance log |
| maintenance_date | DATETIME |  | The date that maintenance took place |
| maintenance_type | VARCHAR(45) |  | Type of maintenance that took place |
| description | VARCHAR(99) |  | Description of maintenance that took place |
| total_flight_hours_at_service | DECIMAL(5,2) |  | The flight hours completed at service for the respective drone |

Maintenance_Parts

| COLUMN | DATA TYPE | ROLE | DESCRIPTION |
|--------|----------|------|-------------|
| part_id | VARCHAR(45) | PK | The main identifier of a specific drone part |
| maintenance_log_id | VARCHAR(45) | FK | The maintenance session tied to a part |
| part_name | VARCHAR(45) |  | The name of a specific part |
| quantity | INT |  | The total amount of a part in stock |
| cost | DECIMAL(8,2) |  | The cost of an individual part |

Packages

| COLUMN | DATA TYPE | ROLE | DESCRIPTION |
|--------|----------|------|-------------|
| package_id | VARCHAR(45) | PK | Main identifier of the individual package |
| customer_id | VARCHAR(35) | FK | Identifier for the customer who ordered the respective package |
| delivery_id | VARCHAR(45) | FK | Identifier for the delivery of the respective package |
| weight | DECIMAL(5,2) |  | How much the package weighs |
| dimensions | VARCHAR(45) |  | The given dimensions of a specific package |
| package_status | VARCHAR(15) |  |  The current status of a respective package |

Routes

| COLUMN | DATA TYPE | ROLE | DESCRIPTION |
|--------|----------|------|-------------|
| route_id | VARCHAR(35) | PK | Primary identifier of a specific route |
| origin_location | VARCHAR(45) |  | Location of orgin for the route |
| destination_location | VARCHAR(45) |  | Location of end destination for the route |
| distance_km | DECIMAL(10,2) |  | Total distance of the route in kilometers |
| estimated_duration | VARCHAR(45) |  | Length of time of the route |

Technicians

| COLUMN | DATA TYPE | ROLE | DESCRIPTION |
|--------|----------|------|-------------|
| technician_id | VARCHAR(35) | PK | Primary identifier for the individual technician |
| name | VARCHAR(35) |  | The name of the respective technician |
| specialization | VARCHAR(45) |  | The type of work a technician specializes in |
| phone | VARCHAR(45) |  | The phone number of a specific technician |
| email | VARCHAR(45) |  | The email address of a specific technician |


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
