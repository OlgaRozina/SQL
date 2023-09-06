- Host: 159.69.151.133
- Port: 5056
- DB: Connect to the table where DDL operations were performed
- User: Connect using the user who performed DDL operations
- Pass: 123


## 1. Retrieve all employees whose salaries exist in the database, along with their salaries.

```
SELECT employees.employee_name, salary.monthly_salary 
FROM employee_salary 
JOIN salary ON employee_salary.salary_id=salary.id 
JOIN employees ON employee_salary.employee_id=employees.id;
```
***
## 2. Retrieve all employees whose salaries are less than 2000.

```
SELECT employees.employee_name, salary.monthly_salary
FROM employee_salary 
JOIN salary ON employee_salary.salary_id=salary.id
JOIN employees ON employee_salary.employee_id=employees.id
WHERE monthly_salary < 2000;
```
***
## 3. Retrieve all salary positions where no employee is assigned. (Salaries exist, but it's unclear who receives them)

```
SELECT salary.monthly_salary, employees.employee_name
FROM employee_salary
LEFT JOIN salary ON salary.id = employee_salary.salary_id
LEFT JOIN employees ON employees.id = employee_salary.employee_id
WHERE employees.employee_name IS NULL;
```
***
## 4. Retrieve all salary positions less than 2000 where no employee is assigned. (Salaries exist, but it's unclear who receives them)

```
SELECT salary.monthly_salary, employees.employee_name
FROM employee_salary
LEFT JOIN salary ON salary.id = employee_salary.salary_id
LEFT JOIN employees ON employees.id = employee_salary.employee_id
WHERE salary.monthly_salary < 2000 AND employees.employee_name IS NULL;
```
***
## 5. Find all employees who have not been allocated a salary.

```
SELECT salary.monthly_salary, employees.employee_name
FROM employee_salary
LEFT JOIN salary ON salary.id = employee_salary.salary_id
LEFT JOIN employees ON employees.id = employee_salary.employee_id
WHERE salary.monthly_salary IS NULL;
```
***
## 6. Retrieve all employees with their job titles.

```
SELECT employees.employee_name, roles.role_name 
FROM roles_employee
JOIN employees ON employees.id = roles_employee.employee_id 
JOIN roles ON roles.id = roles_employee.role_id;
```
***
## 7. Retrieve names and job titles of Java developers only.

```
SELECT employees.employee_name, roles.role_name 
FROM roles_employee
JOIN employees ON employees.id = roles_employee.employee_id 
JOIN roles ON roles.id = roles_employee.role_id
WHERE roles.role_name LIKE '%Java %';
```
***
## 8. Retrieve names and job titles of Python developers only.

```
SELECT employees.employee_name, roles.role_name 
FROM roles_employee
JOIN employees ON employees.id = roles_employee.employee_id 
JOIN roles ON roles.id = roles_employee.role_id
WHERE roles.role_name LIKE '%Python%';
```
***
## 9. Retrieve names and job titles of all QA engineers.

```
SELECT employees.employee_name, roles.role_name 
FROM roles_employee
JOIN employees ON employees.id = roles_employee.employee_id 
JOIN roles ON roles.id = roles_employee.role_id
WHERE roles.role_name LIKE '%QA%';

```
***
## 10. Retrieve names and job titles of manual QA engineers.

```
SELECT employees.employee_name, roles.role_name 
FROM  roles_employee
JOIN employees ON employees.id = roles_employee.employee_id 
JOIN roles ON roles.id = roles_employee.role_id
WHERE roles.role_name LIKE '%Manual QA%';
```
***
## 11. Retrieve names and job titles of QA automation engineers.

```
SELECT employees.employee_name, roles.role_name 
FROM roles_employee
JOIN employees ON employees.id = roles_employee.employee_id 
JOIN roles ON roles.id = roles_employee.role_id
WHERE roles.role_name LIKE '%Automation QA%';
```
***
## 12. Retrieve names and salaries of Junior specialists.

```
SELECT employees.employee_name, roles.role_name 
FROM roles_employee
JOIN employees ON employees.id = roles_employee.employee_id 
JOIN roles ON roles.id = roles_employee.role_id
WHERE roles.role_name LIKE '%Junior%';
```
***
## 13. Retrieve names and salaries of Middle specialists.

```
SELECT employees.employee_name, roles.role_name 
FROM roles_employee
JOIN employees ON employees.id = roles_employee.employee_id 
JOIN roles ON roles.id = roles_employee.role_id
WHERE roles.role_name LIKE '%Middle%';
```
***
## 14. Retrieve names and salaries of Senior specialists.

```
SELECT employees.employee_name, roles.role_name 
FROM roles_employee
JOIN employees ON employees.id = roles_employee.employee_id 
JOIN roles ON roles.id = roles_employee.role_id
WHERE roles.role_name LIKE '%Senior%';
```
***
## 15. Retrieve salaries of Java developers.

```
SELECT monthly_salary 
FROM roles_employee
JOIN employees ON employee_id = employees.id
JOIN roles ON role_id = roles.id
JOIN employee_salary ON employee_salary.employee_id = roles_employee.employee_id
join salary ON employee_salary.salary_id = salary.id
WHERE roles.role_name LIKE '%Java %';
```
***
## 16. Retrieve salaries of Python developers.

```
SELECT monthly_salary 
FROM roles_employee
JOIN employees ON employee_id = employees.id
JOIN rolesON role_id = roles.id
JOIN employee_salary ON employee_salary.employee_id = roles_employee.employee_id
JOIN salary ON employee_salary.salary_id = salary.id
WHERE roles.role_name LIKE '%Python%';

```
***
## 17. Retrieve names and salaries of Junior Python developers.

```
SELECT employees.employee_name, salary.monthly_salary
FROM roles_employee 
JOIN employees ON roles_employee.employee_id = employees.id
JOIN roles ON roles_employee.role_id = roles.id
JOIN employee_salary ON employee_salary.employee_id = roles_employee.employee_id
JOIN salary ON employee_salary.salary_id = salary.id
WHERE roles.role_name LIKE '%Junior Python%';
```
***
## 18. Retrieve names and salaries of Middle JS developers.

```
SELECT employees.employee_name, salary.monthly_salary
FROM roles_employee 
JOIN employees ON roles_employee.employee_id = employees.id
JOIN roles ON roles_employee.role_id = roles.id
JOIN employee_salary ON employee_salary.employee_id = roles_employee.employee_id
JOIN salary ON employee_salary.salary_id = salary.id
WHERE roles.role_name LIKE '%Middle Java%';
```
***
## 19. Retrieve names and salaries of Senior Java developers.

```
SELECT employees.employee_name, salary.monthly_salary
FROM roles_employee 
JOIN employees ON  roles_employee.employee_id = employees.id
JOIN roles ON roles_employee.role_id = roles.id
JOIN employee_salary ON employee_salary.employee_id = roles_employee.employee_id
JOIN salary ON employee_salary.salary_id = salary.id
WHERE roles.role_name LIKE '%Senior Java%';
```
***
## 20. Retrieve salaries of Junior QA engineers.

```
SELECT salary.monthly_salary 
FROM roles_employee
JOIN employees ON employee_id = employees.id
JOIN roles ON role_id = roles.id
JOIN employee_salary ON employee_salary.employee_id = roles_employee.employee_id
JOIN salary ON employee_salary.salary_id = salary.id
WHERE roles.role_name LIKE 'Junior %engineer%';
```
***
## 21. Retrieve the average salary of all Junior specialists.

```
SELECT avg (salary.monthly_salary) 
FROM roles_employee
JOIN employees ON employee_id = employees.id
JOIN roles ON role_id = roles.id
JOIN employee_salary ON employee_salary.employee_id = roles_employee.employee_id
JOIN salary ON employee_salary.salary_id = salary.id
WHERE roles.role_name LIKE '%Junior%';
```
***
## 22. Retrieve the sum of salaries for JS developers.

```
SELECT sum (salary.monthly_salary) 
FROM roles_employee
JOIN employees ON employee_id = employees.id
JOIN roles ON role_id = roles.id
JOIN employee_salary ON employee_salary.employee_id = roles_employee.employee_id
JOIN salary ON employee_salary.salary_id = salary.id
WHERE roles.role_name LIKE '%Java%';
```
***
## 23. Retrieve the minimum salary of QA engineers.

```
SELECT min(salary.monthly_salary) 
FROM roles_employee
JOIN employees ON employee_id = employees.id
JOIN roles ON role_id = roles.id
JOIN employee_salary ON employee_salary.employee_id = roles_employee.employee_id
JOIN salary ON employee_salary.salary_id = salary.id
WHERE roles.role_name LIKE '%QA%';
```
***
## 24. Retrieve the maximum salary of QA engineers.

```
SELECT max(salary.monthly_salary) 
FROM roles_employee
JOIN employees ON employee_id = employees.id
JOIN roles ON role_id = roles.id
JOIN employee_salary ON employee_salary.employee_id = roles_employee.employee_id
JOIN salary ON employee_salary.salary_id = salary.id
WHERE roles.role_name LIKE '%QA%';
```
***
## 25. Retrieve the count of QA engineers.

```
SELECT count(roles.role_name) 
FROM roles_employee
JOIN employees ON employee_id = employees.id
JOIN roles ON role_id = roles.id
JOIN employee_salary ON employee_salary.employee_id = roles_employee.employee_id
JOIN salary ON employee_salary.salary_id = salary.id
WHERE roles.role_name LIKE'%QA%';
```
***
## 26. Retrieve the count of Middle specialists.

```
SELECT count(roles.role_name) 
FROM roles_employee
JOIN employees ON employee_id = employees.id
JOIN roles ON role_id = roles.id
JOIN employee_salary ON employee_salary.employee_id = roles_employee.employee_id
JOIN salary ON employee_salary.salary_id = salary.id
WHERE roles.role_name LIKE '%Middle%';
```
***
## 27. Retrieve the count of developers.

```
SELECT count(roles.role_name) 
FROM roles_employee
JOIN employees ON employee_id = employees.id
JOIN roles ON role_id = roles.id
JOIN employee_salary ON employee_salary.employee_id = roles_employee.employee_id
JOIN salary ON employee_salary.salary_id = salary.id
WHERE roles.role_name LIKE'%developer%';
```
***
## 28. Retrieve the total salary fund of developers.

```
SELECT sum (salary.monthly_salary)
FROM roles_employee
JOIN employees ON employee_id = employees.id
JOIN roles ON role_id = roles.id
JOIN employee_salary ON employee_salary.employee_id = roles_employee.employee_id
JOIN salary ON employee_salary.salary_id = salary.id
WHERE roles.role_name LIKE '%developer%';
```
***
## 29. Retrieve names, job titles, and salaries of all specialists in ascending order.

```
SELECT employees.employee_name, roles.role_name 
FROM roles_employee
JOIN employees ON employees.id = roles_employee.employee_id 
JOIN roles ON roles.id = roles_employee.role_id
JOIN employee_salary ON employee_salary.employee_id = roles_employee.employee_id
JOIN salary ON employee_salary.salary_id = salary.id
ORDER BY salary.monthly_salary ASC;
```
***
## 30. Retrieve names, job titles, and salaries of all specialists in ascending order for specialists with salaries between 1700 and 2300.

```
SELECT employees.employee_name, roles.role_name, salary.monthly_salary
FROM roles_employee
JOIN employees ON employees.id = roles_employee.employee_id 
JOIN roles ON roles.id = roles_employee.role_id
JOIN employee_salary ON employee_salary.employee_id = roles_employee.employee_id
JOIN salary ON employee_salary.salary_id = salary.id
WHERE salary.monthly_salary between 1700 and 2300
ORDER BY salary.monthly_salary ASC;
```
***
## 31. Retrieve names, job titles, and salaries of all specialists in ascending order for specialists with salaries less than 2300.

```
SELECT employees.employee_name, roles.role_name, salary.monthly_salary
FROM roles_employee
JOIN employees ON employees.id = roles_employee.employee_id 
JOIN roles ON roles.id = roles_employee.role_id
JOIN employee_salary ON employee_salary.employee_id = roles_employee.employee_id
JOIN salary ON employee_salary.salary_id = salary.id
WHERE salary.monthly_salary<2300
ORDER BY salary.monthly_salary ASC;
```
***
## 32. Retrieve names, job titles, and salaries of all specialists in ascending order for specialists with salaries equal to 1100, 1500, 2000.1. On the local repository, make branches for:

```
SELECT employees.employee_name, roles.role_name, salary.monthly_salary
FROM roles_employee
JOIN employees ON employees.id = roles_employee.employee_id 
JOIN roles ON roles.id = roles_employee.role_id
JOIN employee_salary ON employee_salary.employee_id = roles_employee.employee_id
JOIN salary ON employee_salary.salary_id = salary.id
WHERE salary.monthly_salary IN (1100, 1500, 2000)
ORDER BY salary.monthly_salary ASC;
```

***