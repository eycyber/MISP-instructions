# General instructions to help you quickly setup and use MISP

## Time required: 30 mins

## Requirements
 - Ubuntu installed system or Virtual Machine (preferred 4 GB ram and 25 GB hdd, 1 demo-ed with 2GB ram and 50 GB hdd)
 - internet connection

## Optional requirements
 - Alternately, take a cloud server for 5 $ per month in Digital Ocean or AWS or Azure (you will get servers for free at least for 2-3 months)
 - Buy a domain for 140 INR which you can use for a year or renew
 - SSL certificate for the domain (free by Let's Encrypt)
 
 
## Preparation 
#### Update and upgrade your Ubuntu OS
```
sudo apt-get update
sudo apt-get upgrade
```
#### Install dependencies
```
sudo apt install haveged -qy
sudo service haveged start
```

## Check compatibility
```
wget -O /tmp/INSTALL.sh https://raw.githubusercontent.com/MISP/MISP/2.4/INSTALL/INSTALL.sh
bash /tmp/INSTALL.sh
```

## Install MISP Core
```
wget -O /tmp/INSTALL.sh https://raw.githubusercontent.com/MISP/MISP/2.4/INSTALL/INSTALL.sh
bash /tmp/INSTALL.sh -c
```

#### (Optional) Put SSL (Let's Encrypt)
```
sudo add-apt-repository ppa:certbot/certbot
sudo apt install python-certbot-apache
 
(Optional) In case you have your domain, open the virtual host file for your domain using nano or your favorite text editor:

sudo nano /etc/apache2/sites-available/your_domain.conf
ServerName <enter_your_domain>;

sudo apache2ctl configtest
sudo systemctl reload apache2

(Optional) Incase, you have firewall allow http/https through firewall

Get ssl certificate for your domain (or IP address if there is no domain)
sudo certbot --apache -d <your_domain_or_ip>

(Optional) To renew certificate, required only after 2-3 months, but you can still check for it now

sudo certbot renew --dry-run
```