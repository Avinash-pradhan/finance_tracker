# 💰 Personal Finance Tracker

A production-ready full-stack **Django 4.2** web application for tracking income, expenses, budgets, and financial analytics.

## ✨ Features

| Module             | Capabilities                                                            |
| ------------------ | ----------------------------------------------------------------------- |
| **Authentication** | Register · Login · Logout · Password Change                             |
| **Transactions**   | Add · Edit · Delete · Filter · Search · Pagination                      |
| **Categories**     | 15 predefined global categories + unlimited custom categories           |
| **Budgets**        | Monthly budgets per category · Progress tracking · Email alerts         |
| **Analytics**      | Pie Chart · Monthly Trend · Weekly Spending                             |
| **Exports**        | CSV export · PDF monthly reports                                        |
| **Dashboard**      | Income · Expenses · Net Balance · Budget Progress · Recent Transactions |
| **Admin Panel**    | Django Admin interface for managing application data                    |

---

## 🛠 Tech Stack

* **Backend:** Django 4.2
* **Language:** Python 3.11+
* **Database:** PostgreSQL
* **Frontend:** HTML5 · CSS3 · Bootstrap 5.3 · Vanilla JavaScript
* **Charts:** Google Charts
* **Email:** Django SMTP
* **PDF:** ReportLab
* **CSV:** Python `csv` module
* **Configuration:** `python-decouple`

---

## 🚀 Quick Start

### 1. Clone the Repository

```bash
git clone https://github.com/Avinash-pradhan/finance_tracker.git
cd finance_tracker
```

### 2. Create a Virtual Environment

Windows:

```powershell
python -m venv venv
venv\Scripts\activate
```

Linux/macOS:

```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

---

## 🗄️ PostgreSQL Configuration

This project uses **PostgreSQL** as its database.

Make sure PostgreSQL is installed and running on your system.

Create a database:

```sql
CREATE DATABASE django_db;
```

Create a `.env` file in the project root.

Example:

```env
SECRET_KEY=your-secret-key

DB_NAME=django_db
DB_USER=postgres
DB_PASSWORD=your-postgresql-password
DB_HOST=localhost
DB_PORT=5432
```

> **Important:** Never commit `.env` to GitHub. It contains sensitive credentials.

The project reads database credentials from environment variables instead of storing passwords directly in `settings.py`.

---

## ⚙️ Database Migration

Run:

```bash
python manage.py migrate
```

This creates the required Django and application database tables.

---

## 👤 Create Superuser

Create an admin account:

```bash
python manage.py createsuperuser
```

Then start the development server:

```bash
python manage.py runserver
```

Open:

```text
http://127.0.0.1:8000/
```

Admin panel:

```text
http://127.0.0.1:8000/admin/
```

---

## 📊 Application Modules

### Dashboard

The dashboard provides an overview of:

* Total income
* Total expenses
* Net balance
* Current budget progress
* Recent transactions

### Transactions

Users can:

* Add income
* Add expenses
* Edit transactions
* Delete transactions
* Filter by type
* Filter by category
* Filter by date
* Search transactions
* Navigate through paginated results

### Categories

The application provides predefined categories along with support for custom user categories.

### Budgets

Users can create monthly budgets for categories and monitor spending progress.

Budget alerts are triggered when spending reaches:

* **80%** → Warning
* **100%** → Critical

### Analytics

The application provides visual financial analytics using Google Charts:

* Category spending — Pie Chart
* Monthly income/expense — Line Chart
* Weekly spending — Bar Chart

### Exports

Users can export financial data as:

* CSV
* PDF monthly report

---

## 📧 Email Configuration

### Development

For development, email can be printed directly to the terminal:

```env
EMAIL_BACKEND=django.core.mail.backends.console.EmailBackend
```

### Production

For Gmail SMTP:

```env
EMAIL_BACKEND=django.core.mail.backends.smtp.EmailBackend
EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_USE_TLS=True
EMAIL_HOST_USER=your-email@gmail.com
EMAIL_HOST_PASSWORD=your-gmail-app-password
DEFAULT_FROM_EMAIL=Finance Tracker <your-email@gmail.com>
```

> Use a **Gmail App Password**, not your normal Gmail password.

---

## 🗂️ Project Structure

```text
finance_tracker/
│
├── manage.py
├── requirements.txt
├── .env.example
├── .gitignore
├── README.md
│
├── finance_tracker/
│   ├── settings.py
│   ├── urls.py
│   ├── asgi.py
│   └── wsgi.py
│
├── tracker/
│   ├── models.py
│   ├── forms.py
│   ├── services.py
│   ├── signals.py
│   ├── admin.py
│   ├── apps.py
│   │
│   ├── migrations/
│   │   ├── 0001_initial.py
│   │   ├── 0002_seed_predefined_categories.py
│   │   └── 0003_*.py
│   │
│   ├── views/
│   │   ├── auth_views.py
│   │   ├── dashboard_views.py
│   │   ├── transaction_views.py
│   │   ├── category_views.py
│   │   ├── budget_views.py
│   │   ├── chart_views.py
│   │   ├── analytics_views.py
│   │   └── export_views.py
│   │
│   ├── urls/
│   │   ├── auth_urls.py
│   │   └── app_urls.py
│   │
│   ├── templates/
│   │   └── tracker/
│   │
│   └── management/
│       └── commands/
│
├── templates/
│   ├── base.html
│   ├── registration/
│   └── email/
│
└── static/
    ├── css/
    └── js/
```

---

## 🔗 URL Map

| URL                              | Description            |
| -------------------------------- | ---------------------- |
| `/`                              | Redirects to Dashboard |
| `/auth/register/`                | User Registration      |
| `/auth/login/`                   | User Login             |
| `/auth/logout/`                  | User Logout            |
| `/dashboard/`                    | Main Dashboard         |
| `/analytics/`                    | Financial Analytics    |
| `/transactions/`                 | Transaction List       |
| `/transactions/add/`             | Add Transaction        |
| `/categories/`                   | Category Management    |
| `/budgets/`                      | Budget Management      |
| `/export/csv/`                   | CSV Export             |
| `/export/pdf/`                   | PDF Export             |
| `/api/charts/category-spending/` | Category Spending API  |
| `/api/charts/monthly-trend/`     | Monthly Trend API      |
| `/api/charts/weekly-spending/`   | Weekly Spending API    |
| `/admin/`                        | Django Admin           |

---

## 🔒 Security

The application follows common Django security practices:

* Environment variables for sensitive configuration
* PostgreSQL database
* CSRF protection
* Django password hashing
* Login protection
* User-specific data filtering
* Permission checks for protected objects
* `.env` excluded from Git
* `db.sqlite3` excluded from Git
* `__pycache__` excluded from Git
* Secret credentials are not stored in source code

---

## 🧪 Testing Checklist

After starting the server, verify:

* [ ] User registration works
* [ ] Login/logout works
* [ ] Password change works
* [ ] Income transaction works
* [ ] Expense transaction works
* [ ] Transaction editing works
* [ ] Transaction deletion works
* [ ] Search and filtering work
* [ ] Pagination works
* [ ] Categories work
* [ ] Budgets work
* [ ] 80% budget alert works
* [ ] 100% budget alert works
* [ ] Analytics charts load correctly
* [ ] CSV export works
* [ ] PDF export works
* [ ] Admin panel works
* [ ] Mobile layout works
* [ ] PostgreSQL connection works

---

## 📌 Environment Variables

The following configuration values should be stored in `.env`:

```env
SECRET_KEY=
DB_NAME=
DB_USER=
DB_PASSWORD=
DB_HOST=
DB_PORT=

EMAIL_HOST=
EMAIL_PORT=
EMAIL_USE_TLS=
EMAIL_HOST_USER=
EMAIL_HOST_PASSWORD=
DEFAULT_FROM_EMAIL=
```

Never upload the actual `.env` file to GitHub.

---

## 📄 License

MIT License — free to use, modify, and distribute.

---

## 👨‍💻 Author

**Avinash Pradhan**

GitHub:
https://github.com/Avinash-pradhan

Project Repository:
https://github.com/Avinash-pradhan/finance_tracker
