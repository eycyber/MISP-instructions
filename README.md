

# update and upgrade
sudo apt-get update
sudo apt-get upgrade

# Check
wget -O /tmp/INSTALL.sh https://raw.githubusercontent.com/MISP/MISP/2.4/INSTALL/INSTALL.sh
bash /tmp/INSTALL.sh

# This will install MISP Core
wget -O /tmp/INSTALL.sh https://raw.githubusercontent.com/MISP/MISP/2.4/INSTALL/INSTALL.sh
bash /tmp/INSTALL.sh -c


#If installation is stuck

sudo apt install haveged -qy
sudo service haveged start


#Put SSL (Let's encrypt)
sudo add-apt-repository ppa:certbot/certbot
sudo apt install python-certbot-apache

To check, open the virtual host file for your domain using nano or your favorite text editor:

sudo nano /etc/apache2/sites-available/your_domain.conf
ServerName your_domain;


sudo apache2ctl configtest
sudo systemctl reload apache2

#Allow https through firewall

sudo certbot --apache -d your_domain -d www.your_domain

#renew

sudo certbot renew --dry-run



#Change password

sudo /var/www/MISP/app/Console/cake Password admin@admin.test Password1234
