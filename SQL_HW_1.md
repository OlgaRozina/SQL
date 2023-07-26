# SQL_HW_1
##1. Create the 'employees' table:
```
create table employees (
 id  serial primary key,
 employee_name varchar (50 ) not null
); 
```
***
## 2. Fill the 'employee' table with 70 rows:
```
insert into employees(employee_name)
values ('Liam'),
       ('Emma'),
       ('Noah'),
       ('Olivia'),
       ('William'),
       ('Ava'),
       ('James'),
       ('Isabella'),
       ('Oliver'),
       ('Sophia'),
       ('Benjamin'),
       ('Mia'),
       ('Elijah'),
       ('Charlotte'),
       ('Lucas'),
       ('Amelia'),
       ('Mason'),
       ('Harper'),
       ('Logan'),
       ('Evelyn'),
       ('Alexander'),
       ('Abigail'),
       ('Ethan'),
       ('Emily'),
       ('Jacob'),
       ('Elizabeth'),
       ('Michael'),
       ('Sofia'),
       ('Daniel'),
       ('Avery'),
       ('Henry'),
       ('Ella'),
       ('Jackson'),
       ('Scarlett'),
       ('Sebastian'),
       ('Grace'),
       ('Aiden'),
       ('Chloe'),
       ('Matthew'),
       ('Victoria'),
       ('Samuel'),
       ('Riley'),
       ('David'),
       ('Aria'),
       ('Joseph'),
       ('Lily'),
       ('Carter'),
       ('Zoey'),
       ('Owen'),
       ('Penelope'),
       ('Wyatt'),
       ('Layla'),
       ('John'),
       ('Lillian'),
       ('Jack'),
       ('Nora'),
       ('Luke'),
       ('Addison'),
       ('Jayden'),
       ('Aubrey'),
       ('Gabriel'),
       ('Brooklyn'),
       ('Anthony'),
       ('Hannah'),
       ('Dylan'),
       ('Mila'),
       ('Isaac'),
       ('Scarlett'),
       ('Andrew'),
       ('Ellie');
```
***
## 3. Create the 'salary' table:
```
create table salary (
 id serial primary key,
 monthly_salary int not null
);
```
***
## 4. Fill the 'salary' table with 40 rows: 
```
insert into salary (monthly_salary)
values (1000),
       (1100),
       (1200),
       (1300),
       (1400),
       (1500),
       (1600),
       (1700),
       (1800),
       (1900),
       (2000),
       (2100),
       (2200),
       (2300),
       (2400),
       (2500);
```
***
## 5. Create the 'employee_salary' table:
```
create table employee_salary(
    id serial primary key,
    employee_id int not null unique,
    salary_id int not null
);
```
***
## 6. Fill the 'employee_salary' table with 40 rows. In 10 rows out of 40 insert non-existent employee_id:
```
insert into employee_salary (employee_id, salary_id)
values (3,7),
       (1,4),
       (2,11),
       (4,2),
       (6,6),
       (7,3),
       (8,10),
       (9,5),
       (10,4),
       (5,9),
       (40,13),
       (23,4),
       (11,2),
       (12,6),
       (13,7),
       (14,8),
       (17,4),
       (52,13),
       (15,10),
       (26,4),
       (16,1),
       (18,5),
       (33,7),
       (20,14),
       (21,5),
       (22,9),
       (24,3),
       (25,11),
       (28,6),
       (29,1),
	   (81,5),
	   (91,7),
	   (101,15),
	   (111,9),
	   (120,1),
	   (125,6),
	   (178,2),
	   (93,8),
	   (88,2),
	   (115,1);
```
***
## 7. Create the 'roles' table:
```
create table roles(
    id serial primary key,
    role_name int not null unique
   );
```
***
## 8. Change column type 'role_name' from int to varchar(30)
```
alter table roles
alter column role_name TYPE varchar(30);
```
***
## 9. Fill the 'roles' table with 20 rows:
```
insert into roles (role_name)
values ('Junior Python developer'),
        ('Middle Python developer'),
        ('Senior Python developer'),
        ('Junior Java developer'),
        ('Middle Java developer'),
        ('Senior Java developer'),
        ('Junior JavaScript developer'),
        ('Middle JavaScript developer'),
        ('Senior JavaScript developer'),
        ('Junior Manual QA engineer'),
	    ('Middle Manual QA engineer'),
	    ('Senior Manual QA engineer'),
	    ('Project Manager'),
	    ('Designer'),
	    ('HR'),
	    ('CEO'),
	    ('Sales manager'),
	    ('Junior Automation QA engineer'),
	    ('Middle Automation QA engineer'),
	    ('Senior Automation QA engineer');
```
***
## 10. Create the 'roles_employee' table:
```
create table roles_employee(
    id serial primary key,
    employee_id int not null unique references employees(id),
    role_id int not null references roles(id)
);
```
***
## 11. Fill the 'roles' table with 40 rows:
```
insert into roles_employee (employee_id, role_id)
values (3,7),
       (1,4),
       (2,11),
       (4,2),
       (6,6),
       (7,3),
       (8,10),
       (9,5),
       (10,4),
       (5,9),
       (61,13),
       (23,4),
       (11,2),
       (12,6),
       (13,7),
       (14,8),
       (17,4),
       (31,13),
       (15,10),
       (26,4),
       (16,1),
       (18,5),
       (33,7),
       (20,14),
       (21,5),
       (22,9),
       (24,3),
       (25,11),
       (28,6),
       (29,1),
	   (30,5),
	   (34,7),
	   (40,15),
	   (42,9),
	   (43,1),
	   (41,6),
	   (50,2),
	   (52,8),
	   (54,2),
	   (60,1);
```
***
