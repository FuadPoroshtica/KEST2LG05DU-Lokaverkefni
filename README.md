# Linux-Lokaverkefni
Linux Lokaverkefni með Debian 10

[Diary](https://github.com/AtliOskarsson/Linux-Lokaverkefni/wiki)

## Configured private ip

added lines 10 to 21 <br/>
https://github.com/AtliOskarsson/Linux-Lokaverkefni/blob/master/etc/network/interfaces

## Configured FQDN
Edited /etc/hostname to server1.atli.local <br/>
Added 127.0.0.1 to /etc/hosts <br/>
![alt text](https://github.com/AtliOskarsson/Linux-Lokaverkefni/blob/master/Photos/hostname-domainname.PNG)

## Configured dhcp

changed lines 34 to 43 <br/>
https://github.com/AtliOskarsson/Linux-Lokaverkefni/blob/master/etc/dhcp/dhcpd.conf

![alt text](https://raw.githubusercontent.com/AtliOskarsson/Linux-Lokaverkefni/master/Photos/ip.PNG)

## DNS 

apt-get install bind9 bind9utils bind9-doc


https://github.com/AtliOskarsson/Linux-Lokaverkefni/blob/master/etc/bind/named.conf.local <br/>
Added both zones <br/>
https://github.com/AtliOskarsson/Linux-Lokaverkefni/blob/master/etc/bind/named.conf.options <br/>
Changed line 5, 13 and 16 <br/>
https://github.com/AtliOskarsson/Linux-Lokaverkefni/blob/master/etc/bind/zones/db.100.168.192 <br/>
Changed line 5, 13 and 16 <br/>
https://github.com/AtliOskarsson/Linux-Lokaverkefni/blob/master/etc/bind/zones/db.atli.local <br/>
![alt text](https://github.com/AtliOskarsson/Linux-Lokaverkefni/blob/master/Photos/pingserver1.PNG)

## Users

![alt text](https://github.com/AtliOskarsson/Linux-Lokaverkefni/blob/master/Photos/usersLogin.PNG)

Each user has a home directory <br/>
![alt text](https://github.com/AtliOskarsson/Linux-Lokaverkefni/blob/master/Photos/userDirectory.PNG)

## Samba share

samba configurations file <br/>
https://github.com/AtliOskarsson/Linux-Lokaverkefni/blob/master/etc/samba/smb.conf

## ssh protocol
apt-get install openssh-server
apt-get install openssh-client
systemctl status ssh

Only added AllowGroups sameign so only the users in the group sameign can use ssh <br/>
https://github.com/AtliOskarsson/Linux-Lokaverkefni/blob/master/etc/ssh/sshd_config

![alt text](https://github.com/AtliOskarsson/Linux-Lokaverkefni/blob/master/Photos/ssh.PNG)

## Apache2 with SSL Certification

I used the command below to create a key for the ssl certification
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/apache-selfsigned.key -out /etc/ssl/certs/apache-selfsigned.crt

Added line 17 to <br/>
https://github.com/AtliOskarsson/Linux-Lokaverkefni/blob/master/etc/bind/zones/db.atli.local


https://github.com/AtliOskarsson/Linux-Lokaverkefni/blob/master/etc/apache2/conf-available/ssl-params.conf <br/>
https://github.com/AtliOskarsson/Linux-Lokaverkefni/blob/master/etc/apache2/sites-available/000-default.conf <br/>
https://github.com/AtliOskarsson/Linux-Lokaverkefni/blob/master/etc/apache2/sites-available/default-ssl.conf <br/>

![alt text](https://github.com/AtliOskarsson/Linux-Lokaverkefni/blob/master/Photos/siteSsl.PNG)

## MySQL and phpmyadmin

apt install apache2 php php-json php-mbstring php-zip php-gd php-xml php-curl php-mysql <br/>
wget https://files.phpmyadmin.net/phpMyAdmin/4.9.0.1/phpMyAdmin-4.9.0.1-all-languages.zip <br/>
unzip phpMyAdmin-4.9.0.1-all-languages.zip -d /opt <br/>
mv -v /opt/phpMyAdmin-4.9.0.1-all-languages /opt/phpMyAdmin <br/>
chown -Rfv www-data:www-data /opt/phpMyAdmin <br/>


![alt text](https://github.com/AtliOskarsson/Linux-Lokaverkefni/blob/master/Photos/mysql.PNG)

![alt text](https://github.com/AtliOskarsson/Linux-Lokaverkefni/blob/master/Photos/phpmyadmin.PNG)


## PurFTPd
apt install pure-ftpd
echo "yes" > /etc/pure-ftpd/conf/Daemonize <br/>
echo "yes" > /etc/pure-ftpd/conf/NoAnonymous <br/>
echo "yes" > /etc/pure-ftpd/conf/ChrootEveryone <br/>
echo "yes" > /etc/pure-ftpd/conf/IPV4Only <br/>
systemctl restart pure-ftpd <br/>
apt install gftp # to test ftp out <br/>

![alt text](https://github.com/AtliOskarsson/Linux-Lokaverkefni/blob/master/Photos/ftp.PNG)

## Quota 
apt install quota
quotacheck -ugm / # Creates files /aquota.user and /aquota.group (contain info about the limits)
quotaon -v / # turn on the quota system

Added usrquota,grpquota to line 9
https://github.com/AtliOskarsson/Linux-Lokaverkefni/blob/master/etc/fstab

![alt text](https://github.com/AtliOskarsson/Linux-Lokaverkefni/blob/master/Photos/quota.PNG)

## squirrelmail

I was able to get the squirrelMail up but did not have time to get users to work

![alt text](https://github.com/AtliOskarsson/Linux-Lokaverkefni/blob/master/Photos/squirrelmail.PNG)



