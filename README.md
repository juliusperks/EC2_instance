# EC2_instance

https://roadmap.sh/projects/ec2-instance

1) Login or create a free AWS account
2) Set your region
3) Open EC2 -> Instances -> Launch Instance

Instance settings
- Name: static-web-server
- AMI: Ubuntu Server
- Instance type: t2.micro
- Key pair: Create new and download the .pem file
- Auto-assign public ip: enabled
- Securty group inbound rules:
    - SSH Source: My IP
    - HTTP: Anywhere (0.0.0.0/0)

4) Click Launch Instance
5) In Instances, select the instance and copy the Public IPv4 address

Use WSL or a linux operating system
6) Copy the .pem into your .ssh directory
7) chmod 400 <keyname>.pem
8) ssh -i <keyname>.pem ubuntu@PUBLIC_IP
9) 
sudo apt update
sudo apt upgrade -y
sudo apt install nginx -y
sudo systemctl enable --now nginx
10) curl -I http://localhost
11) Deploy a simple static website
sudo tee /var/www/html/index.html > /dev/null <<'HTML'
<!doctype html>
<html>
  <head>
    <meta charset="utf-8" />
    <title>EC2 Static Site</title>
  </head>
  <body>
    <h1>Hello from AWS EC2!</h1>
    <p>Deployed with Ubuntu + Nginx.</p>
  </body>
</html>
HTML
12) access the website from your computer
http://PUBLIC_IP
