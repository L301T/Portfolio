nstallation and Configuration of GLPI on AWS EC2 Debian
Goal: Install and configure GLPI (open-source ticketing system) on an AWS EC2 instance running Debian.

Steps Performed:

Launched an AWS EC2 t3.micro instance with Debian.
Obtained public IP: 13.61.179.151.
Downloaded PEM key file ender.pem for SSH authentication.
Connected from Windows PowerShell with:
ssh -i C:\Users\YourUsername\Desktop\ender.pem admin@13.61.179.151
(Replace YourUsername and IP address with your own details)
Updated system packages with:
sudo apt update && sudo apt upgrade -y
Installed Apache, MariaDB, PHP and required PHP extensions for GLPI:
sudo apt install apache2 mariadb-server php php-mysql php-curl php-intl php-mbstring php-xml php-gd php-ldap php-imap php-zip php-bcmath -y
Secured MariaDB running:
sudo mysql_secure_installation
(Answer prompts to set root password, remove anonymous users, disallow remote root login, remove test database)
Created GLPI database and user:
sudo mysql -u root -p
Inside MariaDB run:
CREATE DATABASE glpidb;
CREATE USER 'glpiuser'@'localhost' IDENTIFIED BY 'secure_password';
GRANT ALL PRIVILEGES ON glpidb.* TO 'glpiuser'@'localhost';
FLUSH PRIVILEGES;
EXIT;
Downloaded and installed GLPI:
cd /tmp
wget https://github.com/glpi-project/glpi/releases/download/10.0.11/glpi-10.0.11.tgz
tar -xvzf glpi-10.0.11.tgz
sudo mv glpi /var/www/html/
Set correct permissions:
sudo chown -R www-data:www-data /var/www/html/glpi
sudo chmod -R 755 /var/www/html/glpi
Restarted Apache and checked status:
sudo systemctl restart apache2
sudo systemctl status apache2
Apache should be active and running.
Why These Steps:

Update system and install necessary software to prepare the environment.
Secure MariaDB to prevent unauthorized access.
Create dedicated DB and user for GLPI to isolate permissions.
Set proper permissions for Apache to serve GLPI.
Verify Apache is running to confirm the setup.
Next Steps:

Open browser and go to http://13.61.179.151/glpi
Follow the GLPI installation wizard and enter database info.

End of guide.
