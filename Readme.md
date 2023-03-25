
1. Задание №1

CREATE DATABASE hw2;\
USE hw2;\
CREATE TABLE IF NOT EXISTS sales\
(\
 id INT PRIMARY KEY AUTO_INCREMENT,\
 order_date VARCHAR(45) NOT NULL,\
 count_product INT NOT NULL\
 );
 
 SELECT *\
 FROM sales;
 
 INSERT sales\
	VALUES \
	(1, "2022-01-01", 156),\
    (2, "2022-01-02", 180),\
    (3, "2022-01-03", 21),\
    (4, "2022-01-04", 124),\
    (5, "2022-01-05", 341);
    
 SELECT *\
 FROM sales;
    
2. Задание №2

SELECT \
	id AS "id заказа",\
    IF (count_product < 100, "Маленький заказ",\
		IF(count_product BETWEEN 100 AND 300, "Средний заказ",\
			IF(count_product > 300, "Большой заказ", " " )))\
	 AS "Тип заказа"\
FROM sales;
 
3. Задание №3

CREATE TABLE IF NOT EXISTS orders\
(\
 id INT PRIMARY KEY AUTO_INCREMENT,\
 employee_id VARCHAR(45) NOT NULL,\
 amount VARCHAR(45) NOT NULL,\
 order_status VARCHAR(45) NOT NULL\
 );
 
 SELECT *\
 FROM orders;
 
 INSERT orders\
	VALUES \
	(1, "e03", "15.00", "OPEN"),\
    (2, "e01", "25.50", "OPEN"),\
    (3, "e05", "100.70", "CLOSED"),\
    (4, "e02", "22.18", "OPEN"),\
    (5, "e04", "9.50", "CANSELLED");
    
     SELECT *\
     FROM orders;
     
SELECT \
    id AS "id",\
    employee_id AS "employee_id",\
    amount AS "amount", \
    order_status AS "order_status",\
CASE\
	WHEN order_status = "OPEN" THEN "Order is in open state"\
    WHEN order_status = "CLOSED" THEN "Order is closed"\
    WHEN order_status = "CANSELLED" THEN "Order is canselled"\
END AS "full_order_status"\
FROM orders;
