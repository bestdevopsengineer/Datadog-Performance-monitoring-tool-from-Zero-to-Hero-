
# What is an Application Performance Management?
collects metrics data from your applications and  this data helps to monitor application insights, so we can:
1-improve performance
2-improve user experience
3-reduce issues and errors


## APM helps to monitor all key aspects of your project
1-Front End
2-Back end
3-Infrastructure

### How is APM monitoring performed?
from our project/service/website APM collect  [metrics/events/logs/traces] or MELT  
with these data to:
1- gain insights from the user perspective
2-quickly spot performance trends at a glance
3-root cause analysis
4-generate alerts on anomalies
5-tracks individual SQL statements
6-monitor key performance indicators such as: response time/ error rate / resource usage / latency
```bash
sudo su -
yum -y install mariadb-server wget
systemctl enable mariadb
systemctl start mariadb
yum -y update
```
### Set Environmental Variables
```bash
DBName=ec2db
DBPassword=admin123456
DBRootPassword=admin123456
DBUser=ec2dbuser
```
### Database Setup on EC2 Instance:
```bash
echo "CREATE DATABASE ${DBName};" >> /tmp/db.setup
echo "CREATE USER '${DBUser}' IDENTIFIED BY '${DBPassword}';" >> /tmp/db.setup
echo "GRANT ALL PRIVILEGES ON *.* TO '${DBUser}'@'%';" >> /tmp/db.setup
echo "FLUSH PRIVILEGES;" >> /tmp/db.setup
mysqladmin -u root password "${DBRootPassword}"
mysql -u root --password="${DBRootPassword}" < /tmp/db.setup
rm /tmp/db.setup
```
### Adding some dummy data to the Database inside EC2 Instance:
```bash
mysql -u root --password="${DBRootPassword}"
USE ec2db;
CREATE TABLE table1 (id INT, name VARCHAR(45));
INSERT INTO table1 VALUES(1, 'Virat'), (2, 'Sachin'), (3, 'Dhoni'), (4, 'ABD');
SELECT * FROM table1;
```
### Migration of Database in EC2 Instance to RDS Database:
```bash
mysqldump -u root -p ec2db > ec2db.sql
mysql -h <replace-rds-end-point-here> -P 3306 -u rdsuser -p rdsdb < ec2db.sql
mysql -h <replace-rds-end-point-here> -P 3306 -u rdsuser -p
SHOW Databases;
USE rdsdb
SELECT * FROM table1;
```


