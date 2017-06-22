# linux-server-configuration

SERVER DETAILS
IP Address:52.56.33.98
SSH port: 22
URL: ec2-52-56-33-98.eu-west-2.compute.amazonaws.com

LIST OF SOFTWARES INSTALLED
1.Install Apache:
  sudo apt-get install apache2
  Install the libapache2-mod-wsgi package:
  sudo apt-get install libapache2-mod-wsgi
  
2.Install PostgreSQL with:
  sudo apt-get install postgresql postgresql-contrib
  Create a PostgreSQL user called catalog with:
  sudo -u postgres createuser -P catalog
  You are prompted for a password. This creates a normal user that can't create databases, roles (users).
  Create an empty database called catalog with:
  sudo -u postgres createdb -O catalog catalog
  
3.Install Flask, SQLAlchemy, etc
  sudo apt-get install python-psycopg2 python-flask
  sudo apt-get install python-sqlalchemy python-pip
  sudo pip install oauth2client
  sudo pip install requests
  sudo pip install httplib2
  sudo pip install flask-seasurf
  
4.Install Git version control software
  sudo apt-get install git
  
CONFIGURATION CHANGES

1.Add user grader to sudo group
  usermod -aG sudo grader

2.Update all currently installed packages
  apt-get update - to update the package indexes
  apt-get upgrade - to actually upgrade the installed packages
  
3.Set-up SSH keys for user grader
  As root user do:
  mkdir /home/grader/.ssh
  chown grader:grader /home/grader/.ssh
  chmod 700 /home/grader/.ssh
  cp /root/.ssh/authorized_keys /home/grader/.ssh/
  chown grader:grader /home/grader/.ssh/authorized_keys
  
4.Change timezone to UTC
  sudo timedatectl set-timezone UTC
  
5.Configuration Uncomplicated Firewall (UFW)
  By default, block all incoming connections on all ports:
  sudo ufw default deny incoming
  Allow outgoing connection on all ports:
  sudo ufw default allow outgoing
  Allow incoming connection for SSH on port 2200:
  sudo ufw allow 2200/tcp
  Allow incoming connections for HTTP on port 80:
  sudo ufw allow www
  Allow incoming connection for NTP on port 123:
  sudo ufw allow ntp
  To check the rules that have been added before enabling the firewall use:
  sudo ufw show added
  To enable the firewall, use:
  sudo ufw enable
  To check the status of the firewall, use:
  sudo ufw status
  chmod 644 /home/grader/.ssh/authorized_keys
  
6.Clone the repository that contains Project 3 Catalog app
  Move to the /srv directory and clone the repository as the www-data user. The www-data user will be used to run the catalog app.
  cd /srv
  sudo mkdir fullstack-nanodegree-vm
  sudo chown www-data:www-data fullstack-nanodegree-vm/
  sudo -u www-data git clone https://github.com/SteveWooding/fullstack-nanodegree-vm.git fullstack-nanodegree-vm
  
LIST OF THIRD PARTY TOOLS USED TO COMPLETE THIS PROJECT

1.Putty
      Reference: https://en.wikipedia.org/wiki/PuTTY
      Source: http://www.putty.org/ 

2.WinSCP
       Reference: https://en.wikipedia.org/wiki/WinSCP
       Source: https://winscp.net/eng/download.php

