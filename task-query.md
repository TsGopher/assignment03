## Query 1: JOIN

#### Requirement: Retrieve booking information along with Customer name and Vehicle name.

```sql
SELECT
    b.booking_id,
    u.name AS customer_name,
    v.name AS vehicle_name,
    b.start_date,
    b.end_date,
    b.total_cost
FROM bookings b
INNER JOIN users u ON b.user_id = u.user_id
INNER JOIN vehicles v ON b.vehicle_id = v.vehicle_id
```

## Query 2: EXISTS

#### Requirement: Find all vehicles that have never been booked.

```sql
SELECT
    v.vehicle_id,
    v.name,
    v.type,
    v.model,
    v.registration_number,
    v.rental_price,
    v.status
FROM vehicles v
WHERE NOT EXISTS (
    SELECT 1
    FROM bookings b
    WHERE b.vehicle_id = v.vehicle_id
);
```

## Query 3: WHERE

#### Requirement: Retrieve all available vehicles of a specific type (e.g. cars).

```sql
SELECT * FROM vehicles
WHERE status = 'available' AND type = 'car';
```

## Query 4: GROUP BY and HAVING

#### Requirement: Find the total number of bookings for each vehicle and display only those vehicles that have more than 2 bookings.

```sql
SELECT
    v.name AS vehicle_name,
    COUNT(b.booking_id) AS total_bookings
FROM vehicles v
INNER JOIN bookings b
    ON v.vehicle_id = b.vehicle_id
GROUP BY
    v.vehicle_id,
    v.name
HAVING COUNT(b.booking_id) > 2;
```
