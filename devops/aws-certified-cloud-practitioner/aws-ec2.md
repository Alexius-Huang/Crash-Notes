---
description: Instance of AWS Serve
---

# AWS EC2

## Creating SSH Keys

Enter the "Network and Security" section, then enter the "Key Pairs" part.

Create an SSH keypair, option "pem" for Linux or MacOS.

## Connecting Instance

### Use SSH Client

After the instance is created, copy the public IP address.

 Use the SSH client:

```text
ssh -i <ec2-key-name>.pem ec2-user@<ip-address>
```

### Use Browser

Entering the AWS Management Console page - ES2 section. Select an instance and connect by clicking the option "EC2 Instance Connect \(browser-based SSH connection\)".

## Creating a Website

### Install Nginx

```text
# switch to root user
$ sudo su -

# install nginx
$ yum install nginx

# installation via linux's recommendation
$ amazon-linux-extras install nginx1.12
```

### Check the Status of Nginx

```text
# Use system control to check
$ systemctl status nginx

# Start up the Nginx
$ systemctl start nginx

# Check the network status of nginx
$ netstat -ntlp
```

### Add Inbound Rule

Go to the AWS Management Console, target specific instance's security group, and create a new inbound rule:

* TCP protocol
* Port 80
* Source 0.0.0.0/0

After that, you can successfully enter the URL in the browser via IP address.

### Modify the Page

Enter the directory where Nginx works:

```text
cd /usr/share/nginx/html
```

In this directory, you can modify the `index.html` page to change the webpage outlook.

