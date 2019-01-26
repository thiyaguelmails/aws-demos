# Launching a Web Server on EC2 and Accessing Metadata

## Steps:

1. Launch an EC2 Instance running Amazon Linux 2 with the following Userdata
```
#!/bin/bash -ex
yum -y update
yum -y install httpd php mysql php-mysql
chkconfig httpd on
sudo systemctl start httpd
if [ ! -f /var/www/html/lab2-app.tar.gz ]; then
cd /var/www/html
wget https://us-west-2-aws-training.s3.amazonaws.com/awsu-ilt/AWS-100-ESS/v4.2/lab-2-configure-website-datastore/scripts/lab2-app.tar.gz
tar xvfz lab2-app.tar.gz
chown apache:root /var/www/html/rds.conf.php
fi

```
2. Security Groups should allow HTTP