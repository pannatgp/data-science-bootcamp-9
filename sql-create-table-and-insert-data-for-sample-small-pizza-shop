CREATE TABLE menu (
  menu_id INT PRIMARY KEY,
  menu_description VARCHAR(255),
  menu_size VARCHAR(125),
  menu_crust VARCHAR(125),
  menu_price DECIMAL(10,2)
);

CREATE TABLE customer (
  customer_id INT PRIMARY KEY,
  first_name VARCHAR(255),
  last_name VARCHAR(255),
  mobile_number VARCHAR(10),
  facebook_id VARCHAR(255)
);

CREATE TABLE table_number (
  table_id INT PRIMARY KEY,
  room_id INT,
  seat_amount INT
);

CREATE TABLE staff (
  staff_id INT PRIMARY KEY,
  staff_first_name VARCHAR(255),
  staff_last_name VARCHAR(255),
  staff_role VARCHAR(125),
  shift_time VARCHAR(125)
);

CREATE TABLE staff_time (
  duration_id INT PRIMARY KEY,
  staff_id INT,
  clock_in_time TIMESTAMP,
  clock_out_time TIMESTAMP
);

CREATE TABLE orders (
  order_id INT PRIMARY KEY,
  menu_id INT,
  quantity INT,
  table_id INT,
  staff_id INT,
  order_time TIMESTAMP DEFAULT current_timestamp,
  FOREIGN KEY (menu_id) REFERENCES menu(menu_id),
  FOREIGN KEY (table_id) REFERENCES table_number(table_id),
  FOREIGN KEY (staff_id) REFERENCES staff(staff_id)
);

CREATE TABLE billing (
  bill_id INT PRIMARY KEY,
  bill_time TIMESTAMP DEFAULT current_timestamp,
  order_id INT,
  table_id INT,
  total_price DECIMAL(10,2),
  customer_id INT,
  FOREIGN KEY (order_id) REFERENCES orders(order_id),
  FOREIGN KEY (table_id) REFERENCES table_number(table_id),
  FOREIGN KEY (customer_id) REFERENCES customer(customer_id),
  CONSTRAINT composite_key_name PRIMARY KEY (bill_id, order_id)
);

CREATE TABLE reservation (
  reserved_id INT PRIMARY KEY,
  customer_id INT,
  table_id INT,
  reserved_date_time TIMESTAMP,
  order_id INT,
  FOREIGN KEY (table_id) REFERENCES table_number(table_id),
  FOREIGN KEY (order_id) REFERENCES orders(order_id),
  FOREIGN KEY (customer_id) REFERENCES customer(customer_id)
);

-- Inserting data into the menu table
INSERT INTO menu (menu_id, menu_description, menu_size, menu_crust, menu_price) VALUES
(1, 'New Orleans & Sausage Pizza', 'Regular', 'Thin Crust', 300.00),
(2, 'Pepperoni Pizza', 'Small', 'Pan Crust', 320.00),
(3, 'Vegetarian Pizza', 'Large', 'Stuffed Crust', 380.00),
(4, 'Hawaiian Pizza', 'Regular', 'Thin Crust', 380.00),
(5, 'Supreme Pizza', 'Large', 'Pan Crust', 400.50),
(6, 'Mixed Deluxe Pizza', 'Large', 'Stuffed Crust', 420.00),
(7, 'Seafood Deluxe Pizza', 'Medium', 'Pan Crust', 450.00),
(8, 'Bacon & Hokkaido Cheese Large Pizza', 'Large', 'Stuffed Crust', 480.00),
(9, 'Trio Chicken BBQ Pizza', 'Small', 'Thin Crust', 350.00),
(10, 'Trio Chicken BBQ Pizza', 'Medium', 'Pan Crust', 380.00),
(11, 'Trio Chicken BBQ Pizza', 'Large', 'Stuffed Crust', 420.00),
(12, 'Trio Turkey and Chicken Christmas Limited Edition Pizza', 'Large', 'Stuffed Crust', 500.00);

-- Inserting data into the customer table
INSERT INTO customer (customer_id, first_name, last_name, mobile_number, facebook_id) VALUES
(1, 'Srettha', 'Thavisin', '0812345678', 'srettha.thavisin'),
(2, 'Chadchart', 'Sittipunt', '0812345679', 'chadchart.sittipunt'),
(3, 'Prayut', 'Chan-o-cha', '0812345670', 'prayut.chanocha'),
(4, 'Pita', 'Limjaroenrat', '0812345671', 'pita.limjaroenrat'),
(5, 'Paetongtarn', 'Shinawatra', '0812345672', 'paetongtarn.shinawatra'),
(6, 'Lisa', 'Manoban', '0812345675', 'lisa.blackpink'),
(7, 'Gam', 'Wichayanee', '0812345676', 'gam.wichayanee');

-- Inserting data into the table_number table
INSERT INTO table_number (table_id, room_id, seat_amount) VALUES
(1, 101, 4),
(2, 101, 6),
(3, 101, 2),
(4, 101, 2),
(5, 102, 4),
(6, 102, 6),
(7, 102, 2),
(8, 102, 2);

-- Inserting data into the staff table
INSERT INTO staff (staff_id, staff_first_name, staff_last_name, staff_role, shift_time) VALUES
(1, 'Hermione', 'Granger', 'Manager', 'AllDay'),
(2, 'Severus', 'Snape', 'Chef', 'AllDay'),
(3, 'Harry', 'Potter', 'Waiter', 'Morning'),
(4, 'Ron', 'Weasley', 'Waiter', 'Afternoon'),
(5, 'Albus', 'Dumbledore', 'Dish Washer', 'AllDay');

-- Insert data into orders table
INSERT INTO orders (order_id, menu_id, quantity, table_id, staff_id) VALUES
(1, 1, 3, 1, 4),
(2, 2, 1, 1, 4),
(3, 1, 3, 2, 4),
(4, 1, 1, 3, 3);

-- Insert data into billing table
INSERT INTO billing (bill_id, order_id, table_id, total_price, customer_id) VALUES
(1, 1, 1, 900, 1),
(1, 2, 1, 320, 1),
(2, 3, 2, 900, NULL),
(3, 4, 3, 300, 2);

-- Inserting data into the reservation table
INSERT INTO reservation (reserved_id, customer_id, table_id, reserved_date_time, order_id) VALUES
(1, 1, 1, current_timestamp, 1);


--SQL QUERIES--
.mode box
-- FIND CUSTOMER'S NAME THAT SPEND THE LEAST PER BILL AND MENU DETAILS
SELECT C.FIRST_NAME,
       C.LAST_NAME,
       B.TOTAL_PRICE,
       M.*        
FROM BILLING AS B 
  LEFT JOIN CUSTOMER AS C 
  ON B.CUSTOMER_ID = C.CUSTOMER_ID
  LEFT JOIN ORDERS AS O
  ON B.ORDER_ID = O.ORDER_ID
  LEFT JOIN MENU AS M 
  ON O.MENU_ID = M.MENU_ID
WHERE TOTAL_PRICE = (SELECT MIN(TOTAL_PRICE) FROM BILLING);

-- FIND CUSTOMER'S NAME THAT SPEND THE MOST PER BILL AND MENU DETAILS
SELECT C.FIRST_NAME,
       C.LAST_NAME,
       B.TOTAL_PRICE,
       M.*        
FROM BILLING AS B 
  LEFT JOIN CUSTOMER AS C 
  ON B.CUSTOMER_ID = C.CUSTOMER_ID
  LEFT JOIN ORDERS AS O
  ON B.ORDER_ID = O.ORDER_ID
  LEFT JOIN MENU AS M 
  ON O.MENU_ID = M.MENU_ID
WHERE TOTAL_PRICE = (SELECT MAX(TOTAL_PRICE) FROM BILLING);

-- FIND AVERAGE OF TOTAL PRICE PER BILL
WITH SUM_BILL AS
(SELECT SUM(TOTAL_PRICE) AS SUM_BY_BILL
FROM BILLING 
GROUP BY BILL_ID)
SELECT AVG(SUM_BY_BILL)
FROM SUM_BILL;

-- COUNT HOW MANY ORDER ID WITHIN A BILL AND PAID AMOUNT OF EACH CUSTOMER
SELECT B.BILL_ID,
       COUNT(*) AS ORDER_AMOUNT,
       TOTAL_PRICE AS PAID_AMOUNT,
       ('K.'||C.FIRST_NAME||' '||C.LAST_NAME) AS CUSTOMER_NAME
FROM BILLING AS B 
  LEFT JOIN CUSTOMER AS C 
  ON B.CUSTOMER_ID = C.CUSTOMER_ID
GROUP BY BILL_ID;

-- FIND BILLID WHERE CUSTOMERID IS NULL
SELECT BILL_ID
FROM BILLING 
WHERE CUSTOMER_ID IS NULL;



--SQL QUERIES--
.mode box
-- FIND CUSTOMER'S NAME THAT SPEND THE LEAST PER BILL AND MENU DETAILS
SELECT C.FIRST_NAME,
       C.LAST_NAME,
       B.TOTAL_PRICE,
       M.*        
FROM BILLING AS B 
  LEFT JOIN CUSTOMER AS C 
  ON B.CUSTOMER_ID = C.CUSTOMER_ID
  LEFT JOIN ORDERS AS O
  ON B.ORDER_ID = O.ORDER_ID
  LEFT JOIN MENU AS M 
  ON O.MENU_ID = M.MENU_ID
WHERE TOTAL_PRICE = (SELECT MIN(TOTAL_PRICE) FROM BILLING);

-- FIND CUSTOMER'S NAME THAT SPEND THE MOST PER BILL AND MENU DETAILS
SELECT C.FIRST_NAME,
       C.LAST_NAME,
       B.TOTAL_PRICE,
       M.*        
FROM BILLING AS B 
  LEFT JOIN CUSTOMER AS C 
  ON B.CUSTOMER_ID = C.CUSTOMER_ID
  LEFT JOIN ORDERS AS O
  ON B.ORDER_ID = O.ORDER_ID
  LEFT JOIN MENU AS M 
  ON O.MENU_ID = M.MENU_ID
WHERE TOTAL_PRICE = (SELECT MAX(TOTAL_PRICE) FROM BILLING);

-- FIND AVERAGE OF TOTAL PRICE PER BILL
WITH SUM_BILL AS
(SELECT SUM(TOTAL_PRICE) AS SUM_BY_BILL
FROM BILLING 
GROUP BY BILL_ID)
SELECT AVG(SUM_BY_BILL)
FROM SUM_BILL;

-- COUNT HOW MANY ORDER ID WITHIN A BILL AND PAID AMOUNT OF EACH CUSTOMER
SELECT B.BILL_ID,
       COUNT(*) AS ORDER_AMOUNT,
       TOTAL_PRICE AS PAID_AMOUNT,
       ('K.'||C.FIRST_NAME||' '||C.LAST_NAME) AS CUSTOMER_NAME
FROM BILLING AS B 
  LEFT JOIN CUSTOMER AS C 
  ON B.CUSTOMER_ID = C.CUSTOMER_ID
GROUP BY BILL_ID;

-- FIND BILLID WHERE CUSTOMERID IS NULL
SELECT BILL_ID
FROM BILLING 
WHERE CUSTOMER_ID IS NULL;
