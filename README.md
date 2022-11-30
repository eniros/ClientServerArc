# ClientServerArc
Client-Server Architecture Project
CLIENT SERVER ARCHITECTURE USING MYSQL DATABASE MANAGEMENT SYSTEM (DBMS).

Lauch two (2) EC2 instances. First one for the client and second one for the server. Add an inbound rule to the security group of the server instance to allow the client instance to connect to the server instance (allow only the IP address of the client server on MYSQL Default port 3306).

STEP 1: Installing the MySQL Client on server 1

Update the apt package index and install the package.

sudo apt-get update
sudo apt-get install mysql-client

<img width="557" alt="Screenshot 2022-11-30 at 19 19 53" src="https://user-images.githubusercontent.com/61475969/204890026-a8398f2e-80cd-4d81-9c96-9a2d81f589ff.png">

STEP 2: Installing the MySQL Server on server 2

Update the apt package index and install the package.
sudo apt-get update
sudo apt-get install mysql-server

<img width="557" alt="Screenshot 2022-11-30 at 19 20 59" src="https://user-images.githubusercontent.com/61475969/204890237-5a9a0c56-3312-4ae2-b084-d7c4b4f78bf7.png">

Edit MYSQL configuration file to allow remote access to MySQL server and replace 127.0.0.1 with 0.0.0.0.
sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf

<img width="557" alt="Screenshot 2022-11-30 at 19 46 49" src="https://user-images.githubusercontent.com/61475969/204894078-60c5d1dd-ddaa-40c4-9a50-560d1ed66cc6.png">

Restart MySQL server.
sudo service mysql restart
Create a new user and database for the project.
mysql -u root -p
CREATE USER 'Eniros'@'%' IDENTIFIED WITH mysql_native_password BY '******';
GRANT ALL PRIVILEGES ON *.* TO 'Eniros'@'%' WITH GRANT OPTION;
CREATE DATABASE ProjectServArc;

STEP 3: Connecting to the MySQL Server on server 2 from the client on server 1

Connect to the MySQL server using the following command:
mysql --host=54.211.139.188  --user=Eniros -p OR mysql -h localhost -u myname -p mydb
