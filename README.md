# Zero Trust Identity Lab

A hands-on cybersecurity lab that demonstrates how modern organizations transition from traditional perimeter-based security to a **Zero Trust Architecture (ZTA)**.

This lab guide walks learners through building a small identity-based network using **Tailscale, Linux, and role-based access control**, while applying the core principles defined in **NIST SP 800-207**.

The final result is a working mini Zero Trust environment that includes **identity-based connectivity, microsegmentation, least privilege enforcement, and AI-assisted security analysis**.

---

# Live Lab Guide

You can access the full interactive lab guide here:

**[https://yourusername.github.io/zero-trust-lab](https://sharuhampali.github.io/zta_lab_guide/)**

The guide contains:

- step-by-step instructions
- architecture diagrams
- copyable command blocks
- interactive knowledge checks
- troubleshooting notes

---

# Why This Lab Exists

Traditional enterprise networks relied heavily on **perimeter security**.

In this model, organizations trusted users and devices **once they entered the internal network**.

Example:
User → VPN → Internal Network → All Services


Once authenticated through a VPN or firewall, users could often access many internal systems with minimal additional verification.

However, modern cyber attacks frequently exploit this model.

If an attacker compromises a single device inside the network, they can often move laterally across systems.

This problem has led to the development of **Zero Trust Architecture (ZTA)**.

Zero Trust assumes:

> The network is already compromised.

Instead of trusting users based on location or IP address, every request must be verified using identity and access policies.

Example:
User Identity → Policy Engine → Specific Service


Access decisions are based on:

- user identity
- device identity
- policy rules
- least privilege access

This lab demonstrates how these ideas can be implemented in a simple but realistic environment.

---

# Learning Objectives

After completing this lab, the learner will be able to:

- Understand the core concepts of **Zero Trust Architecture**
- Deploy an **identity-based mesh network** using Tailscale
- Implement **microsegmentation** using network ACL policies
- Enforce the **principle of least privilege** using Linux RBAC
- Use **generative AI tools** to assist with security log analysis
- Understand how modern organizations monitor authentication events

---

# Lab Architecture

The lab simulates a small Zero Trust environment using two machines.
Your Laptop (Analyst Machine)
│
▼
Tailscale Zero Trust Mesh
│
▼
Ubuntu Lab Server
│
└── Web Service :8080


Even though both systems may exist on the same physical network, communication occurs through an **identity-aware encrypted mesh network**.

---

# Technologies Used

This lab uses only free and open tools.

| Component | Technology | Purpose |
|-----------|------------|--------|
| Network | Tailscale | Zero Trust Network Access |
| Compute | Ubuntu Linux | Lab server environment |
| Identity | Google / GitHub SSO | Device authentication |
| Access Control | Tailscale ACLs | Microsegmentation |
| RBAC | Linux sudoers | Least privilege enforcement |
| Service | Python HTTP Server | Demo application |
| AI Analysis | ChatGPT / Claude | Security log interpretation |

---

# Lab Milestones

The lab is divided into four milestones that demonstrate the key principles of Zero Trust.

---

## 1. Identity-Centric Connectivity

Instead of granting access based on IP addresses, devices authenticate using **user identity via SSO**.

Tailscale creates an encrypted mesh network where each device has a verified identity.

---

## 2. Microsegmentation

Network access is restricted to a **single service (port 8080)**.

All other services and ports are blocked using **Tailscale ACL policies**.

This prevents lateral movement inside the network.

---

## 3. Principle of Least Privilege

A restricted **Junior Admin role** is created.

This user can:
restart the web service


But cannot:
read sensitive system files
gain full administrative privileges


This is implemented using the Linux **sudoers** policy system.

---

## 4. Generative AI Security Analysis

Authentication failures are intentionally generated.

The learner then uses a **large language model** to analyze `auth.log` entries and explain suspicious activity.

This demonstrates how AI can function as a **SOC analyst assistant**.

---

# Prerequisites

Before starting the lab, ensure the following tools are available:

### Virtualization

Install one of the following:

- VirtualBox
- VMware Workstation

### Operating System

Download and install:

Ubuntu 22.04 or 24.04

### Accounts

Create an account for:

- Tailscale
- Google or GitHub (for SSO login)

---

# Running the Lab

The full lab instructions are available on the GitHub Pages site.

To summarize the workflow:

1. Create an Ubuntu virtual machine
2. Install Tailscale on the server
3. Install Tailscale on the host machine
4. Connect both machines to the same identity network
5. Launch a Python web service on port 8080
6. Apply Tailscale ACL rules to enforce microsegmentation
7. Create a restricted `junioradmin` user
8. Configure sudo permissions for least privilege
9. Generate authentication failures
10. Analyze logs using AI

Detailed instructions are available in the interactive guide.

---
# How This Demonstrates Zero Trust

This lab recreates several real-world security concepts used by modern organizations:

| Concept | Demonstrated By |
|--------|----------------|
Identity-based access | Tailscale SSO authentication |
Network segmentation | ACL policy restricting port 8080 |
Least privilege | restricted sudo permissions |
Continuous monitoring | auth.log analysis |
Security automation | AI-assisted log analysis |

---
# References

- NIST SP 800-207 — Zero Trust Architecture
- Tailscale Documentation
- Linux sudoers Manual
- OWASP Zero Trust Principles

---
