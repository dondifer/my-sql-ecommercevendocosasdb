# my-sql-ecommercevendocosasdb

CREATE DATABASE `ecommercevendocosasdb` ;

CREATE TABLE users(
id INT AUTO_INCREMENT,
user_name VARCHAR(100),
birth_date DATE,
PRIMARY KEY(id));

CREATE TABLE orders(
id INT AUTO_INCREMENT,
id_user INT,
order_date DATETIME DEFAULT CURRENT_TIMESTAMP,
PRIMARY KEY(id),
FOREIGN KEY (id_user) REFERENCES users(id));

CREATE TABLE categories(
id INT AUTO_INCREMENT,
nameCat VARCHAR(50),
PRIMARY KEY(id));

CREATE TABLE products(
id INT AUTO_INCREMENT,
id_cat INT,
nameProd VARCHAR(50),
info VARCHAR(200),
price FLOAT,
PRIMARY KEY(id),
FOREIGN KEY (id_cat) REFERENCES categories(id));

CREATE TABLE products_order(
id INT AUTO_INCREMENT,
id_product INT,
id_order INT,
PRIMARY KEY(id),
FOREIGN KEY (id_product) REFERENCES products(id),
FOREIGN KEY (id_order) REFERENCES orders(id));

INSERT INTO users(user_name,birth_date) VALUES ('George','1998-09-07'), ('Jeena','1998-09-07'), ('Anna','1998-09-07'),('Michael','1998-09-07'),('Nadia','1998-09-07')
INSERT INTO categories(nameCat) VALUES ('Eletronica'),('Ropa')
INSERT INTO products(id_cat, nameProd, info,price) VALUES (1, 'Mobil', 'Mobil rechulo',100),
(2, 'Jersey', 'Pal frio',30),
(1, 'PC Gaming', 'full equip',600),(1, 'Batidora', 'Pa cosiná',70),(2, 'Cardigan', 'Elegante funcional',67);
INSERT INTO orders(id_user) VALUES (1),(2),(3),(4),(5);


UPDATE products
SET nameProd = 'Iphone'
WHERE id = 1;

UPDATE products
SET price = 50
WHERE id = 2;

UPDATE products
SET price = 10
WHERE id = 4;

SELECT * FROM products WHERE price > 20;
SELECT * FROM products ORDER BY id DESC;
SELECT
products.nameProd,
products.info,
products.price,
categories.nameCat
FROM products
LEFT JOIN categories ON categories.id = products.id_cat;

SELECT
users.user_name,
users.birth_date,
orders.id_user,
orders.order_date
FROM users
LEFT JOIN orders ON users.id = orders.id_user;


SELECT
products.nameProd,
products.info,
products.price,
categories.nameCat
FROM products
LEFT JOIN categories ON categories.id = products.id_cat WHERE products.id = 5;


SELECT
users.user_name,
users.birth_date,
orders.id_user,
orders.order_date
FROM users
LEFT JOIN orders ON users.id = orders.id_user WHERE users.id = 1;
