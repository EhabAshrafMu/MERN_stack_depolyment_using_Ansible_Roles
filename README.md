# MERN Stack Deployment with Ansible

This repository contains an Ansible playbook for deploying a basic **MERN stack** (MongoDB, Express.js, React, Node.js) across two separate servers:

- One server hosts the **frontend and backend** (React + Express/Node.js).
- The other server hosts the **MongoDB database**.

---

## 📁 Repository Structure
ansible.cfg 
group_vars # vars folder
├── inventory/
│ └── hosts # Ansible inventory file (define your server IPs here)
├── roles/
│ ├── webserver/ # Tasks for frontend/backend deployment
│ └── dbserver/ # Tasks for MongoDB installation and configuration
├── playbook.yaml # Main Ansible playbook
└── README.md # Documentation

---

## 🚀 Prerequisites

Before running the playbook, ensure the following:

- Two Linux servers (e.g., RHEL or Ubuntu)
- Passwordless SSH access from the Ansible control node to both servers
- Ansible installed on the control node
- Python and `sudo` installed on both target servers

---

## 🔧 Configuration

### 1. Inventory File

Edit `inventory/hosts` and add your server IPs under the appropriate groups:

```ini
[webserver]
192.168.1.100

[dbserver]
192.168.1.101


📦 Deployment
Step 1: Clone the Repository
bash
Copy
Edit
git clone https://github.com/your-username/mern-ansible-deployment.git
cd mern-ansible-deployment
Step 2: Update the Inventory File
Edit inventory/hosts with your actual server IPs.

Step 3: Run the Playbook
bash
Copy
Edit
ansible-playbook -i inventory/hosts playbook.yaml
This command installs Node.js, MongoDB, and deploys the MERN stack on your servers.

📎 Notes
Ensure your backend is configured to connect to MongoDB using the database server’s internal IP.

This setup is intended for development or internal use. For production, consider adding:

Firewall rules

Authentication

SSL/TLS

NGINX reverse proxy
