# 🩸 Blood Bank Management System

![Python](https://img.shields.io/badge/Python-3.7%2B-blue) ![Django](https://img.shields.io/badge/Django-3.0.5-green) ![SQLite](https://img.shields.io/badge/SQLite-3-lightgrey) ![Status](https://img.shields.io/badge/Status-Active-success)

> A comprehensive web-based blood bank management system built with Django framework. Streamlines blood donation, inventory management, and blood request processing with role-based access for Admin, Donors, and Patients.

## 📋 Overview

The Blood Bank Management System enables efficient management of blood donation activities with:

- **Multi-User System**: Separate interfaces for Admin, Donors, and Patients
- **Blood Inventory Management**: Real-time tracking of blood stock by blood group
- **Donation Tracking**: Complete donation history and approval workflow
- **Request Management**: Blood request processing with approval/rejection system
- **Profile Management**: User profiles with profile pictures and personal information
- **Dashboard Analytics**: Visual representation of key metrics and statistics

## ✨ Features

### 🎯 Admin Panel

- **Dashboard Overview**
  - Total donors, patients, blood requests, and approved donations count
  - Blood stock status for all blood groups (A+, A-, B+, B-, O+, O-, AB+, AB-)
  
- **Donor Management**
  - View all registered donors
  - Update donor information
  - Delete donor records
  - Track donor blood group and contact details

- **Patient Management**
  - View all registered patients
  - Update patient information
  - Delete patient records
  - Track patient medical information

- **Blood Stock Management**
  - View current stock for each blood group
  - Update blood unit quantities
  - Real-time inventory tracking

- **Donation Approval System**
  - Review pending blood donations
  - Approve/reject donation requests
  - Automatic stock updates upon approval
  - Donation history tracking

- **Request Processing**
  - View pending blood requests
  - Approve/reject requests based on stock availability
  - Track request history with status
  - Automatic stock deduction on approval

### 💉 Donor Features

- **Registration & Authentication**
  - Secure donor signup with profile creation
  - Login with username/password
  - Profile picture upload

- **Donation Management**
  - Submit blood donation requests
  - View donation history
  - Track donation status (Pending/Approved/Rejected)
  - Date-wise donation tracking

- **Blood Request Services**
  - Make blood requests for others
  - View personal request history
  - Track request status

- **Dashboard**
  - Personal donation statistics
  - Request made count
  - Pending/Approved donation overview

### 🏥 Patient Features

- **Registration & Authentication**
  - Patient signup with medical information
  - Secure login system
  - Profile management with picture upload

- **Blood Request System**
  - Submit blood requests with medical details
  - Specify blood group, units required, and reason
  - View request status (Pending/Approved/Rejected)
  - Track request history

- **Dashboard**
  - Request statistics
  - Pending requests count
  - Approved requests tracking

### 🔐 Security & Access Control

- Role-based authentication (Admin, Donor, Patient)
- Secure password handling
- Session management
- CSRF protection
- User-specific data access

## 🚀 Quick Start

### Prerequisites

- Python 3.7+
- pip package manager
- Virtual environment (recommended)

### Installation

1. **Clone the repository**

```bash
git clone https://github.com/yourusername/blood-bank-management.git
cd blood-bank-management
```

2. **Create virtual environment** (Optional but recommended)

```bash
python -m venv venv
# Windows
venv\Scripts\activate
# Linux/Mac
source venv/bin/activate
```

3. **Install dependencies**

```bash
pip install -r requirements.txt
```

4. **Apply database migrations**

```bash
python manage.py makemigrations
python manage.py migrate
```

5. **Create superuser (Admin)**

```bash
python manage.py createsuperuser
```

Follow the prompts to create an admin account.

6. **Run the development server**

```bash
python manage.py runserver
```

7. **Access the application**

- Main application: `http://localhost:8000`
- Admin panel: `http://localhost:8000/admin`
- Admin dashboard: `http://localhost:8000/admin-dashboard`
- Donor signup: `http://localhost:8000/donor/donorsignup`
- Patient signup: `http://localhost:8000/patient/patientsignup`

## 🏗️ Architecture

```
┌─────────────────────────────────────┐
│      Django Web Framework           │
│  • URL Routing                      │
│  • Request/Response Handling        │
│  • Template Rendering               │
│  • Authentication & Authorization   │
└──────────────┬──────────────────────┘
               │
┌──────────────▼──────────────────────┐
│         Application Layer           │
│  • blood (Core Management)          │
│  • donor (Donor Module)             │
│  • patient (Patient Module)         │
└──────────────┬──────────────────────┘
               │
┌──────────────▼──────────────────────┐
│          Model Layer                │
│  • Stock (Blood Inventory)          │
│  • BloodRequest (Request Records)   │
│  • Donor (Donor Information)        │
│  • BloodDonate (Donation Records)   │
│  • Patient (Patient Information)    │
└──────────────┬──────────────────────┘
               │
┌──────────────▼──────────────────────┐
│         Database Layer              │
│  • SQLite3 Database                 │
│  • User Authentication Tables       │
│  • Session Management               │
└─────────────────────────────────────┘
```

## 🛠️ Technology Stack

| Component | Technology |
|-----------|-----------|
| Backend Framework | Django 3.0.5 |
| Language | Python 3.7+ |
| Database | SQLite3 |
| Frontend | HTML5, CSS3, Bootstrap |
| Template Engine | Django Templates |
| Form Handling | django-widget-tweaks 1.4.8 |
| Authentication | Django Auth System |
| Static Files | Django Static Files |

## 📁 Project Structure

```
blood-bank-management/
├── manage.py                        # Django management script
├── requirements.txt                 # Python dependencies
├── Procfile.txt                     # Deployment configuration
├── db.sqlite3                       # SQLite database
│
├── bloodbankmanagement/            # Main project directory
│   ├── __init__.py
│   ├── settings.py                 # Project settings
│   ├── urls.py                     # Main URL configuration
│   ├── wsgi.py                     # WSGI configuration
│   └── asgi.py                     # ASGI configuration
│
├── blood/                          # Core blood management app
│   ├── __init__.py
│   ├── admin.py                    # Admin configurations
│   ├── apps.py                     # App configuration
│   ├── forms.py                    # Blood & Request forms
│   ├── views.py                    # Core view functions
│   ├── models.py                   # Stock & BloodRequest models
│   └── migrations/                 # Database migrations
│       ├── 0001_initial.py
│       ├── 0002_bloodrequest.py
│       ├── 0003_auto_20210213_1053.py
│       └── 0004_bloodrequest_date.py
│
├── donor/                          # Donor management app
│   ├── __init__.py
│   ├── admin.py
│   ├── apps.py
│   ├── forms.py                    # Donor & Donation forms
│   ├── views.py                    # Donor view functions
│   ├── models.py                   # Donor & BloodDonate models
│   ├── urls.py                     # Donor URL patterns
│   └── migrations/                 # Database migrations
│       ├── 0001_initial.py
│       └── 0002_auto_20210213_1602.py
│
├── patient/                        # Patient management app
│   ├── __init__.py
│   ├── admin.py
│   ├── apps.py
│   ├── forms.py                    # Patient forms
│   ├── views.py                    # Patient view functions
│   ├── models.py                   # Patient model
│   ├── urls.py                     # Patient URL patterns
│   └── migrations/                 # Database migrations
│       └── 0001_initial.py
│
├── static/                         # Static files
│   ├── css/
│   │   ├── main.css               # Main stylesheet
│   │   └── main.min.css           # Minified CSS
│   ├── image/                      # Application images
│   ├── profile_pic/                # User profile pictures
│   │   ├── Donor/                 # Donor profile pics
│   │   └── Patient/               # Patient profile pics
│   ├── screenshot/                 # Application screenshots
│   └── vendor/                     # Third-party libraries
│       └── select2/
│           ├── select2.min.css
│           └── select2.min.js
│
└── templates/                      # HTML templates
    ├── blood/                      # Admin templates
    │   ├── adminbase.html         # Admin base template
    │   ├── adminlogin.html        # Admin login page
    │   ├── admin_dashboard.html   # Admin dashboard
    │   ├── admin_blood.html       # Blood stock management
    │   ├── admin_donor.html       # Donor management
    │   ├── admin_patient.html     # Patient management
    │   ├── admin_donation.html    # Donation approval
    │   ├── admin_request.html     # Request approval
    │   ├── admin_request_history.html
    │   ├── update_donor.html      # Update donor info
    │   ├── update_patient.html    # Update patient info
    │   ├── index.html             # Home page
    │   ├── navbar.html            # Navigation bar
    │   ├── footer.html            # Footer
    │   └── logout.html            # Logout page
    │
    ├── donor/                      # Donor templates
    │   ├── donorbase.html         # Donor base template
    │   ├── donorlogin.html        # Donor login page
    │   ├── donorsignup.html       # Donor registration
    │   ├── donor_dashboard.html   # Donor dashboard
    │   ├── donate_blood.html      # Donation form
    │   ├── donation_history.html  # Donation history
    │   ├── makerequest.html       # Blood request form
    │   └── request_history.html   # Request history
    │
    └── patient/                    # Patient templates
        ├── patientbase.html       # Patient base template
        ├── patientlogin.html      # Patient login page
        ├── patientsignup.html     # Patient registration
        ├── patient_dashboard.html # Patient dashboard
        ├── makerequest.html       # Blood request form
        └── my_request.html        # Request tracking
```

## 📊 Database Schema

### Models Overview

#### Stock (Blood Inventory)
```python
- id: AutoField (Primary Key)
- bloodgroup: CharField (A+, A-, B+, B-, O+, O-, AB+, AB-)
- unit: PositiveIntegerField (Units in ml)
```

#### BloodRequest
```python
- id: AutoField (Primary Key)
- patient_name: CharField
- patient_age: PositiveIntegerField
- reason: CharField (Medical reason)
- bloodgroup: CharField
- unit: PositiveIntegerField (Units required)
- status: CharField (Pending/Approved/Rejected)
- date: DateField (Request date)
- request_by_donor: ForeignKey (Donor) [Optional]
- request_by_patient: ForeignKey (Patient) [Optional]
```

#### Donor
```python
- id: AutoField (Primary Key)
- user: OneToOneField (User)
- profile_pic: ImageField
- bloodgroup: CharField
- address: CharField
- mobile: CharField
```

#### BloodDonate (Donation Records)
```python
- id: AutoField (Primary Key)
- donor: ForeignKey (Donor)
- disease: CharField
- age: PositiveIntegerField
- bloodgroup: CharField
- unit: PositiveIntegerField
- status: CharField (Pending/Approved/Rejected)
- date: DateField (Donation date)
```

#### Patient
```python
- id: AutoField (Primary Key)
- user: OneToOneField (User)
- profile_pic: ImageField
- age: PositiveIntegerField
- bloodgroup: CharField
- disease: CharField
- doctorname: CharField
- address: CharField
- mobile: CharField
```

## 📖 Usage Guide

### For Admin Users

1. **Login**
   - Navigate to `/adminlogin`
   - Use superuser credentials

2. **Manage Blood Stock**
   - Access "Blood Stock" from dashboard
   - View current inventory for all blood groups
   - Update units as needed

3. **Approve Donations**
   - Navigate to "Donations"
   - Review pending donation requests
   - Approve: Adds units to stock
   - Reject: Updates status without stock change

4. **Process Blood Requests**
   - View "Blood Requests" section
   - Check stock availability
   - Approve: Deducts units from stock
   - Reject: Updates status without stock change

5. **Manage Users**
   - View all donors and patients
   - Update user information
   - Delete user accounts if needed

### For Donor Users

1. **Registration**
   - Visit `/donor/donorsignup`
   - Fill in personal details
   - Upload profile picture
   - Select blood group
   - Create username and password

2. **Make Donation**
   - Login to donor dashboard
   - Click "Donate Blood"
   - Enter donation details (age, disease, units)
   - Submit for admin approval

3. **Request Blood**
   - Navigate to "Make Request"
   - Fill patient details (name, age, blood group)
   - Specify reason and units needed
   - Track request status

4. **View History**
   - Check donation history
   - Track request history
   - Monitor approval status

### For Patient Users

1. **Registration**
   - Visit `/patient/patientsignup`
   - Provide medical information
   - Enter doctor details
   - Upload profile picture
   - Create credentials

2. **Request Blood**
   - Login to patient dashboard
   - Click "Make Request"
   - Fill request form with medical details
   - Submit for admin review

3. **Track Requests**
   - View "My Requests"
   - Check approval status
   - See request history with dates

## 🔮 Future Enhancements

- [ ] SMS/Email notifications for request approvals
- [ ] Blood camp management module
- [ ] Donor eligibility checker (last donation date)
- [ ] Emergency blood request feature
- [ ] Blood bank location mapping
- [ ] Multi-blood bank network
- [ ] Mobile application (iOS/Android)
- [ ] Donor rewards and badges system
- [ ] Advanced analytics and reporting
- [ ] Blood expiry date tracking
- [ ] Appointment scheduling system
- [ ] Integration with hospital systems
- [ ] QR code for donor verification
- [ ] Real-time stock alerts
- [ ] Multi-language support
- [ ] API for third-party integration
- [ ] Advanced search and filtering
- [ ] Export reports to PDF/Excel
- [ ] Payment integration for voluntary contributions
- [ ] Social media integration for awareness campaigns

## 🔧 Configuration

### Email Configuration (Optional)

To enable contact form email functionality, update `settings.py`:

```python
EMAIL_BACKEND = 'django.core.mail.backends.smtp.EmailBackend'
EMAIL_HOST = 'smtp.gmail.com'
EMAIL_USE_TLS = True
EMAIL_PORT = 587
EMAIL_HOST_USER = 'your-email@gmail.com'
EMAIL_HOST_PASSWORD = 'your-app-password'
EMAIL_RECEIVING_USER = ['recipient@gmail.com']
```

**Note**: Enable "Less secure app access" for Gmail or use App Passwords.

### Production Deployment

1. **Update settings.py**
```python
DEBUG = False
ALLOWED_HOSTS = ['yourdomain.com', 'www.yourdomain.com']
SECRET_KEY = 'your-secure-secret-key'  # Change this!
```

2. **Collect static files**
```bash
python manage.py collectstatic
```

3. **Use production database** (PostgreSQL recommended)
```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'bloodbank_db',
        'USER': 'dbuser',
        'PASSWORD': 'password',
        'HOST': 'localhost',
        'PORT': '5432',
    }
}
```

4. **Deploy with Gunicorn** (Update Procfile)
```
web: gunicorn bloodbankmanagement.wsgi --log-file -
```

## 🔧 Troubleshooting

**Issue: Module import errors**
```bash
pip install -r requirements.txt
```

**Issue: Database errors**
```bash
python manage.py makemigrations
python manage.py migrate
```

**Issue: Static files not loading**
```bash
python manage.py collectstatic
# Ensure STATIC_URL and STATICFILES_DIRS are configured
```

**Issue: Profile picture upload errors**
```bash
# Ensure media directories exist
mkdir -p static/profile_pic/Donor
mkdir -p static/profile_pic/Patient
```

**Issue: Permission denied on migrations**
```bash
python manage.py migrate --run-syncdb
```

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

**Contribution Guidelines:**

- Follow PEP 8 style guide for Python code
- Add docstrings to all functions and classes
- Write meaningful commit messages
- Update documentation as needed
- Test thoroughly before submitting PR
- Include screenshots for UI changes

## 🙏 Acknowledgments

- Built with Django web framework
- Bootstrap for responsive UI design
- Font Awesome for icons
- Select2 for enhanced dropdowns
- Inspired by real-world blood bank management needs

## 📧 Contact

For questions, suggestions, or support:

- Open an issue on GitHub

---

**Disclaimer**: This application is designed for educational and demonstration purposes. For production use in medical facilities, ensure compliance with healthcare regulations, data protection laws (HIPAA, GDPR), and security best practices. Consult with legal and medical professionals before deployment.

---
<div align="center">
  <strong>Made with ❤️ for saving lives | © 2025 Pratyush Srivastava
</strong>
</div>
