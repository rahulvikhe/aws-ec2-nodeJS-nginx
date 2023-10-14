# aws-ec2-nodeJS-nginx

Step 1: Set Up an EC2 Instance

1.1. Launch an EC2 Instance:Log in to your AWS Console. Go to the EC2 dashboard and click on "Launch Instance. "Choose an Ubuntu AMI and configure the instance as needed (e.g., instance type, security groups - (Allow HTTP, HTTPS & SSH), and key pair).
01.png

1.2. Connect to the EC2 Instance: Use SSH to connect to your EC2 instance: 
    
    ssh -i your-key-pair.pem ubuntu@your-ec2-public-ip

Step 2: Install Node.js

2.1. Update APT:

    sudo apt update
    sudo apt upgrade

2.2. Install Node.js (Version 14.16.0):

    curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -
    sudo apt-get install -y nodejs

Step 3: Set Up Your Gatsby Website

3.1. Upload Your Gatsby Project: You can use git or any other method to upload your Gatsby project to the EC2 instance.

    git clone https://github.com/rahulvikhe/personal-portfolio-v1.git
    cd personal-portfolio-v1/

3.2. Install Project Dependencies:

Inside your project directory, run:

    npm install -g yarn
    yarn

3.3. Install gatsby:

    npm install -g gatsby-cli

3.4. Build Your Gatsby Project:

    npm run build

