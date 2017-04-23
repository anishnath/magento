##Guide to Install Magento on Ubuntu 14.04 LTS

1. Install Apache
```
bash ~ sudo apt-get -y install apache2
bash ~ sudo vim /etc/apache2/sites-available/magento.conf
		<VirtualHost *:80>
		    DocumentRoot /var/www/html
		    <Directory /var/www/html/>
		        Options Indexes FollowSymLinks MultiViews
		        AllowOverride All
		    </Directory>
		</VirtualHost>
```

2. Enable magento.conf 

```
bash ~ sudo a2ensite magento.conf
```

3. Disable Default 000-default.conf 

```
bash ~ sudo a2dissite 000-default.conf
```

4. Installing PHP 7 on Ubuntu 14
Setup the PHP  Repo 

```
bash ~ sudo apt-get install -y language-pack-en-base
bash ~ sudo LC_ALL=en_US.UTF-8 add-apt-repository ppa:ondrej/php
bash ~ sudo apt-get update
bash ~ sudo apt-get -y install php7.0
```

5. Increasing the PHP memory Limit

```
bash ~ sudo vim /etc/php/7.1/apache2/php.ini 
bash ~ memory_limit = 512M
```

6. Install PHP-extensions Magento Dependency

```
bash ~ sudo apt-get -y install php-mbstring php5-mhash php-mcrypt php-curl php-cli php-mysql php-gd libapache2-mod-php php7.0-zip php7.0-intl php7.0-xml
```

7. Enable URL Re-write 

```
bash ~ sudo a2enmod rewrite
bash ~ sudo php5enmod mcrypt
```

8. Install and Configure Mysql on  on Ubuntu 14.04

```
bash ~ sudo apt-get install mysql-server-5.6 mysql-client-5.6 mysql-client-core-5.6
bash ~ mysql -u root -p
CREATE DATABASE magento;
CREATE USER 'magento'@'localhost' IDENTIFIED BY 'magento';
GRANT ALL PRIVILEGES ON * . * TO 'magento'@'localhost';
FLUSH PRIVILEGES;
exit
```

9. Magento Install Goes Here 
Download the Magento CE from the Magento Website 

```
bash ~ sudo rsync -avP /tmp/Magento-CE-2/. /var/www/html/
bash ~ sudo chown -R www-data:www-data /var/www/html/
```

10. Restart Apache2
```
sudo service apache2 restart
```

11. Begin the Magento Installation by Typing 
###http://<<host>> 
