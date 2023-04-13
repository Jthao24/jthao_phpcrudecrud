### Section 1 
The purpose of the PHP Crude Crud Application is to demonstrate basic Dynamic HTML Application using PHP. The PHP Crude Crud Application will allow us as users to access the “employee” sample database within the MySQL database, as well as add users to the MySQL database.

### Section 2
In order to create an entirely new application architecture and stack from the “ground up”, there are three general steps in which we need to be mindful of. The first step is to create and use a Virtual Machine that is capable of running the necessary server, language, and database. That said, the second thing we have to do is install the necessary server, language, and database that we plan on using; which is Apache2, PHP, and MariaDB (a distribution of MySQL). The third and final step is to deploy the PHP Crude Crud Application.

### Section 3
Therefore, we have to first start with creating and configuring a Virtual Machine that is capable of running the server Apache2, using the PHP programming language, and the databases of MariaDB which is a distribution of MySQL. That said, the Virtual Machine’s within VirtualBox will have a recommended set of settings of about 2GB (2048MB) of RAM, one single virtual CPU, and a 25GB virtual hard disk.

### Section 4
First and foremost we must know how to create a VirtualBox Virtual Machine. Therefore, here are the steps in which needs to be completed in order to create a VirtualBox Virtual Machine:

1. Click on “new” and make sure that you are on the “Welcome” page if you do not see the “new” button.

2.  Choose an appropriate name for the Virtual Machine and use the .iso OS installer that we downloaded (Ubuntu 20.04); and click on the box that says “Skip Unattended Installation”, after that click next.

3. Configure the Virtual Machine to make sure that it has what you need in terms of hardware, but usually the recommended set of settings for VirtualBox Virtual Machines consists of 2GB (2048MB) of RAM and one single virtual CPU for the machine; which will work just fine. Once done with the configuration, click next.

4. Now we will configure the Virtual Machine for the virtual hard disk which is usually set at a size of 25GB, please note the “Pre-allocate Full Size” box (Do Not Check this box). Once done, click next.

5. Finally a “summary” page will appear, take a look at it and make sure you have it set up the way you want it set up and click the “Finish” button when satisfied. 

### Section 5
Another thing that we need to make sure we have done and downloaded is the correct iso installer; that iso installer is the Ubuntu 20.04. Here are the steps to downloading the correct iso installer: 

1. Go to this web page, https://releases.ubuntu.com/20.04/ 

2. Download the “Server install image” by clicking the link (Don’t download the “Desktop image”).

3. Make sure you place it in a space/spot in which you would like to store the iso file rather than leaving it in the “Downloads” folder.

### Section 6
Now let’s focus on how to install the Apache2 server and the PHP programming language which will be used for the PHP Crude Crud Application. When it comes to installing Apache2 and PHP, it is rather simple and quick; first make sure you are logged into the Ubuntu Virtual Machine in which you wish to use and follow the steps provided below for both Apache2 and PHP:

- To install Apache2 run the following command:
    - sudo apt install apache2

- To install PHP and other various utilities run the following command(s):
    - sudo apt install php
    - sudo apt install libapache2-mod-php
    - sudo apt install php-cli
    - sudo apt install php-mysql
    - sudo apt install php-pgsql
- Another way we can install PHP and the other various utilities is by running the following command:
    - sudo apt install php libapache2-mod-php php-cli php-mysql php-pgsql

One thing that should probably be done after installing PHP is to reboot the server because you could run into some issues or the server can act a little flakey if the server isn’t rebooted. That said, you do not need to reboot the server after installing Apache2.

### Section 7
The last thing that we need to install for the PHP Crude Crud Application is the MariaDB database. Here are the steps:

1. Update the package repos by running this command - sudo apt update
2. Upgrade the Server by running this command - sudo apt upgrade
3. Install the MariaDB by running this command - sudo apt install mariadb-server
4. Verify the MariaDB by running this command - sudo systemctl status mariadb
5. mysql -V
6. Secure the MySQL Installation by running the following - sudo mysql_secure_installation

In regards to the questions asked for in the script. There is no need to update/change the MySQL root user
- Remove anonymous access
- Remove test table
- Do not allow root to access the database remotely

Restart MariaDB so the changes may take effect.

### Section 8
In order for PHP to connect to the database we have to first create and add our own user credentials into the database system because we do not want to continue to use root user all of the time. After adding our new user credentials into the MariaDB mysql database system we will have to create an employees database within the MariaDB mysql database by redirecting (<) the employees.sql file into our mysql database while using our new user credentials. The command used for redirecting the employees.sql file into our mysql database is as follows:
- mysql -u (yourusername) -p -t < employees.sql

This connection data will be stored in the mysql database under Databases, to see this type in the following command:
- show databases; (needs the colon mark after each command when working with MySQL)
	
After that is done, we will have to move or copy the PHP Crude Crud Application file (testdb.php) into the directory that is using the Apache2 server to serve up web files. Run the following command:
- sudo cp testdb.php /var/www/html

This should move the file using the php file into the correct directory that is using the Apache2 server. Another thing to note is that within the php files that we cloned from the phpcrudecrud github repository, there are two lines in all of those php files; one line allows access to the the credentials file that we used to store the credentials that we wish to use, and the second line is the “php object oriented style of creating a mysql connection”.

### Section 9
As for how we are to deploy the PHP Crude Crud Application, we must follow the following steps shown below.
1. We must copy all of the files that we got from the phpcrudecrud github repository into the directory that is using the Apache2 server which is /var/www/html. Run the following command:
    
    a. sudo cp * /var/www/html/
2. Once that is done go ahead and check that everything is there by running the following commands:
    
    a. cd /var/www/html/
    
    b. ls
    
3. Lastly, go and check the browser using the IP address of the Virtual Machine. Make sure that it works and play around with it.

### Section 10
To make sure that the application is running and working correctly, run some system tests, for example run a functionality test and make sure that each feature is working according to the requirements. Another example could be a performance test which will check how the application is running and working while multiple users use the application.
