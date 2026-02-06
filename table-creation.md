## USER TABLE

```sql
CREATE TYPE USER_ROLE AS ENUM ('Admin', 'Customer');

create table users (
user_id serial primary key,
name varchar(250),
email varchar(300) not null unique,
phone varchar(250),
role USER_ROLE
)
```

## VEHICLES TABLE

```sql
CREATE TYPE VEHICLE_TYPE AS ENUM ('car', 'bike', 'truck');
CREATE TYPE AVAILABILITY_STATUS AS ENUM ('available', 'rented', 'maintenance');

create table vehicles (
vehicle_id serial primary key,
name varchar(250) not null,
type VEHICLE_TYPE ,
model varchar(25),
registration_number varchar(50),
rental_price int,
status AVAILABILITY_STATUS
)
```

## BOOKINGS TABLE

```sql
CREATE TYPE BOOKING_STATUS AS ENUM ('pending', 'confirmed', 'completed', 'cancelled');

create table bookings (
booking_id serial primary key,
user_id int references users(user_id),
vehicle_id int references vehicles(vehicle_id),
start_date date,
end_date date,
status BOOKING_STATUS,
total_cost int
)
```

---

---

---

## Insert into users table

```sql
INSERT INTO users (name, email, phone, role) VALUES
('Alice', 'alice@example.com', '1234567890', 'Customer'),
('Bob', 'bob@example.com', '0987654321', 'Admin'),
('Charlie', 'charlie@example.com', '1122334455', 'Customer');
```

## Insert into vehicles table

```sql
INSERT INTO vehicles (name, type, model, registration_number, rental_price, status) VALUES
('Toyota Corolla', 'car', '2022', 'ABC-123', 50, 'available'),
('Honda Civic', 'car', '2021', 'DEF-456', 60, 'rented'),
('Yamaha R15', 'bike', '2023', 'GHI-789', 30, 'available'),
('Ford F-150', 'truck', '2020', 'JKL-012', 100, 'maintenance');
```

## Insert into bookings table

```sql
INSERT INTO bookings (user_id, vehicle_id, start_date, end_date, status, total_cost) VALUES
(1, 2, '2023-10-01', '2023-10-05', 'completed', 240),
(1, 2, '2023-11-01', '2023-11-03', 'completed', 120),
(3, 2, '2023-12-01', '2023-12-02', 'confirmed', 60),
(1, 1, '2023-12-10', '2023-12-12', 'pending', 100);
```
