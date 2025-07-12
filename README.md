# SQL Project
Educational projects under the guidance of experienced teachers

--CREATE 7 tables 
create table booking_list (
	id_booking serial primary key,
	date_in date, 
	date_out date,
	id_room int references list_of_rooms(id_room),
	id_guest int references list_of_guests(id_guest),
	total_price int 
); 

create table list_of_rooms (
	id_room serial primary key,
	floor numeric,
	id_room_type int references room_type(id_room_type),
	price_per_night int
);

create table list_of_guests (
	id_guest serial primary key, 
	first_name varchar(20),
	last_name varchar (30), 
	phone_number int
); 

Create table booking_to_extra (
	id_booking int references booking_list(id_booking) ,
	id_extra_s int references extra_services (id_extra_s)
); 

create table extra_services (
	id_extra_s serial Primary key,
	name_extra_s varchar (20),
	price_extra_s int,
	id_employee int references employee_list (id_employee) 
);

create table room_type (
	id_room_type serial Primary key,
	room_type varchar (10)
);

create table employee_list(
	id_employee serial primary key,
	first_name_employee varchar(20),
	last_name_employee varchar(30),
	phone_employee int
);

--INSERT 7 tables
Insert into room_type (room_type) values 
	('standart'), ('studio'), ('deluxe'), ('family'); 

Insert into employee_list (first_name_employee, last_name_employee, phone_employee)
	values
		('John', 'Doe', '1234'),
		('Jane', 'Smith', '5678'),
		('Michael', 'Johnson', '8765'),
		('Emily', 'Davis', '4321');

insert into list_of_rooms (floor, id_room_type, price_per_night)
	VALUES 
		(1, 1, 100), -- Standart
		(1, 2, 150), -- Studio
		(2, 3, 200), -- Deluxe
		(2, 4, 180), -- Family
		(3, 1, 110), -- Standart
		(3, 2, 160), -- Studio
		(4, 3, 210), -- Deluxe
		(4, 4, 190), -- Family
		(5, 1, 120), -- Standart
		(5, 2, 170); -- Studio

Insert into list_of_guests (first_name, last_name, phone_number)
	VALUES 
		('Alice', 'Walker', 5551234),
		('Tom', 'Scott', 5555678),
		('Megan', 'Evans', 5558765),
		('Liam', 'Roberts', 5554321),
		('Sophia', 'Carter', 5558760),
		('Jack', 'Mitchell', 5551347),
		('Chloe', 'Nelson', 5559812),
		('Ryan', 'Adams', 5557773),
		('Grace', 'Perez', 5554531),
		('Luke', 'Baker', 5559624),
		('Hannah', 'Collins', 5558342),
		('Nora', 'Sanders', 5552991),
		('Oliver', 'Morris', 5556139),
		('Zoe', 'Hughes', 5554732),
		('Henry', 'Foster', 5559840),
		('Isabella', 'Wright', 5558204),
		('Daniel', 'Price', 5551568),
		('Ella', 'James', 5553597),
		('Leo', 'Russell', 5554726),
		('Victoria', 'Bell', 5556041);

Insert Into extra_services (name_extra_s, price_extra_s, id_employee)
	VALUES 
		('Глажка одежды', 20, 1),  -- Глажка, цена 20, сотрудник с id = 1 (например, John Doe)
		('Трансфер', 50, 2),  -- Трансфер, цена 50, сотрудник с id = 2 (например, Jane Smith)
		('Прачечная', 30, 3),  -- Прачечная, цена 30, сотрудник с id = 3 (например, Michael Johnson)
		('Массаж', 70, 4);  -- Массаж, цена 70, сотрудник с id = 4 (например, Emily Davis) 

INSERT INTO booking_list (date_in, date_out, id_room, id_guest) 
	VALUES
('2025-02-01', '2025-02-05', 1, 1),
		('2025-02-01', '2025-02-05', 1, 1),
		('2025-02-04', '2025-02-06', 2, 7),
 		('2025-02-05', '2025-02-07', 3, 5),
  		('2025-02-06', '2025-02-09', 4, 9),
  		('2025-02-07', '2025-02-10', 5, 2),
 		('2025-02-08', '2025-02-11', 6, 11),
 		('2025-02-09', '2025-02-12', 7, 15),
 		('2025-02-10', '2025-02-13', 8, 18),
 		('2025-02-11', '2025-02-14', 9, 4),
  		('2025-02-12', '2025-02-15', 10, 19),
  		('2025-02-13', '2025-02-16', 1, 12),
  		('2025-02-14', '2025-02-17', 2, 8),
  		('2025-02-15', '2025-02-18', 3, 14),
  		('2025-02-16', '2025-02-19', 4, 20),
  		('2025-02-17', '2025-02-20', 5, 6),
  		('2025-02-18', '2025-02-21', 6, 13),
  		('2025-02-19', '2025-02-22', 7, 16),
  		('2025-02-20', '2025-02-23', 8, 1),
  		('2025-02-21', '2025-02-24', 9, 10),
  		('2025-02-22', '2025-02-25', 10, 3),
  		('2025-02-23', '2025-02-26', 1, 5),
  		('2025-02-24', '2025-02-27', 2, 7),
  		('2025-02-25', '2025-02-28', 3, 4),
  		('2025-02-26', '2025-02-28', 4, 6),
  		('2025-02-27', '2025-03-01', 5, 2),
  		('2025-02-28', '2025-03-02', 6, 8),
  		('2025-03-01', '2025-03-04', 7, 11),
  		('2025-03-02', '2025-03-05', 8, 15),
  		('2025-03-03', '2025-03-06', 9, 14),
  		('2025-03-04', '2025-03-07', 10, 9);

insert into booking_to_extra (id_booking, id_extra_s)
	VALUES (1,2), (3,4), (7,3), (10,1), (16,2), (19,2), (23,2), (25,4), (29,3), (30,2),(1,3);
--UPDATE booking_list
update booking_list b
set total_price = 
		(date_out-date_in)*
		(select price_per_night from list_of_rooms where id_room=b.id_room)+
		coalesce( 
		(select sum(price_extra_s) from extra_services e, booking_to_extra be
		where  e.id_extra_s=be.id_extra_s AND b.id_booking=be.id_booking)  
		,0); 

--SELECT * FROM 7 tables
select * from room_type;
Select * from employee_list;
Select * From list_of_rooms; 
Select * From list_of_guests;
Select * From extra_services; 
Select * From booking_list;
Select * From booking_to_extra; 

--FINAL TABLE 
SELECT
	b.id_booking, lg.first_name, lg.last_name, b.date_in,b.date_out, (b.date_out-b.date_in) as nights_qty, 
	r.room_type, lr.price_per_night, 
	e.name_extra_s,e.price_extra_s, empl.first_name_employee, empl.last_name_employee,b.total_price
FROM booking_list b
LEFT JOIN booking_to_extra be
	ON b.id_booking=be.id_booking
LEFT JOIN extra_services e
	ON be.id_extra_s=e.id_extra_s
LEFT JOIN employee_list empl
	ON e.id_employee=empl.id_employee
LEFT JOIN list_of_rooms lr
	ON b.id_room=lr.id_room 
LEFT JOIN room_type r
	ON lr.id_room_type=r.id_room_type 
LEFT JOIN list_of_guests lg
	ON b.id_guest=lg.id_guest
ORDER BY 1;

--АГРЕГИРУЮЩИЕ
--посчитать сколько каждый сотрудник выполнил работ по всем броням 
SELECT empl.first_name_employee, empl.last_name_employee, sum(e.id_employee) as qty_services 
FROM booking_to_extra be
JOIN extra_services e
	ON be.id_extra_s=e.id_extra_s
JOIN employee_list empl
	ON e.id_employee=empl.id_employee
GROUP BY e.id_employee, empl.first_name_employee, empl.last_name_employee;

--посчитать сколько раз гость делал бронь 
SELECT lg.first_name, lg.last_name, count(*) 
FROM booking_list b
JOIN list_of_guests lg
	ON b.id_guest=lg.id_guest
GROUP BY lg.id_guest
ORDER BY 1,2;

--АГРЕГИРУЮЩИЕ+ПОДЗАПРОС 
--вывести брони, где итоговая цена больше средней за все время 
SELECT * 
FROM booking_list 
WHERE total_price > ( SELECT 
	avg((date_out-date_in)*
		(select price_per_night from list_of_rooms where id_room=b.id_room)+
		coalesce( 
		(select sum(price_extra_s) from extra_services e, booking_to_extra be
		where  e.id_extra_s=be.id_extra_s AND b.id_booking=be.id_booking)  
		,0))
	FROM booking_list b
	LEFT JOIN booking_to_extra be
		ON b.id_booking=be.id_booking
	LEFT JOIN extra_services e
		ON be.id_extra_s=e.id_extra_s
	);

--вывести количество броней для каждого типа комнаты, сколько ночей было проведено гостями в этих комнатах и 
--средняя цена для каждого типа комнаты 
SELECT 
    r.room_type,
    COUNT(b.id_booking) AS total_bookings,
    SUM(b.date_out - b.date_in) AS total_nights, 
	(SELECT AVG(price_per_night) 
     FROM list_of_rooms 
     WHERE id_room_type = r.id_room_type) AS avg_price_per_night
FROM booking_list b
LEFT JOIN list_of_rooms lr
	ON b.id_room=lr.id_room 
LEFT JOIN room_type r
	ON lr.id_room_type=r.id_room_type 
LEFT JOIN list_of_guests lg
	ON b.id_guest=lg.id_guest
GROUP BY r.id_room_type
ORDER BY 1; 

