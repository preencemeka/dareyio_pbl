# Installing the Nginx Web Server

sudo apt install nginx
![instll_nginx](https://user-images.githubusercontent.com/72884580/218335292-2e094f2b-23f4-46ef-89ad-3dabe38f40e8.jpg)

#### To verify that nginx is installed
command - sudo systemctl status nginx
![image](https://user-images.githubusercontent.com/72884580/218335483-301acd2a-126b-421b-9aa2-0d2f6e957015.png)

#### To test if the nginx server is working using the browser

Type http://public-ip-address:80 into the browser
![image](https://user-images.githubusercontent.com/72884580/218335633-3ed795b1-cda8-4fef-a111-8a3ec99de8ea.png)


# Installing MYSQL

Command - sudo apt install mysql-server

#### Checking MYSQL version

Command - mysql --version
![image](https://user-images.githubusercontent.com/72884580/218335745-47dcee82-4b79-4fd1-9237-6062fde261b3.png)

# Installing PHP
* php-fpm - Stands for “PHP fastCGI process manager”, and tell Nginx to pass PHP requests to this software for processing.
* php-mysql - a PHP module that allows PHP to communicate with MySQL-based databases

### The above packages will be installed using:
Command - sudo apt install php-fpm php-mysql

# Configuring nginx to use PHP processor

### Create the root web directory for your_domain as follows:
Command - sudo mkdir /var/www/projectLEMP

### Assign the ownership of the directory using the $USER environment variable
Command - sudo chown -R $USER:$USER /var/www/projectLEMP

### Open a new configuration file in Nginx’s sites-available directory using the nano editor
Command - sudo nano /etc/nginx/sites-available/projectLEMP

*This will create an empty file and the config below will be added:


<!--#/etc/nginx/sites-available/projectLEMP

server {
    listen 80;
    server_name projectLEMP www.projectLEMP;
    root /var/www/projectLEMP;

    index index.html index.htm index.php;

    location / {
        try_files $uri $uri/ =404;
    }

    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php8.1-fpm.sock;
     }

    location ~ /\.ht {
        deny all;
    } -->
    
   ### Activate the above config by linking to the config file from mginx's sites-enabled directory
   Command - sudo ln -s /etc/nginx/sites-available/projectLEMP /etc/nginx/sites-enabled/
   
   ### To test the cinfig for syntax error:
   Command - sudo nginx -t
   
   ### To disable default ngnx host currently configured to listen on port 80
   Command - sudo unlink /etc/nginx/sites-enabled/default
   
   ### Nginx is then reloaded to apply changes
   Command - sudo systemctl reload nginx
   
   ### When an index.html is added to the web root /var/www/projectLEMP, the output on a web is:
   ![image](https://user-images.githubusercontent.com/72884580/218337347-eafecbae-19e5-4032-9882-51259a559357.png)
   
   # Testing PHP with NGINX
   ### Creating a new file called info.php
   Command - sudo nano /var/www/projectLEMP/info.php
   The output is:
   ![lemp-php](https://user-images.githubusercontent.com/72884580/218337762-4d07d438-02ba-4d59-911f-3230e030e9fa.jpg)
   
   # Retrieving data from MySQL database with PHP
   
   1. Log into MySQL - sudo mysql
   2. Create a new database using the command - create database `example_database`
   3. Creat a new user using the command - create user 'example_user'@'%' IDENTIFIED WITH mysql_native_password BY 'password';
   4. Grant the user full privileges using the command - GRANT ALL ON example_database.* TO 'example_user'@'%';
   5. Exit mysql and then log in with the newly created user using the command - mysql -u example_user -p
   6. To confirm the newly created database - show databases;
   ![image](https://user-images.githubusercontent.com/72884580/218338293-21974df9-e267-4d49-aac2-8585a01728e4.png)
   7. Creating a todo_list, output is:
   ![todo_list php](https://user-images.githubusercontent.com/72884580/218338342-dc0d2b8a-a970-43bb-9c5b-71a4c43e288e.jpg)
   ![todo_list php](https://user-images.githubusercontent.com/72884580/218338490-900881aa-11b1-4f4e-8a12-594920aab0cf.jpg)




