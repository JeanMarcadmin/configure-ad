# 🖥️ Configuring On-Premises Active Directory in Azure VMs

This guide documents how to deploy and configure a traditional **Active Directory Domain Services (AD DS)** environment within **Azure virtual machines**, simulating an on-premises setup in the cloud.

<p align="center">
  <img src="https://learn.microsoft.com/en-us/azure/architecture/example-scenario/infrastructure/images/ad-ds.png" width="70%" alt="AD in Azure"/>
</p>

---

## 🎯 Purpose

To create an isolated, cloud-hosted Active Directory environment using Azure IaaS resources. This is useful for labs, hybrid network simulations, or production-like test environments without using Azure AD DS.

---

## 🧰 Prerequisites

- Azure Subscription
- Basic knowledge of networking and Active Directory
- Tools:
  - Azure Portal or Azure CLI
  - Remote Desktop Protocol (RDP)
  - Windows Server ISO or Marketplace Image

---

## 🏗️ Deployment Overview

1. Create a Virtual Network (VNet)
2. Deploy Windows Server VMs into that VNet
3. Promote one VM to Domain Controller
4. Configure DNS and join other VMs to the domain
5. Test Group Policy and AD features

---

## ⚙️ Step-by-Step Configuration

### 1. Create a Virtual Network

```bash
az network vnet create \
  --name ad-vnet \
  --resource-group AD-Infra \
  --address-prefix 10.0.0.0/16 \
  --subnet-name ad-subnet \
  --subnet-prefix 10.0.1.0/24
