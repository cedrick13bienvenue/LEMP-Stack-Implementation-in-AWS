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