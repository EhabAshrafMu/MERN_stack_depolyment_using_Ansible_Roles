# 🚀 MERN Stack Deployment with Ansible

This repository contains an automated **Ansible** playbook for deploying a basic **MERN stack** (MongoDB, Express.js, React, Node.js) across two separate Linux servers:

- **Web Server:** Hosts the frontend (React) and backend (Node.js/Express).
- **Database Server:** Hosts the MongoDB database.

---

## 📁 Project Structure

```
.
├── ansible.cfg
├── configure.yml.bk
├── group_vars
│   ├── all.yaml
│   └── webservers.yaml
├── inventory
│   └── hosts
├── playbook.yaml
└── roles
    ├── common
    │   ├── defaults
    │   ├── files
    │   ├── handlers
    │   ├── meta
    │   ├── tasks
    │   ├── templates
    │   ├── tests
    │   └── vars
    ├── dbserver
    │   ├── defaults
    │   ├── files
    │   ├── handlers
    │   ├── meta
    │   ├── tasks
    │   ├── templates
    │   ├── tests
    │   └── vars
    └── webserver
        ├── defaults
        ├── files
        ├── handlers
        ├── meta
        ├── tasks
        ├── templates
        ├── tests
        └── vars
```

---

## 🔧 Prerequisites

Make sure the following are in place before running the playbook:

- Two Linux servers (e.g., RHEL or Ubuntu).
- Passwordless SSH access from the Ansible control node to both target servers.
- Ansible installed on the control node.
- Python and `sudo` installed on both target servers.

---

## 🛠 Configuration Steps

### 1. Inventory File

Edit `inventory/hosts` to define your servers:

```ini
[webserver]
192.168.x.x

[dbserver]
192.168.y.y
```

### 2. Group Variables

Edit the files under `group_vars/` to define custom variables such as:

- MongoDB configuration
- Node.js app port
- React app build location
- Environment variables

---

## 📦 Deployment

### Step 1: Clone the Repository

```bash
git clone https://github.com/EhabAshrafMu/MERN_stack_depolyment_using_Ansible_Roles.git
cd MERN_stack_depolyment_using_Ansible_Roles
```

### Step 2: Edit the Inventory

Update `inventory/hosts` with your actual server IPs.

### Step 3: Run the Playbook

```bash
ansible-playbook -i inventory/hosts playbook.yaml
```

This will:

- Install Node.js, npm, and MongoDB
- Configure and enable MongoDB
- Deploy and serve the backend (Express) and frontend (React)

---

## ✅ Post-Deployment Check

- Visit `http://<webserver_ip>:3000` to check the React frontend.
- Use tools like Postman or browser to hit Express routes.
- Use `mongo` shell on the DB server to verify MongoDB is running.

---

## 🔒 Notes & Recommendations

This setup is intended for **development or internal use**. For production environments, consider:

- **Securing MongoDB** with user authentication
- **Reverse Proxy** using NGINX or Apache
- **SSL/TLS Certificates**
- **Firewall rules and SELinux configurations**
- **Environment variable management**

---

