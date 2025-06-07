# 🛡️ Wazuh Installation on Ubuntu

## 📘 Project Summary
This repository documents the step-by-step process I followed to install **Wazuh**, a powerful open-source security information and event management (SIEM) tool, on an Ubuntu virtual machine. The installation includes setup of the Wazuh indexer, server, and dashboard components with proper SSL certificate generation and configuration.

## 🧰 Tools & Environment
- OS: Ubuntu (VM)
- Wazuh version: 4.12
- Shell access with root privileges
- Tools used: `curl`, `nano`, `bash`, Wazuh certs tool

---

## ⚙️ Installation Steps

### 🔐 1. Get Root Privileges

sudo su

🌐 2. Install Curl

sudo apt install curl

📥 3. Download Certificate Tool & Config File

curl -sO https://packages.wazuh.com/4.12/wazuh-certs-tool.sh
curl -sO https://packages.wazuh.com/4.12/config.yml

📝 4. Edit Configuration File
Customize node names and IP addresses:

sudo nano ./config.yml

Example config structure:
nodes:
  indexer:
    - name: node-1
      ip: "<indexer-node-ip>"

  server:
    - name: wazuh-1
      ip: "<wazuh-manager-ip>"

  dashboard:
    - name: dashboard
      ip: "<dashboard-node-ip>"


📦 5. Generate Certificates

bash ./wazuh-certs-tool.sh -A
This generates .tar packages needed for installation.

sudo bash ./wazuh-install -a
Once installed, access the Wazuh dashboard via your browser.

🔐 Default Credentials
Username: admin

Password: (default password, update for security!)


