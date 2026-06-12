# 🛡️ Secure IaaS Web Deployment & Advanced OS Governance

An enterprise-grade infrastructure deployment engineered on Microsoft Azure, featuring high-performance web asset delivery via Nginx and granular multi-tenant access control policies. This project implements strict compliance with the **Principle of Least Privilege (PoLP)** at both the cloud control plane and the Linux Operating System layer.

---

## 📋 Architectural Overview

Our client required a high-performance web application host providing complete configuration autonomy. Managed hosting services were bypassed in favor of an **Infrastructure as a Service (IaaS)** model, ensuring absolute administrative control over software dependencies, configurations, and manual patch cycles.

### 📐 Infrastructure Specifications
* **Cloud Service Provider:** Microsoft Azure
* **Compute Layer:** Azure Virtual Machine Instance
* **Operating System Platform:** Ubuntu 22.04 LTS (Long-Term Support)
* **Web Server Delivery:** Nginx Engine (High-Performance HTTP Server)

---

## 🔒 Perimeter Security & Network Topology

To mitigate exposure vectors and secure access paths, isolated ingress network traffic rules were provisioned through the Azure Network Security Group (NSG) firewall:

* **Port 22 (SSH):** Locked down strictly to authorized administrative endpoints to maintain remote cryptographic terminal connections for environment management.
* **Port 80 (HTTP):** Provisioned globally (`0.0.0.0/0`) to process inbound public web requests and route incoming data streams from client browsers directly to the active web root.

---

## ⚙️ Web Server Deployment & Core Optimization

Upon validating perimeter defenses, secure remote administrative terminal control was established via SSH. The local environment package registries were refreshed and core server components optimized:

```bash
# Update localized system package indices and execute full distribution upgrades
sudo apt update && sudo apt full-upgrade -y

# Deploy the high-performance Nginx web server engine
sudo apt install nginx -y
```

---

## 🚀 Application Asset Context
Rather than serving the boilerplate Nginx landing block, the environment root file system structure was updated. A premium, modern dark-themed web status portal dashboard displaying a dynamic "Mission Accomplished" was deployed. 

* 📁 View the raw code template here: **[Web Source Directory](./index.html)**

---

## 👥 Identity, Governance, & Multi-Tenant Linux Security
Handing over full root administrative access credentials (sudo) to client-side developers introduces extensive compliance, operational, and system-wide security liabilities. A reckless command or improper dependency patch could corrupt system libraries.

To remediate this, a robust access control model was implemented across both cloud resources and the server's OS kernel file boundaries. 

* **🌤️ Cloud Plane Governance (Azure IAM)**
Role-Based Access Control limits infrastructure configuration drift. The client’s identity inside the Azure management tenant was locked to a restrictive Reader role, granting visual resource audits while entirely preventing unauthorized compute modifications.

* **🐧 OS-Level Access Control (Granular Permissions)**
To isolate client developers within safe execution parameters, user workspaces were locked directly to the active application directory footprint

* **Group Strategy and Provisioning**
A dedicated systems management group named webdevs was established. A restricted client user workspace account named maxwelcyber was provisioned and attached to it:
# Create the secure developer coordination group
```bash
sudo groupadd webdevs
```

# Provision the client identity and append it to the team group infrastructure
```bash
sudo useradd -m -g webdevs maxwelcyber
```
