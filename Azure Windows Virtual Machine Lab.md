# Azure Windows Virtual Machine Lab (End-to-End Guide)

## 📌 Lab Overview

This lab walks through the complete lifecycle of deploying, accessing, and safely deleting a **Windows Server Virtual Machine** in **Microsoft Azure**. It is designed for hands-on learning and cost control best practices.

**Estimated Time:** 15–25 minutes  
**Skill Level:** Beginner to Intermediate  
**Platform:** Microsoft Azure  
**OS:** Windows Server 2025 Datacenter (x64)

---

## 🎯 Lab Objectives

By completing this lab, you will be able to:

- Deploy a Windows Server VM in Azure
- Configure networking and security for RDP access
- Connect to the VM using Remote Desktop
- Properly delete all resources to avoid charges

---

## 📋 Prerequisites

- Active Azure subscription
- Access to the Azure Portal
- RDP client (Windows built-in or equivalent)
- Password manager (recommended)

---

## 🧱 Architecture Overview


# Azure Windows Virtual Machine Lab Setup Guide

## Phase 1: Project Setup

### 1. Navigate to the Virtual Machine Service
- Log in to the **Azure Portal**.
- In the top search bar, type **Virtual machines** and select the service.
- Click **+ Create** (top left) and select **Azure virtual machine**.

### 2. Configure Basic Settings (Basics Tab)
- **Subscription:** Select your active subscription.
- **Resource Group:** Click **Create new**
  - **Naming Convention:** `RG-WindowsVM-Lab-011126`
- **Virtual Machine Name:**  
  - Example: `VM-Win-011126`
- **Region:** `(US) East US` (or the closest region to you).
- **Availability Options:**  
  - Select **No infrastructure redundancy required** (recommended for labs).
- **Security Type:** Standard
- **Image:**  
  - Windows Server 2025 Datacenter – x64 Gen2
- **VM Architecture:** x64
- **Size:**  
  - `Standard_D2s_v3` — 2 vCPUs, 8 GiB memory

### 3. Administrator Account
- **Username:**  
  - Example: `azureuser`
- **Password:**  
  - Must be at least **12 characters**
  - Include **uppercase**, **lowercase**, **numbers**, and **special characters**
- **Action:**  
  - Save credentials in a password manager immediately.

### 4. Inbound Port Rules
- **Public inbound ports:** Allow selected ports
- **Selected inbound ports:**  
  - ✅ RDP (3389) — required for VM access

---

## Phase 2: Disks & Networking (Quick Setup)

### 5. Disks
- Click **Next: Disks**
- **OS Disk Type:**
  - Standard SSD (cheaper, sufficient for labs)
  - Premium SSD (faster, optional)
- Leave all other settings as default.

### 6. Networking
- Click **Next: Networking**
- Ensure the following are automatically created (marked as **(new)**):
  - Virtual Network
  - Subnet
  - Public IP
- **NIC Network Security Group:** Basic
- **Public inbound ports:**  
  - Allow selected ports (RDP 3389)

---

## Phase 3: Validation & Creation

### 7. Review
- Click **Review + create**
- Wait for the green **Validation passed** message.
- **If validation fails:**
  - Click **Previous**
  - Fix red-highlighted errors (commonly password complexity or missing fields)

### 8. Deploy
- Review the estimated hourly cost.
- Click **Create**
- Deployment typically takes **2–5 minutes**.

---

## Phase 4: Connecting to Your VM

### 9. Access the Resource
- Once deployment completes, click **Go to resource**.

### 10. Connect via RDP
- On the **Overview** page, click **Connect**
- Select **Native RDP**
- Click **Download RDP File**

### 11. Login
- Open the downloaded `.rdp` file.
- Click **Connect**
- If prompted:
  - Select **More choices** → **Use a different account**
- Enter the username and password created earlier.
- Accept the security certificate warning by clicking **Yes**.

✅ You are now logged into your Windows Virtual Machine desktop.

---

## Phase 5: Lab Clean-Up (Crucial Step)

### 12. Destroy Resources
> ⚠️ Never leave lab resources running when not in use.

- Return to **Azure Portal Home**
- Search for **Resource groups**
- Select your resource group:
  - Example: `RG-WindowsVM-Lab-011126`
- Click **Delete resource group**
- Type the resource group name to confirm
- Click **Delete**

**Why this matters:**  
Deleting the resource group removes the VM, disk, IP address, and network together—preventing unexpected charges.
