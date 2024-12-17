
# Personal Blog with WordPress on AWS

Deployed a WordPress blog on an AWS EC2 instance with a database backend


## AWS Services
- EC2
- Mysql
- IAM
- Security Groups
- Elastic IP
## Key Achievements

- Configured LAMP stack on EC2
- secured with IAM and Elastic IP
- integrated Mysql for database scalability.
## Steps

# Step1: Launch an EC2 Instance

1. **Log in to AWS**:
- Open the AWS Management Console and go to **EC2 Dashboard**.

**b. Launch Instance**:

- Click **Launch Instance** and select **Amazon Linux 2** or a pre-configured **WordPress AMI** from AWS Marketplace.

**c. Select Instance Type**:

- Choose **t2.micro** (free tier eligible).

**d Configure Security Group**:

- Allow the following:
    - **SSH (port 22)** for server access.
    - **HTTP (port 80)** for web traffic.
    - **HTTPS (port 443)** for secure traffic.

**e. Create or Select a Key Pair**:

- Download the `.pem` file if creating a new key pair.

**f. Launch the Instance**.

# **Step2:  Connect to the EC2 Instance**

1. **Convert PEM to PPK (if using PuTTY)**:
    - Open **PuTTYgen** > Load the `.pem` file > Save it as `.ppk`.
2. **Use PuTTY or SSH**:
    - For PuTTY:
        - Enter the **public IP** of the instance.
        - Load the `.ppk` file under **Connection > SSH > Auth**.

# Step3: Install Dependencies

1. **Update the Server**: sudo yum update -y
2. Install webserver: sudo apt install apache2
3. **Install Apache, PHP, and MariaDB**:  sudo yum install -y httpd mariadb-server php php-mysqlnd wget
4. Install mysql server for database: sudo apt install mysql-server 

# Step4: Configure the Database

1. **Secure MySQL**: 
sudo mysql_secure_installation
2. **Create a WordPress Database**:
- sudo mysql -u root -p
- CREATE DATABASE wordpress;
- CREATE USER 'wordpressuser'@'localhost' IDENTIFIED BY 'password';
- GRANT ALL PRIVILEGES ON wordpress.* TO 'wordpressuser'@'localhost';

# **Step5: Install WordPress**

1. **Download WordPress**:
- wget https://wordpress.org/latest.tar.gz
- tar -xvzf latest.tar.gz
- sudo mv wordpress /var/www/html/

b. **Configure WordPress**:

- sudo cp /var/www/html/wordpress/wp-config-sample.php /var/www/html/wordpress/wp-config.php
- sudo nano /var/www/html/wordpress/wp-config.php

# **Step6: Access Your WordPress Site**

1. **Find Public IP**:
    - Go to the EC2 dashboard and get the **Public IPv4** of your instance.
2. **Open in Browser**:
    - Visit: `http://<your-public-ip>/wordpress`.
3. **Complete WordPress Setup**:
    - Follow the setup wizard to create your admin account and configure your site.


## Demo

![Alt Text](https://i.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnVwcGNoNWo2cXNybmw0dHBnbHduYXA4YXdkc3duazFlY3E2NGZubSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/LArjwNLraSumR8Yito/giphy.gif)

## Image

![DR Implementation Architecture]()
