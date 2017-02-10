# full-stack-web-developer-nanodegree: liux-web-server
1. For this project was done as a requirements for the Udacity Full Stack Nanodegree. The project involved taking a baseline installation of a Linux distribution on a virtual machine and preparing it to host a previously created web application (Catalog), this required installing updates, securing it from a number of attack vectors and installing/configuring web and database servers.

2. The main technologies used in this project are Python, Flask, Sqlachemy, oauth2 and sqlite.

# Installation and Running

1. IP addreess: 35.163.150.155 ssh port: 2200
2. The hosted application is publically available at: "http://35.163.150.155/catalog/#"
3. Summary of software installed:

	2. Create a new user named grader and grant this user sudo permissions.:
		i. Run "sudo adduser grader" to create grader.
		ii. Run "sudo nano /etc/sudoers.d/grader " to create sudoer file for grader and insert the following "grader ALL=(ALL) NOPASSWD:ALL "

	3. Update all currently installed packages.:
		i. Run "sudo apt-get update"
		ii. Run "sudo apt-get upgrade"
		iii. Run "sudo apt-get install finger".
	4. Configure the local timezone to UTC.
		i. Run "sudo dpkg-reconfigure tzdata"
	 Install the finger package:
		i. Run "sudo apt-get install finger" scroll to the bottom of the Continents list and select "None of the above" in the second list, select "UTC" (Source: http://askubuntu.com/questions/138423/how-do-i-change-my-timezone-to-utc-gmt)
	5. Changed ssh port form 22 to 2200 with the following steps (source: https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)
		i. Run "sudo nano /etc/ssh/sshd_config" and changed "Port 22 " to "Port 2200 ".
		ii. Run "sudo restart ssh"
	6. Configure the Uncomplicated Firewall (UFW) to only allow incoming connections for SSH (port 2200), HTTP (port 80), and NTP (port 123)
		i. Run " sudo ufw status" to check the status of the firewall to ensure its disabled.
		ii. Run "sudo ufw default deny incoming" to deny all incoming connections.
		iii. Run "sudo ufw default allow outgoing" to allow all outgoing connections.
		iv. Run "sudo ufw allow ssh" to enable ssh.
		v. Run "sudo ufw allow 2200/tcp" enable port 2200.
		vi. Run "sudo nano /etc/ssh/sshd_config" and changed "Port 22 " to "Port 2200 " Changed ssh port form 22 to 2200 with the following steps (source: https://help.ubuntu.com/community/SSH/OpenSSH/Configuring). 
		vii. Run "sudo restart ssh"
		viii. Run "sudo ufw allow ntp"
		ix. Run "sudo ufw allow www"
		x. Run "sudo ufw enable" to enable firewal changes.
		xi. Run "sudo ufw status" to confirm changes made.

	7. Install and configure Apache to serve a Python mod_wsgi application.
		i. Run "sudo apt-get install apache2"
		ii. Run "sudo apt-get install libapache2-mod-wsgi"
		iii. Run "sudo nano /etc/apache2/sites-enabled/000-default.conf" edit the configuration. For now, add the following line at the end of the <VirtualHost *:80> block, right before the closing </VirtualHost> line:
	        WSGIDaemonProcess application  python-path=/usr/local/lib/python2.7/site-packages
	        WSGIScriptAlias / /var/www/html/myapp.wsgi
	    <directory /var/www/catalog>
	        WSGIProcessGroup application
	        WSGIApplicationGroup %{GLOBAL}
	        WSGIScriptReloading On
	        Order deny,allow
	        Allow from all
	    </directory>		
		iv. Run "sudo apache2ctl restart".

	8. Install and configure PostgreSQL:
		i. Run "sudo apt-get install postgresql".
		ii. To create a database with a user that have full rights on the database, use the following commands (Source: https://help.ubuntu.com/community/PostgreSQL): "sudo -u postgres createuser -D -A -P catalog" enter a password for the user and  "sudo -u postgres createdb -O catalog catalog"
	
	9. Install git, clone and set up your Catalog App project (from your GitHub repository from earlier in the Nanodegree program) so that it functions correctly when visiting your server’s IP address in a browser. Remember to set this up appropriately so that your .git directory is not publicly accessible via a browser!
		i. Run "sudo apt-get install git" 
		ii. Run "cd /var/www" and run "git clone --depth 1 https://github.com/ricardo-0x07/catalog.git"
		iii. Run "sudo sh /var/www/catalog/pg_config.sh" to install project dependencies.
		iii. Run "sudo nano /var/www/html/myapp.wsgi" to insert the following and save and exit:
		
				import sys
				import site
				import logging

				logging.basicConfig(stream=sys.stderr)

				site.addsitedir('/usr/local/lib/python2.7/site-packages')

				sys.path.insert(0, '/var/www/catalog/')

				from application import app as application
				application.secret_key = 'super_secret_key'
 
4. Contents of the ~/.ssh/udacity_key.rsa:
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEApxXPENf9zhCX4OMZ5EF6baRcASTqVWHJ+82JhsaHGM1Nw0Q4
+gHgbYUTLPGxA2/9LT4mAtukCu/JJ18iF1qqzkM7BfSRWVNfzPcycLfjaR97yFPv
IUYYyn2DSJ+wtdoEbD4P178CmVFLJGFi89z3qMn3KF/fk4dGh4K2mMuBiyzyJ9Wp
qwT40dKlwCrVjyLiwAJfkF2ISs3bwGpAexgDLOLZEVlR3xcx2sHFudJYvU+9BMI/
fUCT5dHXjD6bzjwWmAfjGjm7lnT1BpQYKj1rwqCM5uzp/DlAEmnYEgbjOo7ECZfC
1Dnj5zBrBnlsh53sTlyEftsIiTqz8e9HGawscQIDAQABAoIBAHzKuSDncVTa59S7
SbdFgF8rhtwD6lFi/CzpUnIrDPPlQtM4vSVdCXZDEhNbYM4kcn+8Dz/LNDZG6YJS
d2/h8/iiFg9YnsaMktzPNAkkDuGQ9i6lIdFEPXffTpKLUrw/3VXK9KI6s4I3SVwe
sH1a6E5Uqhipop7ZRkAnzKFKPbLn5eOODl1DI/A3S2HzXe2II6c9OHDklMMZZfXT
1oInyGEhrLNbu9KJB2GOu6F8qoYQ7mV+SnPgLOkCJeJm4oDHtLG0exFp7gfbjvvL
iW4fIf7g+v3LmqHiHDu8qJ0omOqvxM0H6Hbj2rIqCbKGZo8UEKRo8Go5s0lzHfBs
9wgPF5ECgYEA0yGTzaEIVdnc0dqZyRJIglwNt/MrwdDQEqIXelS5TbK9FnYuFg2H
LMl8e/Pzu28jsYySw5O2aRtGu1RtQQDv95KUCTkj+HhMEUePaIg2In3JV45/fWUq
g/mv9ss/OzCcqglU5uD9sCQUmHTH2I4uoQC6CkihNDoj2mMyrnlUaosCgYEAypfy
D1wXMuxv8Nf+9sST09ohDIryW44lp2YyEvVSNNA5JMIT/uMhjSO7awjqyjpCR8+7
li05Pm3Uhl0ytl8JW3PHgbuR58K1ms0K5JgWpBf+Qax98ukfmzNPmo6M9ulek0Vg
rvpjYJq6m3ZkcJHYZgQM2iKXeyF4giJ1rgBa8HMCgYAMzJtOOvXrZnK5khwCkYYt
yPDX9vjvHf6PMp5jvyEgsbY+11lB4v4P3AMc7JQZB8rNJ616B8lmI84s6xhYeXsS
siMhUAJ7PKe34HO0LZXCj4eWNEBMVMa4C3n8ZyPlLbRBpqEsAfW/KODKwUGgQjZX
cljU6MRFC0VDJwJai2ZvswKBgEeBJ5tKOpnrn3rXEZNRQIfGdmGx7OZpnlqeFFBi
q7geQfz6TwpoaiAhm3WkuRHVTC2CYUgZABpLs3YVEOATXP8dNy5P4Kh3LZfMhOq3
z03tdf0B/5Yrt88UZiU76P8A0TOTihNYJpkjI3fZaovcvg8LoOmgyexYnOr5dKWM
VIyHAoGAfF+Ob7C1+j55yos9Oce9QpDHEvQ7pFgpclxDxVQfdE6iblYnGw0svwGJ
LKta8f5LvAZe1p3AZVQSZ8F/pJEUPMKnf8ig4IXcVSedarRROvNpRx5uxaU9Rf43
Tf7+hQHslnnTKiCycx2O1vCk/uBDygL6oBzB9LISE5RV+TYEHM4=
-----END RSA PRIVATE KEY-----

## History

1.

## Credits

1. The udacity nano degree team provided the guidance and training i required to complete this project.


## changelog



#Versioning
 Version 1. 
