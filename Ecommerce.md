CREATE DATABASE ecommerce_db;
USE ecommerce_db;

CREATE TABLE customers (
    customer_id INT PRIMARY KEY AUTO_INCREMENT,
    customer_name VARCHAR(100) NOT NULL,
    email VARCHAR(100),
    city VARCHAR(50)
);

CREATE TABLE categories (
    category_id INT PRIMARY KEY AUTO_INCREMENT,
    category_name VARCHAR(100) NOT NULL
);

CREATE TABLE products (
    product_id INT PRIMARY KEY AUTO_INCREMENT,
    product_name VARCHAR(100) NOT NULL,
    price DECIMAL(10,2),
    stock INT,
    category_id INT,
    FOREIGN KEY (category_id)
        REFERENCES categories(category_id)
);

CREATE TABLE orders (
    order_id INT PRIMARY KEY AUTO_INCREMENT,
    customer_id INT,
    order_date DATE,
    order_status VARCHAR(30),
    FOREIGN KEY (customer_id)
        REFERENCES customers(customer_id)
);

CREATE TABLE order_items (
    order_item_id INT PRIMARY KEY AUTO_INCREMENT,
    order_id INT,
    product_id INT,
    quantity INT,
    unit_price DECIMAL(10,2),
    FOREIGN KEY (order_id)
        REFERENCES orders(order_id),
    FOREIGN KEY (product_id)
        REFERENCES products(product_id)
);

CREATE TABLE payments (
    payment_id INT PRIMARY KEY AUTO_INCREMENT,
    order_id INT,
    payment_method VARCHAR(30),
    amount DECIMAL(10,2),
    payment_status VARCHAR(30),
    FOREIGN KEY (order_id)
        REFERENCES orders(order_id)
);


-- Insert Data

INSERT INTO customers
(customer_id, customer_name, email, city)
VALUES
(1, 'Rahul Sharma', 'rahul@gmail.com', 'Chennai'),
(2, 'Priya Reddy', 'priya@gmail.com', 'Nellore'),
(3, 'Arjun Kumar', 'arjun@gmail.com', 'Bangalore'),
(4, 'Sneha Rao', 'sneha@gmail.com', 'Hyderabad'),
(5, 'Kiran Patel', 'kiran@gmail.com', 'Mumbai'),
(6, 'Divya Singh', 'divya@gmail.com', 'Chennai'),
(7, 'Vikram Das', 'vikram@gmail.com', 'Kolkata'),
(8, 'Ananya Roy', 'ananya@gmail.com', 'Delhi'),
(9, 'Manoj Verma', 'manoj@gmail.com', 'Pune'),
(10, 'Keerthi Naidu', 'keerthi@gmail.com', 'Nellore');


INSERT INTO categories
(category_id, category_name)
VALUES
(1, 'Electronics'),
(2, 'Clothing'),
(3, 'Home Appliances'),
(4, 'Books'),
(5, 'Footwear');


INSERT INTO products
(product_id, product_name, price, stock, category_id)
VALUES
(1, 'Laptop', 55000.00, 15, 1),
(2, 'Smartphone', 25000.00, 30, 1),
(3, 'Headphones', 2000.00, 50, 1),
(4, 'T-Shirt', 800.00, 100, 2),
(5, 'Jeans', 1800.00, 60, 2),
(6, 'Washing Machine', 22000.00, 10, 3),
(7, 'Mixer Grinder', 3500.00, 25, 3),
(8, 'SQL Programming Book', 700.00, 40, 4),
(9, 'Python Programming Book', 900.00, 35, 4),
(10, 'Running Shoes', 3000.00, 45, 5),
(11, 'Formal Shoes', 2500.00, 20, 5),
(12, 'Bluetooth Speaker', 4000.00, 25, 1);

INSERT INTO orders
(order_id, customer_id, order_date, order_status)
VALUES
(101, 1, '2026-01-05', 'Delivered'),
(102, 2, '2026-01-06', 'Delivered'),
(103, 3, '2026-01-07', 'Shipped'),
(104, 1, '2026-01-10', 'Delivered'),
(105, 4, '2026-01-12', 'Processing'),
(106, 5, '2026-01-15', 'Delivered'),
(107, 6, '2026-01-18', 'Shipped'),
(108, 2, '2026-01-20', 'Delivered'),
(109, 7, '2026-01-22', 'Cancelled'),
(110, 8, '2026-01-25', 'Delivered'),
(111, 3, '2026-02-01', 'Delivered'),
(112, 9, '2026-02-03', 'Processing'),
(113, 10, '2026-02-05', 'Delivered'),
(114, 4, '2026-02-08', 'Delivered'),
(115, 6, '2026-02-10', 'Shipped');

INSERT INTO order_items
(order_item_id, order_id, product_id, quantity, unit_price)
VALUES
(1, 101, 1, 1, 55000.00),
(2, 101, 3, 2, 2000.00),

(3, 102, 2, 1, 25000.00),
(4, 102, 4, 3, 800.00),

(5, 103, 8, 2, 700.00),
(6, 103, 9, 1, 900.00),
(7, 103, 3, 1, 2000.00),

(8, 104, 5, 2, 1800.00),
(9, 104, 10, 1, 3000.00),

(10, 105, 6, 1, 22000.00),
(11, 105, 7, 1, 3500.00),

(12, 106, 11, 2, 2500.00),
(13, 106, 4, 2, 800.00),

(14, 107, 12, 1, 4000.00),
(15, 107, 3, 2, 2000.00),

(16, 108, 1, 1, 55000.00),
(17, 108, 8, 1, 700.00),

(18, 109, 10, 1, 3000.00),

(19, 110, 2, 1, 25000.00),
(20, 110, 11, 1, 2500.00),

(21, 111, 7, 2, 3500.00),
(22, 111, 9, 2, 900.00),

(23, 112, 6, 1, 22000.00),
(24, 112, 5, 1, 1800.00),

(25, 113, 4, 5, 800.00),
(26, 113, 8, 3, 700.00),

(27, 114, 1, 1, 55000.00),
(28, 114, 12, 2, 4000.00),

(29, 115, 2, 1, 25000.00),
(30, 115, 10, 2, 3000.00);


INSERT INTO payments
(payment_id, order_id, payment_method, amount, payment_status)
VALUES
(1, 101, 'UPI', 59000.00, 'Paid'),
(2, 102, 'Credit Card', 27400.00, 'Paid'),
(3, 103, 'UPI', 4300.00, 'Paid'),
(4, 104, 'Debit Card', 6600.00, 'Paid'),
(5, 105, 'UPI', 25500.00, 'Pending'),
(6, 106, 'Cash on Delivery', 6600.00, 'Paid'),
(7, 107, 'Credit Card', 8000.00, 'Paid'),
(8, 108, 'Net Banking', 55700.00, 'Paid'),
(9, 109, 'UPI', 3000.00, 'Failed'),
(10, 110, 'Credit Card', 27500.00, 'Paid'),
(11, 111, 'UPI', 8800.00, 'Paid'),
(12, 112, 'Debit Card', 23800.00, 'Pending'),
(13, 113, 'Cash on Delivery', 6100.00, 'Pending'),
(14, 114, 'Credit Card', 63000.00, 'Paid'),
(15, 115, 'UPI', 31000.00, 'Paid');


-- Display all customers who live in Chennai.
select * from customers where city = "Chennai";

-- Display products whose price is greater than ₹3,000.
select * from products where price > 3000;

-- Find customers who live in either Chennai or Nellore.
select * from customers where city in ("Chennai", "Nellore");

select * from customers where city = "Chennai" or city = "Nellore";

-- Find products priced between ₹1,000 and ₹5,000.
select * from products where price between 1000 and 5000;

-- Find customers whose names start with the letter 'A'.
select * from customers where customer_name like 'A%';

-- Find orders placed during January 2026.
select * from orders where order_date between '2026-01-01' and '2026-01-31';


-- Find products that are not in the Electronics category.
select * from products join categories on products.category_id = categories.category_id
where category_name= "Electronics";


-- Count the total number of customers in each city.
select count(*) as count, city from customers group by city;

-- Find the average price of all products.
select avg(price) as average_price from products;

-- Find the most expensive and least expensive products.
select max(price), min(price) from products;

-- Calculate the total quantity in each category.
select count(*), category_name from products join categories on products.category_id = categories.category_id
 group by category_name;
 
 -- calculate the total quantity of each catogory which is sold
 select count(*), category_id from products as p join order_items
 as oi on p.product_id = oi.product_id
 join orders as o on oi.order_id = o.order_id where order_status = "Delivered"
 group by category_id;
 
 use ecommerce;
select * from order_items;

-- Count the number of orders for each order status.
select count(*), order_status from orders group by order_status;

-- Calculate the total value of each order using its order items.

-- Find products whose total quantity sold is greater than 2.
select sum(quantity) as qty, products.product_name from order_items join products
on order_items.product_id = products.product_id
 group by products.product_name having sum(quantity)>2;

-- Display each customer's name along with their order ID and order date.
select customer_name, order_id, order_date from customers join
 orders on customers.customer_id = orders.customer_id;

-- Display customer names and the number of orders placed by each customer.
select customer_name, count(*) as total_orders from customers join orders on 
customers.customer_id = orders.customer_id group by customers.customer_id;

-- Display product names along with their category names.
select product_name, category_name from products join
 categories on products.category_id = categories.category_id;

-- Display order IDs, customer names, payment methods, and payment statuses.

select customer_name, orders.order_id, payment_method, payment_status from customers join 
orders on customers.customer_id = orders.customer_id
join payments on orders.order_id = payments.order_id;

select * from payments;

-- Display the names of customers who purchased a Laptop.
select customer_name, product_name from customers as c join orders as o
on c.customer_id = o.customer_id
join order_items as oi on oi.order_id = o.order_id
join products as p on p.product_id = oi.product_id
where product_name = 'Laptop';

-- Display the products purchased by Rahul Sharma, including quantity and price.

select product_name, quantity, unit_price, (quantity*unit_price) as total from customers as c join orders as o 
on c.customer_id = o.customer_id join order_items as oi
on o.order_id = oi.order_id join products as p on oi.product_id = p.product_id
where customer_name = 'Rahul Sharma';







-- Display customer names and their order statuses.

-- Display products costing more than ₹5,000 with their category names.

-- Display all orders paid through UPI.
select * from orders join payments on orders.order_id = payments.order_id
where payment_method ="UPI";

-- Display products whose stock is less than 30, along with their categories.
select * from products join categories on products.category_id = categories.category_id
where stock <30;

-- Display the order ID, product name, and quantity for every ordered product.

select o.order_id, product_name, quantity from orders as o
join order_items as oi on o.order_id = oi.order_id
join products as p on oi.product_id = p.product_id;


-- Find products priced between ₹1,000 and ₹4,000.
select * from products where price between 1000 and 4000;

-- Display orders whose payment status is either Paid or Pending.
select * from orders join payments on orders.order_id = payments.order_id
where payment_status= "Paid" or payment_status = "Pending";

-- Display products whose names contain the word 'Programming'.

-- Count the number of products in each category.

-- Display customer names, order IDs, and payment methods.

select customer_name, o.order_id, payment_method from customers as c
join orders as o on c.customer_id = o.customer_id
join payments as p on o.order_id = p.order_id;


-- Display customer names, product names, and quantities purchased.

-- Display product names, category names, and stock quantities for products with stock above 20.

-- Find the total amount paid using each payment method.

-- Display customer names, order IDs, and payment amounts for payments above ₹10,000.

select customer_name, o.order_id, amount from customers as c
join orders as o on c.customer_id = o.customer_id
join payments p on o.order_id = p.order_id
where amount>10000; 


-- Calculate the total spending for each customer.

select customer_name,  sum(quantity*unit_price) as total_amount from orders as o
join order_items as oi on o.order_id = oi.order_id
join products as p on oi.product_id = p.product_id
join customers as c on c.customer_id = o.customer_id
group by c.customer_id;




-- Find customers who purchased products belonging to the Electronics category.

-- Count the number of orders placed by customers in each city.

-- Find the total quantity sold for each category.

select category_name, sum(quantity) as qty from order_items as oi join products as p on
oi.product_id = p.product_id 
join categories as c on p.category_id = c.category_id
 group by c.category_id

