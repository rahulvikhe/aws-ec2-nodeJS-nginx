**Step 1: Set Up an EC2 Instance**

1.1. Launch an EC2 Instance: Log in to your AWS Console. Go to the EC2 dashboard and click on "Launch Instance." Choose an Ubuntu AMI and configure the instance as needed (e.g., instance type, security groups - allow HTTP, HTTPS & SSH, and key pair).

1.2. Connect to the EC2 Instance: Use SSH to connect to your EC2 instance:

    ssh -i your-key-pair.pem ubuntu@your-ec2-public-ip

**Step 2: Install Node.js**

2.1. Update APT:

    sudo apt update
    sudo apt upgrade

2.2. Install Node.js (i'm using Version 14.16.0):

    curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -
    sudo apt-get install -y nodejs

**Step 3: Set Up Your Website**

3.1. Upload Your Project: You can use Git or any other method to upload your Gatsby project to the EC2 instance.

    git clone https://github.com/username/repository-name.git

3.2. Install Project Dependencies: Inside your project directory, run:

    npm install -g yarn
    yarn

3.3. Install Gatsby:

    npm install -g gatsby-cli

3.4. Build Your Project:

    npm run build

3.5. Install Nginx and Configure It:

    sudo apt-get install nginx
    sudo nano /etc/nginx/sites-available/default

Inside the default configuration file, configure your Nginx server block. For example:

default

        server {
            listen 80;
            server_name your-domain.com www.your-domain.com;
            root /path/to/your/project/public;
            index index.html;
        
            location / {
                try_files $uri $uri/ /index.html;
            }
        }

Save the configuration file and then enable the site and start Nginx:

    sudo ln -s /etc/nginx/sites-available/default /etc/nginx/sites-enabled/
    sudo systemctl enable nginx
    sudo systemctl start nginx

Make sure to replace your-domain.com with your actual domain or IP address and /path/to/your/gatsby-project with the correct path to your Gatsby project's build output.
