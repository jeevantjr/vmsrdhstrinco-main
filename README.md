# 🚗 VMS — Vehicle Management System

<p align="center">
  <img src="https://img.shields.io/badge/Status-Portfolio%20Demo-brightgreen?style=for-the-badge" alt="Status" />
  <img src="https://img.shields.io/badge/Stack-PHP%20%7C%20MySQL%20%7C%20HTML%2FCSS%2FJS-blue?style=for-the-badge" alt="Stack" />
  <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge" alt="License" />
  <img src="https://img.shields.io/badge/Made%20in-Sri%20Lanka%20🇱🇰-orange?style=for-the-badge" alt="Sri Lanka" />
  <a href="https://drjeevaraj.com/dev.html">
    <img src="https://img.shields.io/badge/Developer-Dr.%20T.%20Jeevaraj-navy?style=for-the-badge" alt="Developer" />
  </a>
</p>

---

> A centralized, web-based fleet management platform designed for public health institutions — replacing manual vehicle registers, fuel books, maintenance logs, insurance files, and spreadsheets with a single secure digital system.

---

## 📸 Screenshots

| Showcase Page | Live Dashboard |
|---|---|
| ![Showcase](images/showcase.png) | ![Dashboard](images/dashboard.png) |
| Full-stack feature showcase | Real-time fleet status (demo) |

---

## 🎯 What Problem Does It Solve?

Public health institutions typically manage their vehicle fleets through fragmented paper-based processes: handwritten fuel registers, manual maintenance logs, physical insurance folders, and multiple unlinked spreadsheets. This causes:

- Difficulty tracking overall fleet status and compliance
- Lost maintenance records and missed service intervals
- No audit trail for fuel consumption or cost accountability
- Insurance and licence expiry alerts only noticed retrospectively
- No central visibility across multiple institutions under a single administration

**VMS replaces all of that** with a role-aware, auditable, multi-institution web platform — accessible from any browser, with no need for specialist IT infrastructure.

---

## ✅ Features

**Authentication & Security**
- OTP-based two-factor login via PHPMailer
- Bcrypt password hashing
- Role-Based Access Control (RBAC) with three roles: Admin · Unit Officer · Institution User
- Session management with server-side validation
- Comprehensive audit trail for all data changes

**Vehicle Engine**
- Register and manage vehicles with full specifications (type, category, fuel type, year, capacity)
- Track operational status (Running / Under Repair / Idle / Off Road)
- Multi-institution assignment and transfer management

**Fuel Engine**
- Log fuel expenditure per vehicle per trip
- Track cumulative consumption and cost trends
- Export fuel reports per institution or fleet-wide

**Maintenance Engine**
- Record all service events (routine, emergency, major overhaul)
- Service interval alerts and overdue maintenance flagging
- Cost tracking per service event and per vehicle lifecycle

**Compliance Engine**
- Insurance policy tracking with expiry alerts (configurable lead time)
- Revenue licence renewal management
- Emission test and roadworthiness certificate tracking

**Reporting Engine**
- PDF report generation (FPDF / TCPDF)
- Excel data export
- Fleet-wide and per-institution summaries
- Date-range filtering across all modules

**Notification Engine**
- Automated email alerts for compliance expiry (configurable days in advance)
- PHPMailer integration with SMTP

---

## 🏗 System Architecture

Three-tier web application architecture:

```
┌─────────────────────────────────────────────────────────────┐
│                    PRESENTATION TIER                        │
│   HTML5 · CSS3 · JavaScript · Tailwind CSS · Lucide Icons  │
│   Responsive design · Chart.js dashboards                  │
└─────────────────────────┬───────────────────────────────────┘
                          │ HTTP / HTTPS
┌─────────────────────────▼───────────────────────────────────┐
│                   APPLICATION TIER                          │
│   PHP 8.x · Business Logic · RBAC Middleware               │
│   PHPMailer (OTP & Alerts) · FPDF / TCPDF (Reports)       │
│   Session Control · Server-side Validation                 │
└─────────────────────────┬───────────────────────────────────┘
                          │ PDO / MySQLi
┌─────────────────────────▼───────────────────────────────────┐
│                      DATA TIER                              │
│   MySQL 8.x · phpMyAdmin · 10 Core Entities               │
│   Audit Log Tables · Soft-Delete Support                   │
└─────────────────────────────────────────────────────────────┘
```

**Application Modules (8)**

| Module | Responsibility |
|---|---|
| Auth Engine | Login, OTP verification, password reset, session lifecycle |
| RBAC Engine | Role assignment, permission checks, user management |
| Vehicle Engine | Fleet registry, status tracking, multi-institution assignment |
| Fuel Engine | Expenditure logging, consumption analytics, cost tracking |
| Maintenance Engine | Service records, interval alerts, cost lifecycle |
| Compliance Engine | Insurance, licence, and certificate expiry management |
| Reporting Engine | PDF/XLS export, summary dashboards, date-range filtering |
| Notification Engine | Automated email alerts for compliance and service events |

---

## 🗄 Database Entities (10)

| Entity | Description |
|---|---|
| `users` | System users with roles, hashed passwords, OTP fields |
| `hospitals` | Registered institutions under fleet administration |
| `vehicles` | Core fleet registry (specs, status, institution, category) |
| `fuel_logs` | Per-vehicle fuel expenditure and consumption records |
| `services` | Maintenance and repair event records |
| `insurance` | Policy details, premium, expiry, insurer |
| `licenses` | Revenue licence and emission certificate tracking |
| `trips` | Trip log entries (origin, destination, purpose, mileage) |
| `notifications` | Alert queue for compliance and maintenance events |
| `documents` | Supporting document metadata (scanned files) |

---

## 🔒 Security Design

| Layer | Implementation |
|---|---|
| Password storage | Bcrypt (cost factor 12) |
| Login verification | OTP via PHPMailer (SMTP) |
| Access control | RBAC middleware on every PHP route |
| Session security | Server-side session tokens, timeout, regeneration |
| Input handling | Prepared statements (PDO), server-side validation |
| Audit trail | Timestamped log of all create/update/delete events |

---

## 👥 Role Matrix

| Feature | Admin | Unit Officer | Institution User |
|---|---|---|---|
| Manage users & roles | ✅ | ❌ | ❌ |
| Add/edit vehicles | ✅ | ✅ | ❌ |
| Log fuel & trips | ✅ | ✅ | ✅ |
| Log maintenance | ✅ | ✅ | ✅ |
| Manage compliance | ✅ | ✅ | ❌ |
| Generate PDF/XLS reports | ✅ | ✅ | ❌ |
| View dashboards | ✅ | ✅ | ✅ |

---

## 🛠 Tech Stack

| Layer | Technology |
|---|---|
| Frontend | HTML5, CSS3, JavaScript (ES6), Tailwind CSS, Lucide Icons |
| Charts | Chart.js |
| Backend | PHP 8.x |
| Database | MySQL 8.x / MariaDB |
| DB Admin | phpMyAdmin |
| Email | PHPMailer (SMTP) |
| PDF Export | FPDF / TCPDF |
| Local Dev | XAMPP (Apache + MySQL + PHP) |
| Version Control | Git / GitHub |

---

## 🚀 Getting Started (Local Development)

### Prerequisites

- XAMPP (or any LAMP/WAMP stack) with PHP 8.x and MySQL 8.x
- Composer (for PHPMailer)
- Git

### Setup

```bash
# 1. Clone the repository
git clone https://github.com/jeevantjr/vmsrdhstrinco.git
cd vmsrdhstrinco

# 2. Move to your XAMPP htdocs folder
cp -r . /xampp/htdocs/vms

# 3. Install PHP dependencies
composer install

# 4. Create the database
# Open phpMyAdmin → Create database: vms_db
# Import: database/vms_schema.sql

# 5. Configure database connection
cp config/config.example.php config/config.php
# Edit config/config.php with your DB credentials

# 6. Configure email (OTP + alerts)
# Edit config/mail.php with your SMTP details

# 7. Start Apache + MySQL in XAMPP Control Panel
# Visit: http://localhost/vms
```

### Default Admin Login

```
URL:      http://localhost/vms/login.php
Username: admin@example.com
Password: (set during installation)
Note:     OTP will be sent to configured admin email
```

---

## 📁 Repository Structure

```
vmsrdhstrinco/
│
├── index.html                  # Public showcase page
├── vms_dashboard.html          # Live fleet dashboard (demo)
│
├── config/
│   ├── config.example.php      # DB connection template (copy → config.php)
│   └── mail.php                # PHPMailer SMTP configuration
│
├── database/
│   └── vms_schema.sql          # Full database schema (all 10 entities)
│
├── modules/
│   ├── auth/                   # Login, OTP, password reset
│   ├── vehicles/               # Vehicle CRUD operations
│   ├── fuel/                   # Fuel log management
│   ├── maintenance/            # Service record management
│   ├── compliance/             # Insurance, licence tracking
│   ├── reports/                # PDF and XLS report generation
│   └── notifications/          # Alert engine and email dispatch
│
├── includes/
│   ├── header.php              # Global nav header
│   ├── footer.php              # Global footer
│   └── auth_check.php          # RBAC middleware
│
├── assets/
│   ├── css/                    # Stylesheets
│   └── js/                     # Scripts and chart configurations
│
├── vendor/                     # Composer packages (gitignored)
├── uploads/                    # User-uploaded documents (gitignored)
├── .gitignore
└── README.md
```

---

## 🔭 Future Roadmap

| Feature | Description |
|---|---|
| 📍 GPS Tracking | Real-time vehicle location via Google Maps API |
| 📱 Mobile App | Native companion app for field officers |
| 🤖 Predictive AI | AI-powered maintenance scheduling and anomaly detection |
| ☁️ Cloud Hosting | Migrate from on-premise XAMPP to cloud infrastructure |
| 💾 Auto Backup | Scheduled daily database backup with restore workflow |
| 🏛 Gov API Integration | Connect with national transport authority API for licence verification |
| 📊 AI Fleet Analytics | Natural language fleet query and trend forecasting |
| 🌐 Multi-language | Tamil and Sinhala interface support (i18n) |

---

## ⚠️ Important Notes

- **Demo data**: All vehicle registrations, records, and figures shown in the live dashboard are entirely fictitious and for demonstration purposes only.
- **Live system**: The actual deployed version manages real fleet data within a secured institutional network and is not publicly accessible.
- **Credentials**: The `config/config.php` file (database credentials) and `uploads/` directory are listed in `.gitignore` and must never be committed.

---

## 📄 License

MIT License — free to adapt for educational, research, or healthcare fleet management use cases.  
See [LICENSE](LICENSE) for full terms.

---

## 👨‍💻 Developer

<table>
  <tr>
    <td width="120" align="center">
      <img src="https://drjeevaraj.com/T. Jeevaraj.jpg" width="96" height="96" style="border-radius:50%; object-fit:cover;" alt="Dr. T. Jeevaraj" />
    </td>
    <td>
      <strong>Dr. Thangarasa Jeevaraaj (Dr. T. Jeevaraj)</strong><br/>
      MBBS · MCGP · MSc Biomedical Informatics<br/>
      MD Trainee, Health Informatics · PGIM, University of Colombo · Sri Lanka<br/><br/>
      <a href="https://drjeevaraj.com">🌐 Website</a> &nbsp;|&nbsp;
      <a href="https://drjeevaraj.com/cv.html">📄 CV</a> &nbsp;|&nbsp;
      <a href="https://drjeevaraj.com/dev.html">💻 Dev Portfolio</a> &nbsp;|&nbsp;
      <a href="https://www.linkedin.com/in/geevanathy/">LinkedIn</a> &nbsp;|&nbsp;
      <a href="https://x.com/drjeevaraj">X / Twitter</a> &nbsp;|&nbsp;
      <a href="mailto:tjeevaraj78@gmail.com">Email</a>
    </td>
  </tr>
</table>

---

## 🗂 Other Projects

| Project | Description | Link |
|---|---|---|
| 🌊 FloodTrackerApp | Community resilience PWA (flood, health, education incident reporting) | [GitHub](https://github.com/jeevantjr/FloodTrackerApp) |
| 🦠 OutbreakWatch | Community health early warning system PWA (disease surveillance) | [GitHub](https://github.com/jeevantjr/OutbreakWatch) |

---

## 🙏 Acknowledgements

- [PHPMailer](https://github.com/PHPMailer/PHPMailer) — SMTP email library
- [FPDF](http://www.fpdf.org) / [TCPDF](https://tcpdf.org) — PHP PDF generation
- [Chart.js](https://www.chartjs.org) — Interactive charts
- [Tailwind CSS](https://tailwindcss.com) — Utility-first CSS framework
- [Lucide Icons](https://lucide.dev) — Icon library
- [XAMPP](https://www.apachefriends.org) — Local development stack

---

<p align="center">
  Built with ❤️ by <a href="https://drjeevaraj.com"><strong>Dr. T. Jeevaraj</strong></a> &nbsp;·&nbsp;
  <a href="https://drjeevaraj.com/cv.html">CV</a> &nbsp;·&nbsp;
  <a href="https://drjeevaraj.com/dev.html">Portfolio</a>
</p>
