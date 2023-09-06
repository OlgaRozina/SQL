
## 1. Retrieve all fields and all rows.

```
select * from students;
```
***
## 2. Retrieve all students in the table.

```
select name from students;
```
***
## 3. Retrieve only user IDs.

```
select id from students;
```
***
## 4. Retrieve only user names.

```
select name from students;
```
***
## 5. Retrieve only user emails.

```
select email from students;
```
***
## 6. Retrieve user names and emails.

```
select name, email from students;
```
***
## 7. Retrieve user IDs, names, emails, and creation dates.

```
select id, name, email, created_on from students;
```
***
## 8. Retrieve users with the password 12333.

```
select * from students 
where password = '1233';
```
***
## 9. Retrieve users who were created on 2021-03-26 00:00:00.

```
select * from students
where created_on = '2021-03-26 00:00:00';
```
***
## 10. Retrieve users where the name contains the word Anna.

```
select * from students
where name like '%Anna%';
```
***
## 11. Retrieve users where the name ends with 8.

```
select * from students
where name like '%8';
```
***
##1 2. Retrieve users where the name contains the letter a.

```
select * from students
where name like '%а%';
```
***
## 13. Retrieve users who were created on 2021-07-12 00:00:00.

```
select * from students
where created_on = '2021-07-12 00:00:00';
```
***
## 14. Retrieve users who were created on 2021-07-12 00:00:00 and have the password 1m313.

```
select * from students
where created_on = '2021-07-12 00:00:00'and password = '1m313';
```
***
## 15. Retrieve users who were created on 2021-07-12 00:00:00 and have the word Andrey in their name.

```
select * from students
where created_on = '2021-07-12 00:00:00'and password = '%Andrey%';
```
***
## 16. Retrieve users who were created on 2021-07-12 00:00:00 and have the digit 8 in their name.

```
select * from students
where created_on = '2021-07-12 00:00:00' and name like '%8%'
```
***
## 17. Retrieve the user whose ID is 110.

```
select * from students
where id = '110';
```
***
## 18. Retrieve the user whose ID is 153.

```
select * from students
where id = '153';
```
***
## 19. Retrieve users with IDs greater than 140.

```
select * from students
where id > '140';
```
***
## 20. Retrieve users with IDs less than 130.

```
select * from students
where id < '130';
```
***
## 21. Retrieve users with IDs less than 127 or greater than 188.

```
select * from students
where id > '127' or id > '188';
```
***
## 22. Retrieve users with IDs less than or equal to 137.

```
select * from students
where id <= '137' ;
```
***
## 23. Retrieve users with IDs greater than or equal to 137.

```
select * from students
where id >= '137' ;
```
***
## 24. Retrieve users with IDs greater than 180 but less than 190.

```
select * from students
where id > '180' and id <'190';
```
***
## 25. Retrieve users with IDs between 180 and 190.

```
select * from students
where id between '180' and '190';
```
***
## 26. Retrieve users where the password is equal to 12333, 1m313, 123313.

```
select * from students
where password in ('12333', '1m313', '123313')
```
***
## 27. Retrieve users where created_on is equal to 2020-10-03 00:00:00, 2021-05-19 00:00:00, 2021-03-26 00:00:00.

```
select * from students
where created_on in ('2020-10-03 00:00:00', '2021-05-19 00:00:00', '2021-03-26 00:00:00');
```
***
## 28. Retrieve the minimum ID.

```
select min(id) from students;
```
***
## 29. Retrieve the maximum ID.

```
select max(id) from students;
```
***
## 30. Retrieve the count of users.

```
select count(id) from students;
```
***
## 31. Retrieve user ID, name, and user creation date. Sort in ascending order of user creation date.

```
select id, name, created_on from students
order by created_on asc;
```
***
## 32. Retrieve user ID, name, and user creation date. Sort in descending order of user creation date.

```
select id, name, created_on from students
order by created_on desc;
```
***