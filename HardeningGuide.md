1. Log in credentials: `root : changeme`
                       `sysadmin : changeme`
2. localhost - check webpage

3. Change root password

4. Change sysadmin password

5. Change accounts to no login: usermod -s /sbin/nologin [username]

6. backup /var/www/html to /opt/html.BAK.1 using cp -R

7. change mysql password on whatever machine is hosting mysql: `mysqladmin -u root password "[new password]"
                                                              `mysql -u root-p mysql
                                                              `update user set password=PASSWORD("[new password]") where user='root';
                                                              flush privileges;
8. fix yum repos. These have been changed to vault instead of release. Script should be in the SCSU CCDC github

9. Change firewall rules, basic script is located in SCSU github as well. (`sudo firewall-cmd --list-all` will list all firewall rules to double check them)

10. configure apache server, /etc/httpd/conf/httpd.conf is userful. Look at Apache and MySQL checklist.
 Basically, you add an apache group and an apache user, apache user has no login. `sudo useradd -r -s /sbin/nologin -g apache_group apache_user` . Then you change the ownership of the /www/ folder to the apache user and apache group
  `sudo chown -R apache_user:apache_group /path/to/your/document/root`

11. sudo yum update ca-certificates to update certs
