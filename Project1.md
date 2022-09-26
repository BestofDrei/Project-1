# Awesome Documentation of project 1
## Step 1

`sudo apt update`

`sudo apt install apache2`

`sudo systemctl status apache2`
![Apache Status check](./Images/Status-check.PNG)

`curl http://localhost:80`

`curl -s http://169.254.169.254/latest/meta-data/public-ipv4`
![Ip Address](./Images/Public%20ip.PNG)

`http://<Public-IP-Address>:80`
![Internet request](./Images/apache%20default%20page.PNG)



## Step 2
`sudo apt install mysql-server`

`sudo mysql`

`sudo mysql_secure_installation`
![pword installation](./Images/Mysql%20root.PNG)

`sudo mysql -p`
![new login](./Images/mysql%20new%20login.PNG)


`mysql> exit`

## Step 3

`sudo apt install php libapache2-mod-php php-mysql`

`php -v`
![php test](./Images/php%20test.PNG)

## Step 4

`sudo mkdir /var/www/projectlamp`

`sudo chown -R $USER:$USER /var/www/projectlamp`

`sudo vi /etc/apache2/sites-available/projectlamp.conf`

`sudo ls /etc/apache2/sites-available`
![sites available](./Images/project%20lamp%20ls.PNG)

`sudo a2ensite projectlamp`

`sudo a2dissite 000-default`

`sudo apache2ctl configtest`
![configtest](./Images/a2ensite%201.PNG)

`sudo systemctl reload apache2`

`sudo echo 'Hello LAMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectlamp/index.html`
![lamp](./Images/project%20lamp%20ip%20capture.PNG)

`http://<Public-IP-Address>:80`
![lamp ip](./Images/lamp%20ip.PNG)

`http://<Public-DNS-Name>:80`
![lamp dns](./Images/lamp%20dns.PNG)

## Step 5

`sudo vim /etc/apache2/mods-enabled/dir.conf`

: <IfModule mod_dir.c>
        #Change this:

        #DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
        #To this:

        DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
</IfModule>

`sudo systemctl reload apache2`

`vim /var/www/projectlamp/index.php`

> add text:
  *<?php
phpinfo();* 

![debug testing](./Images/Php%20info%20stress%201.PNG)

> When you are finished, save and close the file, refresh the page and you will see a page similar to this

![final output](./Images/Phpinfo%20finally%20working.PNG)


