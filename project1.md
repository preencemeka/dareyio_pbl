**LAMP STACK IMPLEMENTATION**

STEP 1 - Installing and Updating Ubuntu's package manager using apt

**command: sudo apt update**
![image](https://user-images.githubusercontent.com/72884580/216776920-c995ba28-282e-4ba7-8197-7bf3b7feaef2.png)

**Command: sudo apt install apache2**
![image](https://user-images.githubusercontent.com/72884580/216777150-f37b6231-8ced-455a-aa5d-e35b2691b7a3.png)

**To verify that apache2 is running as a service**
Command: sudo systemctl status apache2
![image](https://user-images.githubusercontent.com/72884580/216777294-fb9153fc-2dba-4d17-9c1b-ab981053d0a4.png)

STEP 2 - Installing and logging into MYSQL
**Logging ito MYSQL**
![image](https://user-images.githubusercontent.com/72884580/216777575-7e5f7613-600f-48ab-9d65-5c6dfa0ce00d.png)

STEP 3 - Installing PHP

Installing php, php-mysql and libapache2-mod-php
**Command: sudo apt install php libapache2-mod-php php-mysql
![image](https://user-images.githubusercontent.com/72884580/216777898-c3bccd78-a333-48c5-bc9b-8674858b8134.png)

Checking the php version
**Command: php -v  
![image](https://user-images.githubusercontent.com/72884580/216777978-77220b6a-e7dc-447a-aeed-3aa12127794c.png)

STEP 4 - Creating a virtual host for the Website using apache
Enabling the virtual host
**Command: sudo a2ensite projectlamp
![image](https://user-images.githubusercontent.com/72884580/216778890-35aa462b-2c6f-4e4d-9be3-5dfebe01b92f.png)

To make sure your configuration file doesn’t contain syntax errors, run:
**Command: sudo apache2ctl configtest

**On the browser, using the IP address
![image](https://user-images.githubusercontent.com/72884580/216779102-29201627-9937-42e4-aefc-f74fd1bb9eaf.png)

STEP 5 - Enable PHP on the website


