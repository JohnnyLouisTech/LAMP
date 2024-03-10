# LAMP
## Deployment of LAMP Stack Application on Amazon Lightsail

Description:
This tutorial showcases the deployment of a LAMP (Linux, Apache, MySQL, PHP) stack application on a singular Amazon Lightsail instance, demonstrating proficiency in cloud infrastructure management and web application deployment. By leveraging the robust capabilities of Lightsail, the project seamlessly integrates the essential components of the LAMP stack, empowering users to establish a scalable and reliable web hosting environment. This hands-on demonstration underscores the ability to configure and optimize cloud-based solutions for efficient and secure application deployment, highlighting expertise in cloud computing and web development methodologies.

The purpose of deploying a LAMP stack application on Amazon Lightsail is to demonstrate proficiency in cloud infrastructure management and web application deployment. By deploying the LAMP stack on Lightsail, the project aims to showcase the ability to create a scalable and reliable hosting environment for web applications. Additionally, it serves as a practical demonstration of configuring and optimizing cloud-based solutions for efficient and secure application deployment, highlighting expertise in cloud computing and web development methodologies. Overall, the project serves as a valuable learning experience and a testament to the individual’s skills in cloud technology and web development.

Step 1: Log in to your AWS account and search for Lightsail.

Step 2: Create an Amazon Lightsail instance
![image](https://github.com/JohnnyLouisTech/LAMP/assets/29494723/0ff1d995-5153-4ff6-bcd6-7a03c6b9f0a9)

Step 3: Choose Change AWS Region and Availability Zone to create your instance in another location.
![image](https://github.com/JohnnyLouisTech/LAMP/assets/29494723/f86476d8-df62-47c7-a4e3-22e410b654b1)

Step 4: Retain Linux/Unix as the platform and under Select a blueprint choose LAMP (PHP 8.1).
![image](https://github.com/JohnnyLouisTech/LAMP/assets/29494723/94674c83-bba3-4dd7-b18f-7bfba1c83b9c)

Step 5: You will need install the application code. Choose +Add launch script button. Copy and paste code in the next screen.

The script performs the following actions:

Removes the default Apache website
Clones the application code from GitHub into the htdocs directory
Ensures the configuration file is writeable
Uses sed to read the local database password from a file on the disk and insert it into the configuration file
Runs an SQL script to set up the application’s database
# remove default website
# — — — — — — — — — — — -
cd /opt/bitnami/apache2/htdocs
rm -rf *

# clone github repo
# — — — — — — — — —
git clone -b loft https://github.com/mikegcoleman/todo-php .

# set write permissions on the settings file
# — — — — — — — — — — — — — — — — — -
sudo chown bitnami:daemon connectvalues.php
chmod 666 connectvalues.php

# inject database password into configuration file
# — — — — — — — — — — — — — — — — — — — — — — — — -
sed -i.bak “s/<password>/$(cat /home/bitnami/bitnami_application_password)/;” /opt/bitnami/apache2/htdocs/connectvalues.php

# create database
# — — — — — — — —
cat /home/bitnami/htdocs/data/init.sql | /opt/bitnami/mariadb/bin/mysql -u root -p$(cat /home/bitnami/bitnami_application_password)
![image](https://github.com/JohnnyLouisTech/LAMP/assets/29494723/0ce95dbc-8f5e-495c-81e4-28e114837a83)

Step 6: Choose the free tier instance plan. You also have 3 months free with your AWS account.
![image](https://github.com/JohnnyLouisTech/LAMP/assets/29494723/f099568e-67f0-4c7d-9997-dbe32e8812b4)

Step 7: Enter a name for your instance and choose Create instance. Keep it unique.
![image](https://github.com/JohnnyLouisTech/LAMP/assets/29494723/b37c52c8-9266-4d55-847a-e8f2b62144be)

Step 8: Test the application
In this section, you access the running application to ensure everything is running properly. Make note of the IP address. The instance is now running, you can copy it yo your web browser.
![image](https://github.com/JohnnyLouisTech/LAMP/assets/29494723/98eefc01-db9f-4890-b3d5-490274d13c1c)

Step 9: You now should be able to view your app on the web by pasting the IP address. You can add tasks, view, and delete as you please.
![image](https://github.com/JohnnyLouisTech/LAMP/assets/29494723/2f122b08-f681-4c78-b923-c2c6b48e3632)

Step 10: Delete the instance for over charge if you don’t plan on using it for a while. On the Instances tab of the Lightsail home page, choose the ellipsis (⋮) icon next to the LAMP instance you just created and choose Delete.
![image](https://github.com/JohnnyLouisTech/LAMP/assets/29494723/c4cf3736-20ee-461e-be9f-e2eebcbc2f44)

Lastly(11): Select Yes, and delete from the prompt.
![image](https://github.com/JohnnyLouisTech/LAMP/assets/29494723/dd9eea6f-269b-4a0a-9cfe-5f541cb8a831)































