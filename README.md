# The Good Table

### Website URL: https://restaurant-client-cs.herokuapp.com/dashboard

The Good Table is a restaurant schedule management application that allows the user to manage their restaurant's reservations and tables. They are able to add new reservations to certain dates and times, as well as create tables with a desired capacity to seat their customers at.

## Technologies Used
### Front End
- React.js
- Bootstrap
- CSS

### Back End
- Node.js
- Express.js
- PostgreSQL 
- Knex.js

## Installation
1. Fork and clone this repository.
2. Run `cp ./back-end/.env.sample ./back-end/.env`.
3. Update the `./back-end/.env` file with the connection URL's to your ElephantSQL database instance.
4. Run `cp ./front-end/.env.sample ./front-end/.env`.
5. You should not need to make changes to the `./front-end/.env` file unless you want to connect to a backend at a location other than `http://localhost:5000`.
6. Run `npm install` to install project dependencies.
7. Run `npm run start:dev` to start your server in development mode.

## Features

### Dashboard
The Dashboard is the home page of the website. This is where the user can check reservations dates and manage reservations and tables. If it is the day of a party's reservation, the user is able to either seat the party at an available table, edit the party's reservation, or cancel the reservation.

![Dashboard](https://i.gyazo.com/9c809fa135d4ec1b84a7668c1476b0de.jpg)

### Search Page
The Search Page allows the user to search up the phone number of a party's reservation. If no input is put in or a phone number is unrecognized, it will display "No reservations found".

![Search Page](https://i.gyazo.com/6876c69fe45a0593a1e25570649c4f0b.png)

### Reservation Page
The Reservation Page allows the user to create a reservation for their party. They have to input their first name, last name, mobile number, reservation date, reservation time, and party size. The reservation date cannot be today's date. The reservation time must be between 10:30 AM and 9:30 PM. Reservations are unable to be made on Tuesday's.

![Reservation Page](https://i.gyazo.com/608c138268498db6dfbb75f360fd0c0c.png)

### Table Page
The Table Page allows the user to create a new table for parties to be sat at. They are able to enter the name of the table as well as the capacity.

![Table Page](https://i.gyazo.com/c936952edfb6c4d5742bc2524515b3b2.png)

## API
## Reservations
GET `/reservations`
- Retrieves all current reservations

----

GET `/reservations/:reservation_id`
- Retrieves the reservation with the corresponding reservation id 

GET `/reservations/:reservation_id/status`
- Retrieves the desired reservation's status. May return *seated*, *finished*, or *canceled*.

PUT `/reservations/:reservation_id`
- Updates an existing reservation

### Parameters:
| Parameter | Type |
| --------- | ---- |
| `reservation_id`| `int` |

----

POST `/reservations`
- Creates a new reservation

### Parameters:
| Parameter | Type |
| --------- | ---- |
| `first_name`| `str` |
| `last_name`| `str` |
| `mobile_number`| `int` |
| `reservation_date`| `date` |
| `reservation_time`| `str` |
| `people`| `int` |

----

## Tables
GET `/tables`
- Retrieves all tables

----

PUT `/tables/:table_id/seat`
- Updates table status to connected to a reservation 

DELETE `/tables/:table_id/seat`
- Updates the status of the reservation to *finished* at the table and clears the reservation_id
- Does not delete the table, returns the status of the table to *free*

### Parameters:
| Parameter | Type |
| --------- | ---- |
| `reservation_id`| `int` |

----

POST `/tables`
- Creates a new table

### Parameters:
| Parameter | Type |
| --------- | ---- |
| `table_name`| `str` |
| `capacity`| `int` |

----
