# full-stack-web-developer-nanodegree: liux-web-server
1. For this project was done as a requirements for the Udacity Full Stack Nanodegree. The project involved taking a baseline installation of a Linux distribution on a virtual machine and preparing it to host a previously created web application (Catalog), this required installing updates, securing it from a number of attack vectors and installing/configuring web and database servers.

2. The main technologies used in this project are Python, Flask, Sqlachemy, oauth2 and sqlite.

3. Skills gained: 
  a. developed a deep understanding of exactly what web applications are doing, how they are hosted, and the interactions between multiple systems. 
  b. turning a brand-new, bare bones, Linux server into the secure and efficient web application host your applications need.
  c. to install and configure a web and database server and actually host a web application.


# Installation and Running

1. IP addreess: 35.163.150.155 ssh port: 2200
2. The hosted application is publically available at: "http://35.163.150.155/catalog/#"
3. Summary of software installed:
	- finger
	- apache2
	- libapache2-mod-wsgi
	- postgresql
	- git
	- python-pip
	- flask
	- and all those listed in the "/var/www/catalog/pg_config.sh" file by running: 'sudo sh /var/www/catalog/pg_config.sh'
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


## License
MIT License

Copyright (c) 2017 Clive Cadogan

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.


## changelog



#Versioning
 Version 1. 
