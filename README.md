# Project: LEMP Stack Implementation on AWS

## Project Overview

This project involves the manual deployment and configuration of a **LEMP Stack** (Linux, NGINX, MySQL, PHP) on a virtualized Amazon EC2 instance. This implementation focuses on using NGINX as a high-performance web server, providing insight into server block configuration, process management with PHP-FPM, and cloud infrastructure security.

---

## Phase 1: Provisioning the Compute Engine (Linux & Nginx)

The foundation of the stack is an EC2 Instance running **Ubuntu 24.04 LTS**. Nginx serves as the web server, designed to handle high concurrency by using an asynchronous, event-driven architecture.

### 1.1 Installation and Service Management

To prepare the environment, synchronize the local package index before installing the Nginx service:

* **Update package list**
```bash
sudo apt update

```


* **Install Nginx**
```bash
sudo apt install nginx

```


* **Verify service status**
```bash
sudo systemctl status nginx

```



> **Expected Output:** The terminal should display a green indicator and the text **"Active: active (running)"**.
> ![Installation and Service Management](screenshoots/1.png)

### 1.2 Networking and Verification

Configure Security Group: Open Port 80 (HTTP) to 0.0.0.0/0 in the AWS EC2 Security Group to allow inbound web traffic.

* **Public IP Access:** Navigate to the following URL in your browser:
```text
http://<YOUR_PUBLIC_IP>:80

```



> **Web Preview:** The **"Welcome to nginx!"** landing page should appear, confirming the server is accessible from the internet.
> ![Networking and Verification](screenshoots/2.png)

---

## Phase 2: Data Persistence Layer (MySQL)

A relational database is required to store application data and manage user records.

### 2.1 Installation

* **Install MySQL Server**
```bash
sudo apt install mysql-server

```


* **Access MySQL Shell**
```bash
sudo mysql

```



> **Expected Output:** The MySQL administrative prompt `mysql>` should appear.
> ![The MySQL administrative prompt](screenshoots/3.png)


### 2.2 Security Hardening

Run the security script to set a root password, remove anonymous users, and disable remote root logins:

```bash
sudo mysql_secure_installation

```

> **Expected Output:** The script should guide you through the configuration and finish with **"Success. All done!"**.
> ![The MySQL administrative prompt](screenshoots/4.png)

---

## Phase 3: Application Layer (PHP)

Unlike Apache, Nginx does not contain a native PHP module. It requires **PHP-FPM** (FastCGI Process Manager) to process PHP scripts and pass them to the web server.

### 3.1 Installation

* **Install PHP-FPM and PHP-MySQL**
```bash
sudo apt install php-fpm php-mysql

```


* **Verify PHP installation**
```bash
php -v

```



> **Expected Output:** PHP version information such as **"PHP 8.3.6"** should be displayed.
> ![PHP version](screenshoots/5.png)

---

## Phase 4: Server Block Configuration and Directory Setup

Nginx uses **Server Blocks** (similar to Virtual Hosts in Apache) to encapsulate configuration details and host multiple domains on a single server.

### 4.1 Custom Web Root Setup

* **Create project directory**
```bash
sudo mkdir /var/www/projectLEMP

```


* **Assign ownership**
```bash
sudo chown -R $USER:$USER /var/www/projectLEMP

```


* **Create Nginx server block configuration**
```bash
sudo nano /etc/nginx/sites-available/projectLEMP

```
>![Web Preview](screenshoots/6.png)


### 4.2 Activation and Testing

* **Link configuration to sites-enabled**
```bash
sudo ln -s /etc/nginx/sites-available/projectLEMP /etc/nginx/sites-enabled/

```


* **Disable default Nginx host**
```bash
sudo unlink /etc/nginx/sites-enabled/default

```


* **Test Nginx configuration syntax**
```bash
sudo nginx -t

```


* **Reload Nginx**
```bash
sudo systemctl reload nginx

```



> **Expected Output:** The syntax check should return **"syntax is ok"** and **"test is successful"**.
>![Web Preview](screenshoots/7.png)

---
