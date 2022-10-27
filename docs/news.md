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
 
 CREATE USER ‘ci’@’localhost’ IDENTIFIED BY ‘abc’;
 
 GRANT ALL ON *.* TO 'ci'@'localhost' WITH GRANT OPTION;
 ```
 
