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
