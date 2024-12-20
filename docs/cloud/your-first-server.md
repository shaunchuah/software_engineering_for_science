# Your First Server

We will do this as an interactive session as the interfaces are different for each provider and they change over time. There are a variety of cloud providers including AWS, Azure and DigitalOcean. Let me know your preference for this. DigitalOcean is beginner-friendly, however the powerful machines are on AWS and Azure.

## Objectives

We are going to:

1. Set up a server on a cloud provider
2. Perform initial server setup
3. Deploy a website on the internet using nginx

## What you will need

- Credit card
- Cloud provider account
- SSH Key from the previous section

## Free tiers

Most cloud providers offer a free tier for new users. This is a great way to get started with cloud computing without incurring any costs. The free tier usually includes a limited amount of resources for a limited time period. For example, AWS offers a free tier for 12 months with limited resources.

## Provisioning a server

We will walk you through the process of provisioning a server on a cloud provider.

1. Sign in to your cloud provider account.
2. Navigate to the dashboard.
3. Click on the `Create Instance` or `Create Server` button.
4. Choose the operating system you want to use. We recommend using Ubuntu as it is the most popular choice.
5. Choose the server size. The free tier usually offers a small server with 1 CPU and 1GB of RAM.
6. Ensure the server location is set to the UK.
7. Choose the SSH key. You can use an existing SSH key or create a new one. We recommend creating a new SSH key for each server.
8. Click on the `Create` button.

## Initial server setup

Once the server is created, you will need to perform some initial setup steps.

### 1. SSH into the server using the command below

```bash
ssh -i ~/.ssh/id_rsa root@<server-ip>
```

Replace `<server-ip>` with the IP address of your server.

### 2. Update the server

```bash
sudo apt update && sudo apt upgrade -y
```

### 3. Install build tools

```bash
sudo apt install -y build-essential python3-venv python3-dev libpq-dev curl nginx
```

### 4. Secure the server

Configure the firewall to only allow SSH connections:

```bash
sudo ufw allow OpenSSH
sudo ufw allow 'Nginx Full'
sudo ufw enable
```

### 5. Deploy a static website

Create a new directory for the website:

```bash
sudo mkdir -p /var/www/html
```

Create a simple HTML file in the /var/www/html directory:

```bash
cd /var/www/html
sudo nano index.html
```

Copy this into the file:

```html title="/var/www/html/index.html"
<html>
    <head>
        <title>Welcome to your first server</title>
    </head>
    <body>
        <h1>Hello, World!</h1>
    </body>
</html>
```

Configure nginx to serve the website:

```bash
sudo ln -s /etc/nginx/sites-available/default /etc/nginx/sites-enabled/default
sudo systemctl restart nginx
```

Set up DNS records to point to the server IP address.

Visit the website and you should see the "Hello, World!" message.

### 6. What next?

Things you can try:

- Set up SFTP and upload files to this server
- Connect VSCode to this remote server and run jupyter notebooks on it
- Deploying more complex web applications
- Set up this machine as a head node for NextFlow

!!! warning
    Remember to shut down your server after this to avoid unnecessary charges.

## Why did we set up a server from scratch?

Going through this exercise is useful because these concepts will be directly applicable when we move onto more advanced topics of containerization and infrastructure as code. Deploying this by hand will help you understand the underlying concepts of how servers work and how to configure them.

This exercise demonstrates the importance of environment management in creating reproducible workflows. In the past, it was common for the issue of "it works on my machine but not yours" to arise.

If you revisit the chapter on setting up python and python environments, you will see that we are essentially dealing with the same problem here, with a slightly different context.

!!! info
    What we did in this tutorial in setting up the server is also known as ClickOps. This is where you manually click through the interfaces to set up the server. The next level to this is to automate the process of deploying servers using Infrastructure as Code (IaC) tools like Terraform and Ansible. If you are setting up more complex cloud infrastructure, you may wish to pick up these technologies.
