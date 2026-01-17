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

