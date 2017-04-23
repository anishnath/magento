Install Apache
=======================================

	sudo apt-get -y install apache2
	sudo vim /etc/apache2/sites-available/magento.conf

		<VirtualHost *:80>
		    DocumentRoot /var/www/html
		    <Directory /var/www/html/>
		        Options Indexes FollowSymLinks MultiViews
		        AllowOverride All
		    </Directory>
		</VirtualHost>

Enable magento.conf 
	sudo a2ensite magento.conf
Disable Default 000-default.conf 
	sudo a2dissite 000-default.conf

Installing PHP 7 on Ubuntu 14
=====================================================
Setup the Repo 
	sudo apt-get install -y language-pack-en-base
	sudo LC_ALL=en_US.UTF-8 add-apt-repository ppa:ondrej/php
	sudo apt-get update
	sudo apt-get -y install php7.0

Increasing the PHP memory Limit
sudo vim /etc/php/7.1/apache2/php.ini 
memory_limit = 512M

sudo apt-get -y install php-mbstring php5-mhash php-mcrypt php-curl php-cli php-mysql php-gd libapache2-mod-php php7.0-zip php7.0-intl php7.0-xml

Enable URL Re-write 
sudo a2enmod rewrite
sudo php5enmod mcrypt

Installing Mysql on  on Ubuntu 14
=====================================================
==Mysql 
sudo apt-get install mysql-server-5.6 mysql-client-5.6 mysql-client-core-5.6
mysql -u root -p
CREATE DATABASE magento;
CREATE USER 'magento'@'localhost' IDENTIFIED BY 'magento';
GRANT ALL PRIVILEGES ON * . * TO 'magento'@'localhost';
FLUSH PRIVILEGES;
exit

==Magento Install Goes Here 
Download the Magento CE from the Magento Website 

sudo rsync -avP /tmp/Magento-CE-2/. /var/www/html/
sudo chown -R www-data:www-data /var/www/html/

Restart 
sudo service apache2 restart

Begin the Magento Installation by Typing 
http://<<host>> 