# 🔐 Login Attempt Control System

A Python-based authentication control mechanism that protects user accounts from repeated failed login attempts. The system tracks failed attempts, applies progressive delays, and temporarily locks an account after five consecutive failed login attempts.

## 🎯 Objective

The objective of this project is to implement:

- Failed login attempt tracking
- Username and IP address logging
- Progressive login delays
- Temporary account lockout after 5 consecutive failures
- 15-minute account lockout
- Security audit logging
- Testing against simulated repeated failed login attempts

## ✨ Features

- 🔑 Password-based authentication
- 🔢 Failed login attempt counter
- 🌐 IP address tracking in audit logs
- ⏱️ Progressive delay after failed attempts
- 🔒 Automatic account lockout after 5 consecutive failures
- 🕐 15-minute temporary lockout
- 📝 Security audit logging
- 💾 Saves audit events to `audit_log.txt`
- 🧪 Includes an automated test demonstrating lockout enforcement

## 🛠️ Technologies Used

- **Python 3**
- `datetime` module
- `time` module
- File handling
- In-memory data storage

## 📂 Project Structure

```text
Login_Attempt_Control_System/
│
├── login_control.py
├── audit_log.txt
└── README.md
```

## ⚙️ Security Rules

The application uses the following rules:

| Rule | Value |
|---|---|
| Maximum failed attempts | 5 |
| Lockout duration | 15 minutes |
| Progressive delay | Increases after each failed attempt |
| Successful login | Resets failed-attempt counter |
| Lockout event | Recorded in audit log |

## 🚀 How to Run

### 1. Install Python

Make sure Python 3 is installed.

Check the installation:

```bash
python --version
```

### 2. Open the Project Folder

Open a terminal or command prompt in the project directory.

### 3. Run the Program

```bash
python login_control.py
```

## 🧪 Automated Test

The program includes a `run_test()` function that simulates five consecutive incorrect passwords.

The test uses:

```text
Username: admin
IP Address: 192.168.1.100
Incorrect Password: WrongPassword
```

The correct password configured for the demonstration account is:

```text
SecurePass123!
```

The test performs five failed login attempts and then attempts another login using the correct password.

## 💻 Example Test Output

```text
=================================================================
LOGIN ATTEMPT CONTROL SYSTEM - SECURITY TEST
=================================================================

Simulating 5 consecutive incorrect passwords...


--- Test Attempt 1 ---
2026-09-23 20:30:01 | User: admin | IP: 192.168.1.100 | LOGIN FAILED - Failed attempt 1/5
2026-09-23 20:30:01 | User: admin | IP: 192.168.1.100 | Progressive delay: 1 second(s)

--- Test Attempt 2 ---
2026-09-23 20:30:02 | User: admin | IP: 192.168.1.100 | LOGIN FAILED - Failed attempt 2/5
2026-09-23 20:30:02 | User: admin | IP: 192.168.1.100 | Progressive delay: 2 second(s)

--- Test Attempt 3 ---
2026-09-23 20:30:04 | User: admin | IP: 192.168.1.100 | LOGIN FAILED - Failed attempt 3/5
2026-09-23 20:30:04 | User: admin | IP: 192.168.1.100 | Progressive delay: 3 second(s)

--- Test Attempt 4 ---
2026-09-23 20:30:07 | User: admin | IP: 192.168.1.100 | LOGIN FAILED - Failed attempt 4/5
2026-09-23 20:30:07 | User: admin | IP: 192.168.1.100 | Progressive delay: 4 second(s)

--- Test Attempt 5 ---
2026-09-23 20:30:11 | User: admin | IP: 192.168.1.100 | LOGIN FAILED - Failed attempt 5/5
2026-09-23 20:30:11 | User: admin | IP: 192.168.1.100 | ACCOUNT LOCKED - Locked for 15 minutes

=================================================================
TESTING LOGIN AFTER ACCOUNT LOCKOUT
=================================================================

Attempting login using the correct password...

2026-09-23 20:30:11 | User: admin | IP: 192.168.1.100 | LOGIN BLOCKED - Account locked (14 minutes remaining)

Audit log saved to audit_log.txt
```

> The timestamps above are example output. Your actual timestamps will be different when you run the program.

## 📄 Audit Log

The application creates an `audit_log.txt` file containing security events.

Example:

```text
2026-09-23 20:30:01 | User: admin | IP: 192.168.1.100 | LOGIN FAILED - Failed attempt 1/5
2026-09-23 20:30:02 | User: admin | IP: 192.168.1.100 | LOGIN FAILED - Failed attempt 2/5
2026-09-23 20:30:04 | User: admin | IP: 192.168.1.100 | LOGIN FAILED - Failed attempt 3/5
2026-09-23 20:30:07 | User: admin | IP: 192.168.1.100 | LOGIN FAILED - Failed attempt 4/5
2026-09-23 20:30:11 | User: admin | IP: 192.168.1.100 | LOGIN FAILED - Failed attempt 5/5
2026-09-23 20:30:11 | User: admin | IP: 192.168.1.100 | ACCOUNT LOCKED - Locked for 15 minutes
2026-09-23 20:30:11 | User: admin | IP: 192.168.1.100 | LOGIN BLOCKED - Account locked
```

## 🔄 How It Works

1. The user provides a username, password, and IP address.
2. The system checks whether the username exists.
3. The system checks whether the account is currently locked.
4. If the account is locked, login attempts are rejected.
5. If the password is incorrect, the failed-attempt counter increases.
6. A progressive delay is applied after each failed attempt.
7. After 5 consecutive failures, the account is locked for 15 minutes.
8. The lockout event is recorded for security auditing.
9. A successful login resets the failed-attempt counter.
10. After the lockout period expires, the account can be used again.

## 🔒 Account Lockout Enforcement

The most important security test is the fifth failed attempt:

```text
LOGIN FAILED - Failed attempt 5/5
ACCOUNT LOCKED - Locked for 15 minutes
```

A subsequent login attempt is rejected even when the correct password is supplied:

```text
LOGIN BLOCKED - Account locked
```

This demonstrates that the temporary account lockout is being enforced.

## 📊 Test Results

| Test | Expected Result | Status |
|---|---|---|
| Incorrect password – Attempt 1 | Failure recorded | ✅ Passed |
| Incorrect password – Attempt 2 | Failure recorded | ✅ Passed |
| Incorrect password – Attempt 3 | Failure recorded | ✅ Passed |
| Incorrect password – Attempt 4 | Failure recorded | ✅ Passed |
| Incorrect password – Attempt 5 | Account locked | ✅ Passed |
| Correct password while locked | Login blocked | ✅ Passed |
| Audit logging | Events saved to file | ✅ Passed |

## 🎓 Learning Outcomes

This project demonstrates:

- Authentication concepts
- Brute-force attack protection
- Failed login tracking
- Rate limiting concepts
- Temporary account lockout
- Progressive delays
- Security event logging
- Python dictionaries and functions
- Date and time handling
- File handling
- Basic cybersecurity practices

## 🔮 Future Improvements

Possible improvements include:

- Store users in a database
- Hash passwords instead of storing plain-text demonstration passwords
- Track attempts persistently across application restarts
- Add separate rate limits by IP address and username
- Add an administrator dashboard
- Send security alerts after repeated failures
- Use a configurable lockout duration
- Add unit tests
- Build a web-based login interface

## ⚠️ Security Note

This project is an educational demonstration of login-attempt controls.

The example stores a demonstration password in memory for simplicity. A production authentication system should never store passwords in plain text. It should use a suitable password-hashing mechanism, secure session management, appropriate rate limiting, and protected audit logs.

## 📸 Submission Proof

For project submission, include:

1. Source code: `login_control.py`
2. Execution screenshot showing five failed attempts
3. Execution output showing:

```text
ACCOUNT LOCKED - Locked for 15 minutes
```

4. Output showing a subsequent login being blocked
5. `audit_log.txt`

## 👨‍💻 Author

**Your Name**

GitHub:

```text
https://github.com/YOUR-USERNAME
```

Replace the author name and GitHub username with your details.

## 📌 Project Status

**Completed — Educational Cybersecurity Project**
