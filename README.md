<div align="center">

# 🧾 StickNote

### Smart Shop Ledger & Party Management Platform

**Digital Khata • Real-Time Balance Tracking • Automated Payment Receipts**

![React](https://img.shields.io/badge/React-19-61DAFB?style=for-the-badge&logo=react&logoColor=black)
![Vite](https://img.shields.io/badge/Vite-8-646CFF?style=for-the-badge&logo=vite&logoColor=white)
![PHP](https://img.shields.io/badge/PHP-Backend-777BB4?style=for-the-badge&logo=php&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-Database-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![React Router](https://img.shields.io/badge/React%20Router-7-CA4245?style=for-the-badge&logo=reactrouter&logoColor=white)
![MIT](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

---

### Replacing the Paper Khata with a Smart Digital Ledger

*Helping shopkeepers track parties, credit, purchases, and payments — all in one place.*

</div>

# 📖 Overview

StickNote is a shop management platform built for small and medium retailers who currently rely on a paper "khata" (ledger) to track parties, purchases, customer credit, and payments.

The platform digitizes day-to-day shop bookkeeping — adding parties, logging purchases, recording cash payments, managing customer advances, and checking outstanding balances — while giving shop owners instant payment receipts, SMS/email balance notifications, and a secure login system built around each registered shop.

A dedicated **Admin Panel** lets the StickNote team verify new shop registrations and monitor onboarding, keeping the whole platform centrally manageable.

---

# 🎯 Problem Statement

Small shopkeepers across India still track their business manually:

- Paper ledgers that get lost, torn, or miscalculated
- No easy way to check a customer's outstanding balance
- Manual, error-prone purchase and payment entries
- No digital trail of payments or receipts
- No automated way to remind customers about dues
- Time-consuming registration and verification for new shops

StickNote solves this by combining a fast, offline-friendly React interface with a lightweight PHP + MySQL backend, giving every shop its own secure digital ledger — accessible from any device, with instant receipts and balance notifications.

---

# ⚡ Platform Features

## 🏪 Shop Registration & Secure Login

- Shop owner registration with payment screenshot verification
- Unique auto-generated login code per shop
- Protected, token-based session routes

## 🧑‍🤝‍🧑 Party Management

- Add, update, and look up parties (suppliers/vendors)
- Auto-generated Party IDs
- Quick mobile-number based party search

## 🛒 Purchase & Cash Pay Entries

- Multi-slot purchase entry (product, price, quantity, auto-calculated total)
- Cash payment tab with UPI / Cash / Card modes
- Editable, punch-in style ledger rows inspired by a physical khata

## 💰 Customer Advance & Balance Tracking

- Record customer advances against a bill
- Real-time balance calculation
- Instant balance lookup by mobile number

## 🧾 Digital Payment Receipts & Invoices

- Auto-numbered invoices via an invoice counter
- Shareable payment status / receipt lookup page
- QR-based UPI payment support with screenshot upload

## 📷 Scanner & Screenshot Uploads

- Upload and store payment/scanner screenshots
- Backend file validation (type & size checks)

## 📩 SMS & Email Notifications

- Automated balance notifications via SMS (2Factor)
- Lightweight custom SMTP mailer (no external libraries)
- Receipt delivery over email

## 🖥️ Admin Dashboard

- Central view of all shop registrations
- Registration verification & approval workflow
- Live refresh of pending/verified shops

---

# 🏗️ System Architecture

```text
                        Shop Owner / Customer

                                │

                                ▼

                React (Vite) Frontend — Shop Manager

                                │

                         REST API Calls

                                │

                                ▼

                      PHP Backend (REST Endpoints)

                                │

          ┌─────────────────────┼─────────────────────┐

          ▼                                           ▼

   MySQL Database                          SMTP Mailer + SMS Gateway

          │                                           │

          └─────────────────────┬─────────────────────┘

                                ▼

                 Registration • Ledger • Receipts

                                │

                                ▼

               React (Vite) Admin Panel — Shop Admin

                                │

                                ▼

            Registration Verification & Monitoring
```

---

# 🛠️ Tech Stack

| Category              | Technology                          |
| ---------------------- | ------------------------------------ |
| Frontend               | React 19 + Vite                     |
| Routing                | React Router v7                     |
| Animation              | Framer Motion                       |
| Icons                  | React Icons                         |
| Backend                | PHP (REST endpoints)                |
| Database               | MySQL                               |
| Email                  | Custom lightweight SMTP mailer      |
| SMS                    | 2Factor transactional SMS API       |
| Auth                   | Login-code based sessions (localStorage token) |
| File Uploads           | PHP file handling (payments/scanner)|
| Styling                | CSS                                  |
| Version Control        | Git & GitHub                        |
| Deployment             | Apache/.htaccess (shared hosting)   |

---

# 📂 Project Structure

```text
StickNote/

├── shop_manager/                     # Customer/Shop-owner facing app
│   ├── backend/
│   │   ├── add_party.php
│   │   ├── register_user.php
│   │   ├── login_user.php
│   │   ├── save_tab_entry.php
│   │   ├── save_customer_advance.php
│   │   ├── get_parties.php
│   │   ├── get_receipt.php
│   │   ├── upload_scanner.php
│   │   ├── send_balance_notification.php
│   │   ├── sms_sender.php
│   │   ├── smtp_mailer.php
│   │   ├── db_config.php
│   │   ├── shopmanager_database.sql
│   │   └── uploads/
│   │
│   ├── src/
│   │   ├── Components/
│   │   │   ├── HomePage/
│   │   │   ├── ShopHomePage/
│   │   │   └── Invoice/
│   │   ├── assets/
│   │   ├── App.jsx
│   │   └── main.jsx
│   │
│   ├── package.json
│   └── .htaccess
│
├── shop_admin/                       # Admin verification panel
│   ├── backend/
│   │   ├── list_registrations.php
│   │   ├── verify_registration.php
│   │   ├── db_config.php
│   │   └── shop_admin_database.sql
│   │
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   │   └── Dashboard.jsx
│   │   ├── App.jsx
│   │   └── main.jsx
│   │
│   └── package.json
│
└── package-lock.json
```

---

# 🚀 Getting Started

## Clone the Repository

```bash
git clone https://github.com/<your-username>/StickNote.git

cd StickNote
```

---

# ⚙️ Backend Setup

Both `shop_manager/backend` and `shop_admin/backend` run on plain PHP with MySQL.

1. Place the `backend` folders on a PHP-enabled server (XAMPP/WAMP/Apache).
2. Create a MySQL database and import the schema files:

```bash
mysql -u root -p your_database < shop_manager/backend/shopmanager_database.sql
mysql -u root -p your_database < shop_admin/backend/shop_admin_database.sql
```

3. Update database credentials in:

```
shop_manager/backend/db_config.php
shop_admin/backend/db_config.php
```

4. Configure SMS and email credentials:

```
shop_manager/backend/sms_config.php
shop_manager/backend/mail_config.php
```

5. Ensure the `uploads/` folder inside `shop_manager/backend` is writable for payment & scanner screenshots.

Backend will be available at:

```
http://localhost/shop_manager/backend
http://localhost/shop_admin/backend
```

---

# 💻 Frontend Setup

## Shop Manager App

```bash
cd shop_manager
npm install
npm run dev
```

## Shop Admin Panel

```bash
cd shop_admin
npm install
npm run dev
```

Create a production build:

```bash
npm run build
```

The frontend will be available at:

```
http://localhost:5173
```

(or the URL generated by Vite)

> **Note:** Update the `API_BASE` constant at the top of `ShopHomePage.jsx` / `Dashboard.jsx` to point to your backend URL if it differs from the local defaults.

---

# 🌐 Platform Highlights

### 🏪 Digital Shop Onboarding

Shop owners register with basic details and a payment screenshot, then receive a unique login code — no passwords to remember.

### 🧑‍🤝‍🧑 Party & Purchase Ledger

Add parties, log purchases across multiple product slots, and let totals auto-calculate from price × quantity.

### 💰 Customer Advance & Balance Check

Track advance payments per customer and instantly look up outstanding balances by mobile number.

### 🧾 Instant Digital Receipts

Every payment generates a shareable, lookup-able receipt page — no more handwritten slips.

### 📩 Automated Notifications

Balance reminders go out to customers automatically over SMS and email, keeping collections on track.

### 🖥️ Centralized Admin Verification

The Shop Admin dashboard gives the StickNote team a live view of every shop registration awaiting verification.

---

# 💡 Core Capabilities

### 🏪 Shop Registration & Auth

Secure, code-based shop onboarding with payment proof verification and protected session routes on the frontend.

### 🧑‍🤝‍🧑 Party & Customer Management

Structured party/customer records with auto-generated IDs, mobile-based lookup, and editable ledger rows.

### 🛒 Purchase & Cash Pay Tracking

Multi-slot purchase entries with automatic price × quantity totals, plus a dedicated cash-pay tab for daily collections.

### 💰 Advance & Balance Management

Record customer advances against bills and compute real-time outstanding balances.

### 🧾 Receipts & Invoicing

Auto-incrementing invoice numbers with a public lookup page for customers to check payment status.

### 📩 SMS & Email Automation

A custom lightweight SMTP mailer and 2Factor SMS integration handle balance notifications and receipt delivery without heavy external dependencies.

### 🖥️ Admin Oversight

A separate React admin app lists and verifies shop registrations, keeping platform growth centrally managed.

---

# 🎯 Learning Outcomes

This project demonstrates practical experience in:

- React 19 + Vite application development
- React Router v7 protected routing
- REST API design with plain PHP
- MySQL schema design for ledger-style data
- File upload handling & validation
- Custom SMTP mail delivery (no third-party libraries)
- SMS gateway integration
- Multi-app monorepo structure (customer app + admin app)
- Token-based client-side authentication

---

# 📈 Future Roadmap

### 🤖 Automation & Insights

- Automated daily/monthly ledger summaries
- Sales & purchase analytics dashboard
- Smart balance-due reminders based on due dates

### 🌐 Platform Growth

- Multi-shop management for chain retailers
- Role-based access (owner, staff, accountant)
- Bulk import/export of parties & entries

### 📱 Digital Experience

- Native Android app for shop owners
- WhatsApp-based receipt delivery
- Offline-first entry with background sync

### 🔗 Security & Scale

- OTP-based login alongside login codes
- Cloud storage for payment/scanner uploads
- API rate limiting & audit logs

---

# 🤝 Contributing

Contributions, ideas, and improvements are always welcome.

1. Fork the repository

2. Create a feature branch

```bash
git checkout -b feature/new-feature
```

3. Commit your changes

```bash
git commit -m "feat: add new feature"
```

4. Push your branch

```bash
git push origin feature/new-feature
```

5. Open a Pull Request

---

# 📜 License

This project is licensed under the **MIT License**.

---

<div align="center">

## ⭐ Support the Project

If you found **StickNote** useful, consider giving this repository a **Star ⭐** and sharing it with the community.

### Digitizing the shopkeeper's khata, one ledger at a time.

</div>
