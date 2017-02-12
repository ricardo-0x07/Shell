# full-stack-web-developer-nanodegree: liux-web-server
1. For this project was done as a requirements for the Udacity Full Stack Nanodegree. The project involved taking a baseline installation of a Linux distribution on a virtual machine and preparing it to host a previously created web application (Catalog), this required installing updates, securing it from a number of attack vectors and installing/configuring web and database servers.

2. The main technologies used in this project are Python, Flask, Sqlachemy, oauth2 and sqlite.

# Installation and Running

1. IP addreess: 35.163.150.155 ssh port: 2200
2. The hosted application is publically available at: "http://35.163.150.155/catalog/#"
3. Summary of software installed:
	1. Remote login of the root user has been disabled.:
		i. Run "sudo nano /etc/ssh/sshd_config" and change "PermitRootLogin without-password" to "PermitRootLogin no" 
	2. Create a new user named grader and grant this user sudo permissions.:
		i. Run "sudo adduser grader" to create grader.
		ii. Run "sudo visudo /etc/sudoers.d/grader " to create sudoer file for grader and insert the following "grader ALL=(ALL) ALL "

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
 
4. Contents of the ~/.ssh/grader_key:
-----BEGIN RSA PRIVATE KEY-----
MIIEowIBAAKCAQEAror0W3+UI/yZ4xDhIpgAwUObTP7wiPvEWTE5YUBTQqT9k8rO
+jLv4U14wCEsUpk2BVOf6KYxdhhDaEPWLF47Gh16EGEsu5LsjRvoirSEh2nFi7+u
hlsVXi5vZ39x4F6UzeKdKvuWdQYh94h0qkByw9Sy8+IrVQgpCbhSaXPGY7RFBcvn
PQVe3fbFdQnFpbKvRiimVRBbHMB0cYe6F5jfOcnZ/WqFqT6IoW/Yab8D6qEOwUrU
ShjMWjyeQQ3GEsS9woXu7txO4Iony+dBlCoGJXNf6PjuFfXlhi4WiPYMoFL49VIW
nOnNASqBLmU9PhIHJ0cz8iHq+Wg5TyMCRBJyswIDAQABAoIBAG4CUoUg4ePUn8FH
sD43g7JLxCRBQqVz2YtFxR6Qhmmox9JQrydu11Yvl/2watkci7nLvSvLI72FCWc7
6k9IjQOmtHqCZMlMjx9ZCbXylN0sQ0ATbhJscglMRxb6cnGx6yPgwqKGs4vKc7oq
HS35NNxMwQWJ9TnAzOy9aePg/pdzyt7HGE+JpsZpMtCZ0yL4j3CjRR9Xo5i6wmDC
YnhSXAzjTc2sY8BzWMS/MHMQYREIxBiaFb/l4YfHA0R0YGDlhDFH2H6YmyDwxaHZ
vXl+aMUWLyk4GuBl619kUsR42PS2wQN8a2hpqT7lOq7hQyzXzbsG0gWX3zdMKWF7
nWzk3eECgYEA0/Qm3aLAjmn1XBjsMKk9NZ6SvP80te10u+TFSPmcQNpn6k7lEN1Q
Va3bHx0TdaKxNkoUy0n1NO89TDGKbYZECa75p9cKFXl7IIC8Y9DFcjoOBIbhVj/h
rjKLZ0ipDHtzvCNnsKMQyEGnHn4HvsmiJdEs7EOYd71X+GXuUEqcsHkCgYEA0tCO
pRXTSKmNqB5SMHFpDXYJhht1g71uL3LPvAFPs7WlOdyLOT6RVpy3CfqYhAvO8QMj
8sBH4ERoTV23mWr8jOoo6x4DE2bDB4Z4bYQnHsysqmHPxjEH3APMnerpeEtZS7SK
0zkRyoYh6VnIz+QpgjKDKZiJMnycEXnzsExFaYsCgYBi0+7jXSXnwaQ0QzKuJdty
ivPkyCJtycCqc6tBsZGX876MVCkeyfLRYHVRdp9CNI/ovnYfq+Z3vi2Yv2jKVNaY
pUunZO9AwBoXN6+f4xKNhmBO4A1lx/eU3+B8UjbwqQd37BJHHGGQ3nvsDdvSq/W9
KGGH8KTBADpqiiyqp3+UEQKBgQCQZvE+nVuTayiwHszXh+eYo+DULpzpN2lxMOig
dBl/FI5vuuTWukfdlw091ZyA3oHKzwbhsdnKAbGcRPSNLx58+6w5mN4sfPhcgDyf
b6VIUJR5RPSIYm9qwmN3TEDN+HbbB3kMRAwuuIAkEi8eT8ArAaScanKX1Ykl424L
tcLaDwKBgE7HcEAafCWm7ajv/MmVicLOHPJGvaRd9Z04j4M2W7PCH/rnNfK2tVCy
WBmLZNNxbHdbsggGWVTwOd8G/7hksAQGOSB2SmNRmi7n1ur/s4MEhLepMJJL8gJs
e1aeVMR+47X9Ke+OLJKSEATOVW7tpUpp9NL63gic9R20f4mENBsR
-----END RSA PRIVATE KEY-----


## History

1.

## Credits

1. The udacity nano degree team provided the guidance and training i required to complete this project.


## changelog



#Versioning
 Version 1. 
