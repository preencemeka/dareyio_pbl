**Implement a Client-Server Architecture**

**Create 2 instance. Name one MYSQL Server and the other MYSQL client.**

**On the client server, install MYSQL client software. Check the version to confirm**
sudo apt install mysql-client -y
mysql --version

**On the MYSQL server, install MYSQL SERVER software**
sudo apt install mysql-server -y

***Configure MySQL server to allow connections from remote hosts***
sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf

Look for bind-address '127.0.0.1' and replace it with 0.0.0.0


**Restart mysql service**
systemctl restart mysql

**Log into the MySQL console as root**
sudo mysql

Set password for user root using mysql native password as default authentication method. 
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'myPassword';

**Exit MySQL**
exit

**Run a recommended security script to remove some insecure settings and restrict access. The script prompts you to:**

Configure validate password plugin
Remove anonymous users?
Disallow root login remotely?
Remove test database and access to it?
Reload privilege tables now?

**Choose No for all except no 2**
sudo mysql_secure_installation



**Try to log in again when you done with the above step using the command below with the "-p" flag. This will prompt for password for root user.**
sudo mysql -p

**If the above is successful then you have successfully set that a password is required to login as a root user. Exit MySQL.**
exit

**On your linux server running the MySQL check which port the mysql server is listening to and open that port on your instance security group.**
netstat -lnp | grep mysql

**Proceed to check if your client-server ip address is allowed to connect remotely to the mysql server**
SELECT host FROM mysql.user WHERE User = 'root';


**shows both the user and the host**
select user, host from mysql.user;
