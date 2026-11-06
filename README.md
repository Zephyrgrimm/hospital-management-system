# 🏥 Hospital Management System

A desktop-based **Hospital Management System** built with **Python** and **Tkinter**, backed by a **MySQL** database. It provides a centralized GUI to manage hospital operations including doctors, patients, staff, pharmacy, and accounts — all from a single main dashboard.

---

## 📋 Table of Contents

- [Features](#features)
- [Modules](#modules)
- [Tech Stack](#tech-stack)
- [Prerequisites](#prerequisites)
- [Database Setup](#database-setup)
- [Installation](#installation)
- [Running the Application](#running-the-application)
- [Project Structure](#project-structure)
- [Screenshots](#screenshots)

---

## ✨ Features

- 🖥️ Clean and intuitive GUI built with Tkinter
- 🩺 Doctor information viewer with department and fee details
- 🧑‍⚕️ Patient records management
- 💊 Pharmacy/Medicine inventory with search and display
- 👨‍💼 Staff management with add, search, and display functionality
- 💰 Accounts & billing module with invoice generation and payment tracking
- 🔍 Search/filter records by various fields
- 📅 Date picker integration via `tkcalendar`
- 🗄️ Full MySQL database integration

---

## 📦 Modules

| Module | File | Description |
|--------|------|-------------|
| **Main Dashboard** | `main page` | Entry point — launches the main hospital window with navigation menu |
| **Doctor** | `doc.py` | Displays all doctors with their qualifications, department, fees, and availability |
| **Staff** | `bldbnk.py` | View, search, and add hospital staff records (role, salary, contact, status, etc.) |
| **Add Staff** | `add_staff.py` | Form to register new staff members into the database |
| **Pharmacy** | `pharmacy` | Search and display medicine inventory (dosage, strength, stock, expiry, price) |
| **Accounts** | `acc.py` | Manage patient billing — doctor fees, medicine costs, payment type & status |

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| **Language** | Python 3.x |
| **GUI Framework** | Tkinter + ttk |
| **Database** | MySQL |
| **DB Connector** | `mysql-connector-python` |
| **Image Handling** | Pillow (PIL) |
| **Date Picker** | tkcalendar |

---

## ✅ Prerequisites

Make sure the following are installed on your system:

- Python 3.8+
- MySQL Server (running on port `3307` by default in this project)
- pip packages:

```bash
pip install mysql-connector-python pillow tkcalendar
```

---

## 🗄️ Database Setup

1. Open your MySQL client and create the database:

```sql
CREATE DATABASE hospital_management;
USE hospital_management;
```

2. Create the required tables:

```sql
-- Doctor Table
CREATE TABLE doctor (
    doctor_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    education VARCHAR(150),
    position VARCHAR(100),
    fees DECIMAL(10,2),
    availability VARCHAR(200)
);

-- Patients Table
CREATE TABLE patients (
    patient_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    age INT,
    gender VARCHAR(10),
    contact_number VARCHAR(15),
    address TEXT,
    disease VARCHAR(200)
);

-- Staff Table
CREATE TABLE Staff (
    staff_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    role VARCHAR(100),
    department_id INT,
    contact_number VARCHAR(15),
    email VARCHAR(100),
    address TEXT,
    date_of_birth DATE,
    gender VARCHAR(10),
    salary DECIMAL(10,2),
    emergency_contact_number VARCHAR(15),
    status VARCHAR(50)
);

-- Pharmacy Table
CREATE TABLE Pharmacy (
    medicine_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(150),
    dosage_form VARCHAR(100),
    strength VARCHAR(100),
    quantity INT,
    expiry_date DATE,
    manufacturer VARCHAR(150),
    selling_price DECIMAL(10,2)
);

-- Accounts Table
CREATE TABLE Accounts (
    account_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    date DATE,
    doctor_fees DECIMAL(10,2),
    medicine_cost DECIMAL(10,2),
    total_cost DECIMAL(10,2),
    payment_type VARCHAR(50),
    contact_number VARCHAR(15),
    payment_status VARCHAR(50)
);
```

3. Update the database credentials in each `.py` file:

```python
connection = mysql.connector.connect(
    host='localhost',
    user='root',          # your MySQL username
    password='yourpassword',  # your MySQL password
    database='hospital_management',
    port=3306             # or your MySQL port
)
```

> **Note:** Update the image file paths in each module to point to the correct location of `logo2.png`, `hospital2.jpg`, and `main3.jpg` on your system.

---

## 📥 Installation

```bash
# 1. Clone the repository
git clone https://github.com/Zephyrgrimm/hospital-management-system.git
cd hospital-management-system

# 2. Install dependencies
pip install mysql-connector-python pillow tkcalendar

# 3. Set up the database (see Database Setup above)

# 4. Update DB credentials and image paths in all .py files
```

---

## ▶️ Running the Application

```bash
python "main page"
```

This opens the **KPC Hospitals** main dashboard. From there, use the **MENU** buttons to navigate to:

- 🩺 **DOCTOR** — View all doctors
- 🧑 **PATIENTS** — Manage patient records
- 💊 **PHARMACY** — Browse medicine inventory
- 👨‍💼 **STAFF** — View and add staff members
- 💰 **ACCOUNTS** — Handle billing and payments

---

## 📁 Project Structure

```
hospital-management-system/
│
├── main page         # Main dashboard (entry point)
├── doc.py            # Doctor information module
├── acc.py            # Accounts & billing module
├── bldbnk.py         # Staff management module
├── add_staff.py      # Add new staff form
├── pharmacy          # Pharmacy/medicine module
│
├── logo2.png         # Hospital logo
├── hospital2.jpg     # Hospital banner image
├── main3.jpg         # Main page background
├── doc.jpg           # Doctor section image
└── README.md         # Project documentation
```

---

## 🖼️ Screenshots

> _Place your application screenshots here._

| Main Dashboard | Doctor Module | Pharmacy Module |
|:-:|:-:|:-:|
| _(screenshot)_ | _(screenshot)_ | _(screenshot)_ |

---

## 📌 Notes

- Ensure MySQL is running **before** launching the application.
- Image paths in the source files are **hardcoded** — update them to match your local directory.
- The default MySQL port used in this project is `3307`. Change it to `3306` if your server uses the default port.

---

## 📄 License

This project is for educational purposes.
