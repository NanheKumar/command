# Restart Apache 2 web server, enter:
# /etc/init.d/apache2 restart
OR
$ sudo /etc/init.d/apache2 restart
OR
$ sudo service apache2 restart

#To stop Apache 2 web server, enter:
# /etc/init.d/apache2 stop 
OR
$ sudo /etc/init.d/apache2 stop
OR
$ sudo service apache2 stop

#To start Apache 2 web server, enter:
# /etc/init.d/apache2 start
OR
$ sudo /etc/init.d/apache2 start
OR
$ sudo service apache2 start

A note about Debian/Ubuntu Linux systemd users

Use the following systemctl command on Debian Linux version 8.x+ or Ubuntu Linux version Ubuntu 15.04+ or above:
## Start command ##
systemctl start apache2.service
## Stop command ##
systemctl stop apache2.service
## Restart command ##
systemctl restart apache2.service

CentOS/RHEL (Red Hat) Linux version 4.x/5.x/6.x or older specific commands

## Start ##
service httpd start
## Stop ##
service httpd stop
## Restart ##
service httpd restart

CentOS/RHEL (Red Hat) Linux version 7.x or newer specific commands

Most modern distro now using systemd, so you need to use the following command:
## Start command ##
systemctl start httpd.service
## Stop command ##
systemctl stop httpd.service
## Restart command ##
systemctl restart httpd.service

Generic method to start/stop/restart Apache on a Linux/Unix

The syntax is as follows (must be run as root user):
## stop it ##
apachectl -k stop
## restart it ##
apachectl -k restart
## graceful restart it ##
apachectl -k graceful
## Start it ##
apachectl -f /path/to/your/httpd.conf
apachectl -f /usr/local/apache2/conf/httpd.conf


# Where are the Apache and PHP log fiiles:
By default, /var/log/apache2/error.log

This can be configured in /etc/php5/apache2/php.ini.

# Empty log file using echo command
echo "" > /var/log/apache2/error.log
This is the same as

echo  > /var/log/apache2/error.log

# How To Check Ubuntu Version and Other System Information

lsb_release -a

cat /etc/lsb-release

cat /etc/issue

# Slow Query Mysql
SELECT @@global.slow_query_log

To enable the slow query log in MySQL, follow these steps:

Log in to your server using SSH.

mysql -u root -p

SET GLOBAL slow_query_log = 'ON';

There are additional options that you can set for the slow query log:


By default, when the slow query log is enabled, it logs any query that takes longer than 10 seconds to run. To change this interval, type the following command, replacing X with the time in seconds:

SET GLOBAL long_query_time = X;

By default, the slow query log file is located at /var/lib/mysql/hostname-slow.log. To change the log path or filename, type the following command, replacing path with the path to the file, and filename with the name of the log filename:


SET GLOBAL slow_query_log_file = '/path/filename';

To verify that the slow query log is working correctly, log out of the mysql program, and then log back in. (This reloads the session variables for the mysql program.) Type the following command, replacing X with a value that is greater than the long_query_time setting:


SELECT SLEEP(X);

The slow query log file should contain information about the query.


Continue to monitor the slow query log file to see which queries take a long time to run.


When you are done troubleshooting, disable the slow query log. To do this, run the mysql program again, and then type the following command:


SET GLOBAL slow_query_log = 'OFF';

# Check used space on ubuntu

df -h

How to set timezone in ubuntu

List timezone

timedatectl

Set timezone

timedatectl set-timezone Asia/Kolkata

