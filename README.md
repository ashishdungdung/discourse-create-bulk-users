# 🚀 Discourse Bulk User Creator (Excel → API)

Create **multiple users in Discourse** effortlessly using an **Excel file** and the **Discourse Admin API**.

This utility is useful when migrating communities, onboarding users in bulk, or setting up test environments.

---

## ✨ Features

- 📄 Read users from an **Excel (.xlsx)** file  
- 🔐 Uses **official Discourse API** (safe & supported)
- ⚡ Create users **in bulk** with a single command
- 🧩 Simple, minimal Python script – easy to customize
- 🛠️ Ideal for **migrations, staging, or internal communities**

---

## 📂 Project Structure

discourse-create-bulk-users/
│
├── users.py # Main script
├── users.xlsx # Sample input Excel file
├── requirements.txt # Python dependencies
└── README.md
---

## 🧑‍💻 ## 🧑‍💻 Requirements

- Python **3.7+**
- A **Discourse Admin account**
- Discourse **API Key**
- Access to your Discourse instance

---

## 🔑 Discourse API Setup

1. Log in as **Admin** on your Discourse site  
2. Go to:  
   **Admin → API → New API Key**
3. Create a key with:
   - **Scope**: Global
   - **User**: Admin user
4. Note down:
   - API Key
   - Admin Username
   - Forum Base URL (e.g. `https://community.example.com`)

---

## 📄 Excel File Format (`users.xlsx`)

Ensure your Excel file contains the following columns:

| Column Name | Description |
|------------|-------------|
| `name` | Full name of the user |
| `email` | Email address |
| `username` | Discourse username |

> ⚠️ Passwords are **not required**.  
Discourse will automatically send **activation emails**.

---

## 📦 Installation

Clone the repository:

```bash
git clone https://github.com/ashishdungdung/discourse-create-bulk-users.git
cd discourse-create-bulk-users
