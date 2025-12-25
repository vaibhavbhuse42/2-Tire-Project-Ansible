# Deployment of 2-Tier Application using Ansible

## 📌 Project Overview

This project demonstrates **deployment of a 2-tier web application** using a **single Ansible playbook**.

* **App Tier (Web Server)**: Nginx + PHP + PHP-FPM
* **DB Tier (Database Server)**: MariaDB

The setup is automated using Ansible on Amazon Linux servers.

---

## 🏗️ Architecture Diagram

![](/img/Ansible_logo.svg_.avif)

```
                ┌───────────────┐
                │   Client /     │
                │   Browser      │
                └───────┬───────┘
                        │ HTTP
                ┌───────▼───────┐
                │   App Server   │
                │  (Nginx + PHP) │
                │  EC2 Instance  │
                └───────┬───────┘
                        │ MySQL
                ┌───────▼───────┐
                │   DB Server    │
                │   (MariaDB)    │
                │  EC2 Instance  │
                └───────────────┘
```

---

## 🧰 Technology Stack

* **Configuration Management**: Ansible
* **Web Server**: Nginx
* **Backend Language**: PHP
* **Database**: MariaDB
* **OS**: Amazon Linux
* **Cloud**: AWS EC2

---

## 📂 Inventory File

```ini
[appserver]
172.31.6.81 ansible_user=ec2-user ansible_ssh_private_key_file=/home/ec2-user/ansible.pem

[dbserver]
172.31.4.64 ansible_user=ec2-user ansible_ssh_private_key_file=/home/ec2-user/ansible.pem
```

---

## ▶️ Ansible Playbook Description

### App Server Tasks

* Install Nginx, PHP, PHP-FPM
* Start & enable services
* Deploy `index.php` file using Ansible copy module

### DB Server Tasks

* Install MariaDB server
* Start & enable MariaDB service
* Create database using MySQL shell command

---

## 🧪 Verification Steps

1. Run the playbook:

```bash
ansible-playbook 2-tier.yml -i inventory
```

2. Open browser and access:

```
http://<App_Server_Public_IP>/index.php
```

3. PHP Info page should be visible ✅

4. Login to DB server and verify DB:

```bash
mysql -u root -e "SHOW DATABASES;"
```

---

## 📸 Screenshots (Add Your Own)

### 1️⃣ Ansible Playbook Execution


![](/img/Screenshot%20(112).png)


### 2️⃣ PHP Page Output


![](/img/Screenshot%20(115).png)


### 3️⃣ Database Verification


![](/img/Screenshot%20(116).png)


---

## ✅ Conclusion

This project successfully demonstrates:

* Automated deployment of a **2-tier architecture**
* Usage of **single Ansible playbook** for multiple servers
* Real-world DevOps workflow using **Ansible + AWS EC2**

This approach improves **consistency**, **speed**, and **reliability** in application deployment.

---

## 👤 Author

**Vaibhav Navnath Bhuse**

DevOps | Ansible | AWS
