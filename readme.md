# 📚 Documentation Wiki for AWS & DevOps Guides

Welcome to the **Documentation Wiki** for the `rishab0807/documentation` repository!
This repository serves as a **central knowledge base** for practical, step-by-step guides focused on **AWS**, **DevOps**, **cloud access recovery**, and **cross-platform development setups** (Windows + WSL).

These documents are written to be **hands-on**, **production-oriented**, and suitable for **real-world troubleshooting, onboarding, and daily DevOps workflows**.

---

## 🧾 Available Wiki Pages

### 🔑 EC2 SSH Access Recovery & New Key Pair Setup

A detailed guide on how to regain SSH access to an Ubuntu EC2 instance when you’ve lost the original PEM file — **without stopping the instance** — using **AWS Systems Manager (SSM)**. The guide covers:

* Enabling SSM access
* Injecting a new SSH public key
* Validating access from **WSL and Windows PowerShell**

📄 **View it here:**
👉 [https://github.com/rishab0807/documentation/wiki/EC2-SSH-Access-Recovery-&-New-Key-Pair-Setup](https://github.com/rishab0807/documentation/wiki/EC2-SSH-Access-Recovery-&-New-Key-Pair-Setup)

---

### 🖥 GitHub Multi-Account Setup (WSL & Windows)

Step-by-step instructions for configuring and managing **multiple GitHub accounts** on a single machine using **Windows + WSL**. Ideal for developers handling **personal and work accounts** simultaneously.

This guide includes:

* SSH key separation per account
* SSH config best practices
* Git identity validation

📄 **View it here:**
👉 [https://github.com/rishab0807/documentation/wiki/GitHub-Multi-Account-Setup-(WSL-Windows)](https://github.com/rishab0807/documentation/wiki/GitHub-Multi-Account-Setup-%28WSL-Windows%29)

---

### ☁️ AWS Multiple Account Profile Setup (Windows + WSL)

A complete guide to configuring **multiple AWS accounts and CLI profiles** on a Windows machine with **WSL**, using a **single shared AWS configuration** via symlinks.

Covers:

* Secure IAM-based CLI access (no root keys)
* Multiple AWS profiles per account
* One-time symlink setup between Windows and WSL
* Adding/removing profiles safely
* Best practices for long-term maintenance

📄 **View it here:**
👉 [https://github.com/rishab0807/documentation/wiki/AWS-Multiple-Account-Profile-Setup-(Windows-WSL)](https://github.com/rishab0807/documentation/wiki/AWS-Multiple-Account-Profile-Setup-%28Windows-WSL%29)

---

## 📌 How to Use This Wiki

1. Select the guide you need from the list above.
2. Follow the steps carefully in order.
3. Use the **verification commands** included in each guide.
4. Apply the documented **best practices** for security and maintainability.
5. Use these docs for **team onboarding**, **incident recovery**, or **knowledge sharing**.

---

## 🛠 Contribution Guide

Contributions are welcome and encouraged.

When adding or improving documentation:

* Create a new **Wiki page** for each topic
* Keep instructions **clear, concise, and actionable**
* Prefer real-world examples over theory
* Include verification or test steps
* Link related wiki pages where applicable

---

## 🚀 Suggested Topics for Future Docs

* AWS SSM-only access patterns (no SSH)
* Bastion host / jump box architecture
* SSH key rotation strategies
* IAM access design for multi-account AWS setups
* Terraform / IaC workflows with multiple AWS profiles
* Secure secrets handling in WSL environments

---

## 🤝 Got Suggestions or Improvements?

If you have ideas or find issues:

* Open an **Issue** in this repository
* Submit a **Pull Request** with your changes
* Propose new wiki topics for future documentation

---

Thanks for contributing to and using this documentation repository! 🎉

*This README acts as the entry point to the wiki and is intended to evolve as new guides are added.*
