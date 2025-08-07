# EC2-Launch-Wizard-Advanced-Details-User-Data-



#!/bin/bash
yum update -y
yum install httpd git -y
systemctl start httpd
systemctl enable httpd
usermod -a -G apache ec2-user
chown -R ec2-user:apache /var/www
chmod 2775 /var/www
find /var/www -type d -exec chmod 2775 {} \;
find /var/www -type f -exec chmod 0664 {} \;
cd /var/www/html
git clone https://github.com/atulkamble/pong-game.git
mv pong-game/* .
rm -rf pong-game
