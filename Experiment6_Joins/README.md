# Experiment 6: Joins
FROM PATIENTS p 
INNER JOIN DOCTORS d 
ON p.doctor_id = d.doctor_id 
WHERE p.admission_date BETWEEN '2024-01-01' AND '2024-01-31';
```

**Output:**

![{CD7DB36A-DD6D-4C37-961E-1EBB5BE63E93}](https://github.com/user-attachments/assets/f750a5e3-439a-4509-8d7e-d7ec24b04ff4)


**Question 7**
---
-- Write a SQL statement to join the tables salesman, customer and orders so that the same column of each table appears once and only the relational rows are returned. 

```sql
-- SELECT o.ord_no, o.purch_amt, o.ord_date, c.cust_name, c.city AS "customer_city", c.grade, s.name AS "salesman_name", s.city AS "salesman_city", s.commission
FROM orders o 
INNER JOIN customer c
ON o.customer_id = c.customer_id 
INNER JOIN salesman s
ON c.salesman_id = s.salesman_id;
```

**Output:**

![{9BC83E59-5ABA-45C8-AF26-03F8F003D9AE}](https://github.com/user-attachments/assets/d0fbd2bb-2cac-49ff-90db-c19a115f276a)

**Question 8**
---
-- SQL statement to generate a report with customer name, city, order number, order date, order amount, salesperson name, and commission to determine if any of the existing customers have not placed orders or if they have placed orders through their salesman or by themselves.

```sql
-- SELECT 
    c.cust_name,
    c.city,
    o.ord_no,
    o.ord_date,
    o.purch_amt AS "Order Amount",
    s.name AS "name",
    s.commission
FROM 
    customer c
LEFT JOIN 
    orders o ON c.customer_id = o.customer_id
LEFT JOIN 
    salesman s ON o.salesman_id = s.salesman_id;

```

**Output:**

![{6D093C6B-7A8A-4639-AF60-68CF83E491CF}](https://github.com/user-attachments/assets/81923e3d-5465-4f86-a49b-f957b83933fd)


**Question 9**
---
-- Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), the "cust_name," "city," "grade," and "salesman_id" columns from the "customer" table (aliased as "c"), with a left join on the "salesman_id" column and a condition filtering for salesman_id values that have more than one associated customer.

```sql
-- SELECT 
    s.name, 
    c.cust_name, 
    c.city, 
    c.grade, 
    c.salesman_id
FROM 
    customer c
LEFT JOIN 
    salesman s ON c.salesman_id = s.salesman_id
WHERE 
    c.salesman_id IN (
        SELECT 
            salesman_id 
        FROM 
            customer 
        GROUP BY 
            salesman_id 
        HAVING 
            COUNT(customer_id) > 1
    )
ORDER BY 
    c.salesman_id, c.customer_id;

```

**Output:**

![{6736C694-5001-4FB0-91D4-5F37A911AEA4}](https://github.com/user-attachments/assets/d5fa612e-5b9b-4c3a-8f44-14d4bc183227)


**Question 10**
---
-- From the following tables write a SQL query to find those orders where the order amount exists between 500 and 2000. Return ord_no, purch_amt, cust_name, city.
```sql
-- SELECT o.ord_no, o.purch_amt, c.cust_name, c.city 
FROM orders o
INNER JOIN customer c
ON o.customer_id = c.customer_id 
WHERE o.purch_amt BETWEEN 500 AND 2000
ORDER BY o.ord_no;
```

**Output:**

![{1A8FB88F-DB09-4E5E-B65F-32B941634F4E}](https://github.com/user-attachments/assets/68f60cc2-b16d-4cf2-81c6-775097ddaf68)



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
