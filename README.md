# SNS - Student Notes System

SNS (Student Notes System) is a Flask-based web application being developed to help students manage their notes and files in one place.

The project currently includes user registration, email OTP verification, password hashing, MySQL database setup, and the basic frontend pages. Notes and file-management features are planned next.

## Current Progress

| Feature | Status |
|---|---|
| Flask project setup | Completed |
| Home page | Completed |
| Registration page | Completed |
| Email duplicate check | Completed |
| OTP generation | Completed |
| OTP sent through email | Completed |
| OTP verification | Completed |
| Password hashing with bcrypt | Completed |
| User registration in MySQL | Completed |
| MySQL table creation | Completed |
| Login page UI | Completed |
| Login authentication backend | In progress |
| Routes package | Created |
| Notes management | Planned |
| File upload/management | Planned |
| User dashboard | Planned |

## Tech Stack

- Python
- Flask
- MySQL
- HTML
- CSS
- Jinja2
- bcrypt
- Python `smtplib`
- `python-dotenv`
- MySQL Connector/Python

## Current Project Structure

```text
SNS/
│
├── app.py
├── utils.py
├── requirements.txt
├── README.md
├── .env
│
├── database/
│   ├── __init__.py
│   ├── connection.py
│   ├── tables.py
│   └── utilsDB.py
│
├── routes/
│   └── __init__.py
│
├── static/
│   └── css/
│       └── style.css
│
└── templates/
    ├── base.html
    ├── home.html
    ├── login.html
    ├── register.html
    └── verifyotp.html
```

## Database Structure

The application currently creates three MySQL tables.

### `users`
Stores registered user information.

Main fields:

- `userid`
- `username`
- `email`
- `hashpassword`
- `is_active`
- `created_at`

### `notes`
Designed to store notes created by each user.

Main fields:

- `notesid`
- `userid`
- `title`
- `content`
- `created_at`
- `updated_at`

### `files`
Designed to store metadata for uploaded files.

Main fields:

- `fileid`
- `userid`
- `originalname`
- `storedname`
- `mimetype`
- `size`
- `filepath`
- `created_at`

The `notes` and `files` tables use `userid` as a foreign key connected to the `users` table.

## Registration Flow

The registration process currently works like this:

```text
Register
   ↓
Enter username, email and password
   ↓
Check whether passwords match
   ↓
Check whether email already exists
   ↓
Generate a 4-digit OTP
   ↓
Send OTP to the registered email
   ↓
Store temporary registration data in Flask session
   ↓
Verify OTP
   ↓
Hash password using bcrypt
   ↓
Insert user into MySQL
   ↓
Redirect to Login
```

## Email OTP

OTP emails are sent using Gmail SMTP.

Create a `.env` file in the project root with values like:

```env
sender_email=your_email@gmail.com
passkey=your_gmail_app_password
```

Use a Gmail App Password instead of your normal Gmail password.

## MySQL Setup

Make sure MySQL Server is running.

Create the database before starting the application:

```sql
CREATE DATABASE sns_management2;
```

Then update the MySQL connection details in:

```text
database/connection.py
```

The application automatically creates the required tables when `app.py` starts.

## Run the Project on Windows

Open CMD inside the project folder.

### 1. Create a virtual environment

```cmd
python -m venv .venv
```

### 2. Activate it

```cmd
.venv\Scripts\activate
```

### 3. Install dependencies

```cmd
pip install -r requirements.txt
```

### 4. Start MySQL

Make sure the MySQL service is running and the `sns_management2` database exists.

### 5. Run Flask

```cmd
python app.py
```

Then open:

```text
http://127.0.0.1:5000/
```

## Available Routes

| Route | Method | Purpose |
|---|---|---|
| `/` | GET | Home page |
| `/register` | GET, POST | User registration |
| `/verify-otp` | GET, POST | OTP verification |
| `/login` | GET, POST | Login page; backend authentication is still in progress |

## Security

Do not push sensitive or generated files to GitHub.

Recommended `.gitignore` entries:

```gitignore
.env
.venv/
sns_env/
__pycache__/
*.pyc
```

Database passwords, Gmail App Passwords, Flask secret keys, and other credentials should eventually be moved to environment variables instead of being stored directly in Python files.

## Next Steps

Planned development includes:

1. Complete login authentication using email and hashed-password validation.
2. Add logout and session-based authentication.
3. Move authentication routes into the `routes` package.
4. Create the student dashboard.
5. Add create, view, edit, and delete note functionality.
6. Add file upload, download, and delete functionality.
7. Improve form validation and user-facing error messages.
8. Improve the frontend styling and responsive design.
9. Move all credentials and secret configuration into `.env`.

## Project Status

This project is currently under development. The authentication registration flow is partially completed, while the main Notes and Files management features will be added in later stages.

## Author

**Manusha M**

GitHub: `Manusha-M`

---

Built as a learning project using Flask and MySQL.
