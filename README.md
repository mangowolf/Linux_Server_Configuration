#Intro
This repository contains details related to installing, configuring, and viewing the Item Catalog application on Linux Servers found on Amazon Lightsail. It contains the IP Address, URL, summary of software installed, summary of configuration made, and a list of third party resources used to complete the project.

##Details
Public IP Address: 54.208.247.72
URL: http://ec2-54-158-142-39.compute-1.amazonaws.com/

##Summary of Software Installed
- Updated all software preconfigured for a new Ubuntu Linux Server On Amazon Lightsail. (5/3/2017)
- Installed finger_0.17-15_amd64.deb

###Libraries
- apache2
- git
- python-dev
- python-pip
- virtualenv
- Flask
- httplib2
- requests
- oauth2client
- sqlalchemy
- Flask-SQLAlchemy
- python-psycopg2
- postgresql
- postgresql-contrib
- werkzeug==0.8.3
- flask==0.9
- Flask-Login==0.1.3

##Summary of Configurations Made
This section details the configurations made to the Linux server.

###Setup and Login to Amazon Lightsail
	- Created account on Amazon Lightsail
	- Created Linux Server Instance with Ubuntu for the OS
	- Downloaded default key to log into servers through the local terminal
	- SSH into remote server with Ubuntu user

###Setup Grader User
	- Add grader user
	- Grant grader user sudo permission

###SSH Configurations
	- Change port 22 to port 2200 in /etc/ssh/sshd_config file
	- Change PermitRootLogin prohibit-password to PermitRootLogin no to disable root login
	- Temporarily change PasswordAuthentication from no to yes to allow for SSH login setup, turn off after setup.

###SSH Key generation and Upload
	- Generated key pair on local machine
	- Add SSH Port number 2200 to Amazon Lightsail on Networking tab
	- Copy public key to server file .ssh/authorized_keys
	- Testing logging in with key-pair

###Configure Firewall
	- Check firewall inactive status with command sudo ufw status
	- Deny all ufw default incoming and allow default outgoing traffic
	- Allow SSH
	- Allow ports 2200/tcp, 80/tcp, and 123/udp
	- Enable firewall
	- Configure timezone

###Install and Configure Apache to serve Python wsgi app
	- Install Apache libraries
	- Modify /etc/apache2/sites-enabled/000-default.conf file with WSGIScriptAlias / /var/www/html/myapp.wsgi
	- Install python-dev package and verify wsgi is enabled
	- Create and run Hello World app to check installation and configuration works
	- install virtualenv and Flask

##Virtual Host Setup
	- Configure and Enable New Virtual Host in /etc/apache2/sites-available/catalog.conf file
	- Create Catalog.wsgi file and include secret key

###Git
	- Install Git
	- Clone item catalog project from git repository
	- Move files into /var/www/catalog/catalog
	- Make .git inaccessible

###Install Application Dependency Libraries
	- Reference installed Libraries above

###Install and Configure PostgresSQL
	- Install postgresql packages
	- Configure database_setup.py and project.py file
	- Change project.py file to __init__.py
	- Create postgres user catalog and set permissions to schema
	- Run database_setup.py

###Update Google and Facebook OAuth permissions
	- Add host name and IP address to Authorized Javascript origins and update Authorized redirect URIs in Google Developer console.
	- Add host name to Valid OAuth redirect URIs in Facebook Developer Console.

##Third Party Resources
- Udacity.com Forums
- Google Search
- Stackoverflow.com
- Github
- Amazon Lightsail
- Ubuntu
- github.com/jaskanwal96/Linux-Server
- github.com/stueken/FSND-P5_Linux-Server-Configuration