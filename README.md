# ClientServerArc
Client-Server Architecture Project
CLIENT SERVER ARCHITECTURE USING MYSQL DATABASE MANAGEMENT SYSTEM (DBMS).

Lauch two (2) EC2 instances. First one for the client and second one for the server. Add an inbound rule to the security group of the server instance to allow the client instance to connect to the server instance (allow only the IP address of the client server on MYSQL Default port 3306).

STEP 1: Installing the MySQL Client on server 1

Update the apt package index and install the package.

```sudo apt-get update```
```sudo apt-get install mysql-client```

<img width="567" alt="Screenshot 2022-12-03 at 22 29 55" src="https://user-images.githubusercontent.com/61475969/205464771-0da75698-f3cb-4e2d-b0ce-8eee7cf6772d.png">


STEP 2: Installing the MySQL Server on server 2

Update the apt package index and install the package.
```sudo apt-get update```
```sudo apt-get install mysql-server```

<img width="567" alt="Screenshot 2022-12-03 at 22 30 54" src="https://user-images.githubusercontent.com/61475969/205464801-37072fbd-0e74-4174-9a7e-099cd96b2289.png">


Edit MYSQL configuration file to allow remote access to MySQL server and replace 127.0.0.1 with 0.0.0.0.
```sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf```

<img width="567" alt="Screenshot 2022-12-03 at 22 31 41" src="https://user-images.githubusercontent.com/61475969/205464816-f7cbc520-d72f-4305-bd4d-2c55d0cbd5bb.png">


Restart MySQL server.
```sudo service mysql restart```
Create a new user and database for the project.
```mysql -u root -p```
```CREATE USER 'Eniros'@'%' IDENTIFIED WITH mysql_native_password BY '******';```
```GRANT ALL PRIVILEGES ON *.* TO 'Eniros'@'%' WITH GRANT OPTION;```
```CREATE DATABASE ProjectServArc;```


Update the etc file bind address to the you want for the remote connection or set to 0.0.0.0 for universal

<img width="705" alt="Screenshot 2022-12-01 at 14 52 19" src="https://user-images.githubusercontent.com/61475969/205086191-33c9e948-0203-4160-9e2d-b6f6bb83174e.png">


STEP 3: Connecting to the MySQL Server on server 2 from the client on server 1

Connect to the MySQL server using the following command:
```mysql --host=54.211.139.188  --user=Eniros -p OR mysql -h localhost -u myname -p mydb```


<img width="571" alt="Screenshot 2022-12-01 at 10 24 04" src="https://user-images.githubusercontent.com/61475969/205028718-fcbdea5b-1916-4b38-a4aa-5e77fd1bfde3.png">
