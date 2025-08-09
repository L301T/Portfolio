
# Installation and Configuration of GLPI on AWS EC2 Debian

Goal: Install and configure GLPI (open-source ticketing system) on an AWS EC2 instance running Debian.

Steps Performed:

1. Launched an AWS EC2 t3.micro instance with Debian.  
2. Obtained public IP: 13.61.179.151.  
3. Downloaded PEM key file `ender.pem` for SSH authentication.  
4. Connected from Windows PowerShell with:  
   `ssh -i C:\Users\YourUsername\Desktop\ender.pem admin@13.61.179.151`  
   (Replace `YourUsername` and IP address with your own details)  
5. Updated system packages with:  
   `sudo apt update && sudo apt upgrade -y`  
6. Installed Apache, MariaDB, PHP and required PHP extensions for GLPI:  
   `sudo apt install apache2 mariadb-server php php-mysql php-curl php-intl php-mbstring php-xml php-gd php-ldap php-imap php-zip php-bcmath -y`  
7. Secured MariaDB running:  
   `sudo mysql_secure_installation`  
   (Answer prompts to set root password, remove anonymous users, disallow remote root login, remove test database)  
8. Created GLPI database and user:  
   `sudo mysql -u root -p`  
   Inside MariaDB run:  
   `CREATE DATABASE glpidb;`  
   `CREATE USER 'glpiuser'@'localhost' IDENTIFIED BY 'secure_password';`  
   `GRANT ALL PRIVILEGES ON glpidb.* TO 'glpiuser'@'localhost';`  
   `FLUSH PRIVILEGES;`  
   `EXIT;`  
9. Downloaded and installed GLPI:  
   `cd /tmp`  
   `wget https://github.com/glpi-project/glpi/releases/download/10.0.11/glpi-10.0.11.tgz`  
   `tar -xvzf glpi-10.0.11.tgz`  
   `sudo mv glpi /var/www/html/`  
10. Set correct permissions:  
    `sudo chown -R www-data:www-data /var/www/html/glpi`  
    `sudo chmod -R 755 /var/www/html/glpi`  
11. Restarted Apache and checked status:  
    `sudo systemctl restart apache2`  
    `sudo systemctl status apache2`  
    Apache should be active and running.

Why These Steps:

- Update system and install necessary software to prepare the environment.  
- Secure MariaDB to prevent unauthorized access.  
- Create dedicated DB and user for GLPI to isolate permissions.  
- Set proper permissions for Apache to serve GLPI.  
- Verify Apache is running to confirm the setup.

Next Steps:

Open browser and go to `http://13.61.179.151/glpi`  
Follow the GLPI installation wizard and enter database info.

End of guide.
