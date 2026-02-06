## SQL Queries Overview

This repository contains a single SQL script, `queries.sql`, with sample queries for a vehicle booking system. The tables referenced are `users`, `vehicles`, and `bookings`.

### Query 1 – Inner Join: Bookings with Customer and Vehicle Details

Returns each booking with the customer name and vehicle name by joining `bookings` (`b`) with `users` (`u`) and `vehicles` (`v`) on their respective foreign keys.

**Use case**: Generate a report of all bookings including who booked which vehicle and for what dates, along with the total cost.

### Query 2 – NOT EXISTS: Vehicles Without Any Bookings

Selects all vehicles from `vehicles` (`v`) for which **no** matching record exists in `bookings` (`b`).

**Use case**: Find vehicles that have never been booked, which can be useful for utilization analysis or deciding which vehicles to promote or remove.

### Query 3 – WHERE Filter: Available Cars

Selects all rows from `vehicles` where `status = 'available'` and `type = 'car'`.

**Use case**: List all cars that are currently available for rental.

### Query 4 – GROUP BY with HAVING: Popular Vehicles

Joins `vehicles` (`v`) with `bookings` (`b`), groups by vehicle, and counts the number of bookings per vehicle. The `HAVING` clause filters to only vehicles with more than 2 bookings.

**Use case**: Identify the most frequently booked vehicles (e.g., for pricing decisions or fleet planning).
