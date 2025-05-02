MERN Stack Deployment with Ansible
This repository contains an Ansible playbook for deploying a basic MERN stack (MongoDB, Express.js, React, Node.js) across two separate servers:

One server hosts the frontend and backend (React + Express/Node.js).

The other server hosts the MongoDB database.

📁 Repository Structure
.
├── inventory/
│   └── hosts           # Ansible inventory file (define your server IPs here)
├── roles/
│   ├── webserver/      # Tasks for frontend/backend deployment
│   └── dbserver/       # Tasks for MongoDB installation and configuration
├── playbook.yaml       # Main Ansible playbook
└── README.md           # Documentation
🚀 Prerequisites
Before running the playbook, ensure the following:

Two Linux servers (recommended: RHEL or Ubuntu)

Passwordless SSH access from your Ansible control node to both servers

Ansible installed on the control node

Python and sudo installed on both target servers

🔧 Configuration
1. Inventory File
Edit inventory/hosts and add your server IPs under the appropriate groups:

ini
Copy
Edit
[webserver]
192.168.1.100

[dbserver]
192.168.1.101
2. Variables (Optional)
You can define custom variables in group_vars/ or host_vars/ to override default settings like:

MongoDB data path

Application ports

Domain names

Environment variables

📦 Deployment
Step 1: Clone the Repository
bash
Copy
Edit
git clone https://github.com/your-username/mern-ansible-deployment.git
cd mern-ansible-deployment
Step 2: Update Inventory
Edit inventory/hosts and enter the IPs of your frontend/backend server and database server.

Step 3: Run the Playbook
bash
Copy
Edit
ansible-playbook -i inventory/hosts playbook.yaml
This will install Node.js, MongoDB, and deploy your application automatically.

📎 Notes
Ensure that your application is properly configured to connect to MongoDB using the database server’s IP address.

Authentication and firewalls are not preconfigured—make sure to secure your servers for production use.

You may want to set up SSL/TLS and reverse proxy (e.g., NGINX) for real-world deployments.

