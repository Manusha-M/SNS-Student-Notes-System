# SNS - Student Notes System

## Project Overview

The Student Notes System (SNS) is a Flask-based web application designed to help students manage their academic notes in one place. The application provides user registration, email OTP verification, login authentication, password recovery, a student dashboard, and note management.

The project uses Python and Flask for backend development, HTML and CSS for the frontend, and MySQL for database management.

## Features

### 1. User Registration
- Register using a username, email address, and password.
- Validate password and confirm-password fields.
- Check whether an email address is already registered.
- Generate and send a four-digit OTP through email.
- Verify the OTP before completing registration.
- Store user information in MySQL.
- Hash passwords using bcrypt.

### 2. User Login
- Log in using a registered email address and password.
- Validate credentials against the stored user record.
- Verify passwords using password hashing.
- Store user information in the Flask session.
- Redirect authenticated users to the dashboard.

### 3. Email OTP Verification
- Generate a one-time verification code during registration.
- Send the OTP through Gmail SMTP.
- Verify the submitted OTP before creating the account.

### 4. Forgot Password and Password Reset
- Request a password-reset link using a registered email address.
- Generate a time-limited token using ItsDangerous.
- Send the password-reset link through email.
- Validate the token before processing a password reset.
- Hash the new password before updating the database.

### 5. Student Dashboard
- Display the dashboard after successful login.
- Display the logged-in user's information.
- Provide navigation to the notes section.

### 6. Notes Management
- View notes associated with the logged-in user.
- Create notes with a title and content.
- Store notes in the MySQL database.
- View individual notes.
- Associate notes with the corresponding user account.

## Technologies Used

| Technology | Purpose |
|---|---|
| Python | Backend programming |
| Flask | Web application framework |
| MySQL | Database management |
| HTML5 | Web page structure |
| CSS3 | Styling and layout |
| Jinja2 | Dynamic HTML templates |
| MySQL Connector/Python | Database connectivity |
| bcrypt | Password hashing |
| ItsDangerous | Password-reset tokens |
| smtplib | Sending email messages |
| python-dotenv | Environment variable management |
| Git | Version control |
| GitHub | Source code hosting |

## Project Structure

```text
SNS/
│
├── app.py
├── utils.py
├── requirements.txt
├── README.md
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
    ├── verifyotp.html
    ├── forgot_password.html
    ├── reset_password.html
    ├── dashboard.html
    ├── notes.html
    ├── new_notes.html
    └── view_notes.html
```

The structure above represents the main project files. Update the tree if your local project contains additional files or different filenames.

## Prerequisites

Before running the application, install the following:

- Python 3.10 or a compatible version
- MySQL Server
- Git
- A Gmail account with an App Password for email functionality

## Installation and Setup

### Step 1: Clone the Repository

```bash
git clone https://github.com/Manusha-M/SNS-Student-Notes-System.git
```

### Step 2: Navigate to the Project Directory

```bash
cd SNS-Student-Notes-System
```

### Step 3: Create a Virtual Environment

On Windows:

```bash
python -m venv .venv
```

### Step 4: Activate the Virtual Environment

For Windows Command Prompt:

```cmd
.venv\Scripts\activate
```

For Git Bash:

```bash
source .venv/Scripts/activate
```

### Step 5: Install Dependencies

```bash
pip install -r requirements.txt
```

### Step 6: Configure the MySQL Database

Start the MySQL server and create the database configured in your application.

For example:

```sql
CREATE DATABASE sns_management2;
```

Check `database/connection.py` and use the exact database name and connection credentials expected by your application.

Ensure that the MySQL user has the necessary permissions to create and access tables.

### Step 7: Configure Environment Variables

Create a `.env` file in the project root and add the environment variables expected by your application.

Example:

```env
sender_email=your_email@gmail.com
passkey=your_gmail_app_password
```

Use a Gmail App Password instead of your regular Gmail password. The variable names must match those referenced in your code.

Keep `.env` out of version control.

### Step 8: Run the Application

```bash
python app.py
```

Open the following URL in your browser:

```text
http://127.0.0.1:5000/
```

## Application Routes

| Route | HTTP Method | Purpose |
|---|---|---|
| `/` | GET | Home page |
| `/register` | GET, POST | User registration |
| `/verify-otp` | GET, POST | Email OTP verification |
| `/login` | GET, POST | User login |
| `/forgot-password` | GET, POST | Request a password-reset link |
| `/reset-password/<token>` | GET, POST | Reset password using a token |
| `/dashboard` | GET | Student dashboard |
| `/dashboard/notes` | GET | View notes |
| `/dashboard/notes/new-notes` | GET, POST | Create a new note |
| `/dashboard/notes/view/<int:id>` | GET | View an individual note |

The routes listed above should be checked against the actual route definitions in the application before publication.

## Database

The application uses MySQL to store user accounts and notes.

### Users Table

The users table stores account information, such as:

- User ID
- Username
- Email address
- Hashed password
- Account status, if configured
- Account creation timestamp, if configured

### Notes Table

The notes table stores academic notes, such as:

- Note ID
- User ID
- Note title
- Note content
- Creation timestamp, if configured
- Update timestamp, if configured

Each note should be associated with its owner through the user ID.

## Application Workflow

```text
Home Page
    |
    v
User Registration
    |
    v
Email OTP Verification
    |
    v
Account Creation
    |
    v
User Login
    |
    v
Student Dashboard
    |
    v
View Notes or Create Notes
    |
    v
View Individual Note
```

Users can also use the password-recovery functionality if they forget their passwords.

## Security Considerations

- Hash passwords before storing them in the database.
- Use time-limited password-reset tokens.
- Store database credentials and email passwords in environment variables.
- Store the Flask secret key securely in an environment variable.
- Exclude `.env`, virtual environments, and other sensitive files from GitHub.
- Protect dashboard and notes routes with appropriate session checks.
- Ensure users can access only their own notes.
- Disable Flask debug mode in production.

## Project Status

| Module | Status |
|---|---|
| Flask application setup | Implemented |
| Home page | Implemented |
| User registration | Implemented |
| Duplicate email validation | Implemented |
| Email OTP verification | Implemented |
| Password hashing | Implemented |
| MySQL integration | Implemented |
| User login | Implemented |
| Session management | Implemented |
| Forgot password | Implemented |
| Password reset using tokens | Implemented |
| Student dashboard | Implemented |
| View notes | Implemented |
| Create notes | Implemented |
| View individual notes | Implemented |
| Edit and delete notes | Future enhancement |
| File upload and download | Future enhancement |
| Deployment | Future enhancement |

The status should be confirmed through testing of each feature before the project is considered production-ready.

## Future Enhancements

- Add note editing and deletion.
- Implement file uploads and downloads.
- Improve session management and logout functionality.
- Add note search and filtering.
- Improve form validation and error handling.
- Enhance the responsive user interface.
- Deploy the application to a hosting platform.

## Author

**Manusha M**

GitHub: https://github.com/Manusha-M

## License

This project is developed as a learning project. A suitable open-source license can be added if the project is intended for public distribution or reuse.
