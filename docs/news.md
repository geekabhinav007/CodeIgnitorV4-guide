[Home](./index.html){: .btn .fs-10 .mr-4}
# Databse Conectetivity

- Check that the database connectivity is done or not.
- check for phpmyadmin else on terminal 
 ```shell
 sudo mysql
 ```
 - Create a user name "Let say" `ci` with password `abc`.
 
 ```sql
 sudo mysql
 
 CREATE USER 'ci'@'localhost' IDENTIFIED BY 'abc';
 
 GRANT ALL ON *.* TO 'ci'@'localhost' WITH GRANT OPTION;
 ```
 - Create database and create table by following query:
 
 ```sql
 
 CREATE DATABASE ci;
 
 use ci;
 
 CREATE TABLE news (
    id INT UNSIGNED NOT NULL AUTO_INCREMENT,
    title VARCHAR(128) NOT NULL,
    slug VARCHAR(128) NOT NULL,
    body TEXT NOT NULL,
    PRIMARY KEY (id),
    KEY slug (slug)
);

INSERT INTO news VALUES
(1,'Elvis sighted','elvis-sighted','Elvis was sighted at the Podunk internet cafe. It looked like he was writing a CodeIgniter app.'),
(2,'Say it isn\'t so!','say-it-isnt-so','Scientists conclude that some programmers have a sense of humor.'),
(3,'Caffeination, Yes!','caffeination-yes','World\'s largest coffee shop open onsite nested coffee shop for staff only.');
 
```

- Now add following data in `.env` file under ci folder.
```shell
database.default.hostname = localhost
database.default.database = ci
database.default.username = ci
database.default.password = abc
database.default.DBDriver = MySQLi
```
-
