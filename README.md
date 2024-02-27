# Aws-EC2-Wordpress-website

**Launch an Ec2 Instance **




**STEP:1** : Install Apache server on Ubuntu:

_**sudo apt install apache2**_

This command uses the apt package manager to install the Apache HTTP server (apache2) on your Ubuntu system. Apache is one of the most widely used web servers, powering a large portion of websites on the internet.

**STEP:2** : Install PHP runtime and PHP MySQL connector:

_**sudo apt install php libapache2-mod-php php-mysql**_

This command installs PHP along with the PHP module for Apache (libapache2-mod-php) and the PHP MySQL extension (php-mysql). PHP is a server-side scripting language commonly used for web development, and the MySQL extension allows PHP to communicate with MySQL databases.

**STEP:3** : Install MySQL server:

_**sudo apt install mysql-server**_

This command installs the MySQL relational database management system (mysql-server) on your Ubuntu system. MySQL is a popular choice for database management and is often used in web development alongside Apache and PHP (commonly referred to as the LAMP stack).

**STEP:4** : Login to MySQL server:

_**sudo mysql -u root**_

This command logs you into the MySQL server as the root user using the MySQL command-line client (mysql). The -u root option specifies that you're logging in as the root user.

**STEP:4** : Change authentication plugin to mysql_native_password (change the password to something strong):

_**ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password by 'Testpassword@123';**_

This SQL command changes the authentication plugin for the root user to mysql_native_password, which is compatible with older authentication methods. It also sets a new password for the root user. This step is crucial for compatibility with certain applications and scripts that expect the older authentication method.

**STEP:5** : Create a new database user for WordPress (change the password to something strong):

_**CREATE USER 'wp_user'@localhost IDENTIFIED BY 'Testpassword@123';**_

This SQL command creates a new MySQL user named 'wp_user' with the specified password. This user will be used by WordPress to access the MySQL database.

**STEP:6** : Create a database for WordPress:

_**CREATE DATABASE wp;**_

This SQL command creates a new MySQL database named 'wp'. WordPress requires its own database to store its data, so this step is necessary before installing WordPress.

**STEP:7** : Grant all privileges on the database 'wp' to the newly created user:

_**GRANT ALL PRIVILEGES ON wp.* TO 'wp_user'@localhost;**_

This SQL command grants all privileges on the 'wp' database to the 'wp_user' MySQL user. This ensures that the user has full access to the WordPress database, which is necessary for WordPress to function properly.

**STEP:8** : Download WordPress:

_**cd /tmp
wget https://wordpress.org/latest.tar.gz**_

These commands change the directory to /tmp and use wget to download the latest version of WordPress from its official website. WordPress is a popular content management system (CMS) used for creating websites and blogs.

**STEP:9** : Unzip:

_**tar -xvf latest.tar.gz**_

This command extracts the contents of the downloaded WordPress file (latest.tar.gz) using the tar utility. After extracting, you'll have a directory named wordpress containing all the WordPress files.

**STEP:10** : Move WordPress folder to Apache document root:

_**sudo mv wordpress/ /var/www/html**_

This command moves the extracted WordPress folder to the Apache document root directory, which is typically /var/www/html. The document root is the directory from which Apache serves files for your website. Placing WordPress here allows Apache to serve WordPress files to visitors of your website.

**STEP:11** : Go to your website and set the details of the database and run the installation of WordPress. This step involves accessing your website through a web browser and following the WordPress installation wizard. During the installation process, you'll need to provide the database details (database name, username, password) created earlier.

**STEP:12** : Edit the Apache configuration file to make the root directory of your website directly serve your WordPress website:

_**cd /etc/apache2/sites-available/
nano [config file]**_

These commands navigate to the directory containing Apache configuration files (/etc/apache2/sites-available/) and open the configuration file for editing using the nano text editor. In the configuration file, you need to change the document root to point to the WordPress directory (/var/www/html/wordpress in this case) so that Apache serves your WordPress website directly from the root URL.

**STEP:13** : Command to restart/reload Apache server:

_**sudo systemctl restart apache2**
OR
**sudo systemctl reload apache2**_

These commands restart or reload the Apache server to apply the changes made in the configuration file. sudo systemctl restart apache2 completely stops and then starts Apache, while sudo systemctl reload apache2 reloads Apache without interrupting active connections.
