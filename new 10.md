begin configuration:
sudo su -
yum -y install mariadb-server wget
systemctl enable mariadb-server
systemctl start mariadb-server
yum -y update

set environment variables
DBName=ec2db
DBPassword=admin123456
DBRootPassword=admin123456
DBUser=ec2dbuser

mysql -h demo-rds-database-1.cn62m4e0oq88.us-east-1.rds.amazonaws.com -P 3306 -u rdsuser -p rdsdb < ec2db.sql

mysql -h demo-rds-database-1.cn62m4e0oq88.us-east-1.rds.amazonaws.com -P 3306 -u rdsuser -p

SHOW Databases;
USE rdsdb
SELECT * FROM table1;