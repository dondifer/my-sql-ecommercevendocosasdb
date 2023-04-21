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



