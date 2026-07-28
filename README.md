# Secure Coding Review

A Python-based Secure Coding Review project that demonstrates how to identify security vulnerabilities in a web application using **Bandit**, a static application security testing (SAST) tool. The project intentionally includes insecure code to demonstrate common security issues and how they can be detected.

---

## Project Objective

The objective of this project is to:

* Perform a secure code review on a Python Flask application.
* Identify common security vulnerabilities.
* Analyze Bandit scan results.
* Recommend secure coding practices.
* Improve application security through remediation.

---

## Technologies Used

* Python 3.13.x
* Flask
* Bandit
* SQLite3
* macOS Terminal

---

## Project Structure

```text
SecureCodingReview/
│
├── venv/
├── login.py
├── requirements.txt
├── README.md
└── report.md
```

---

## Features

* Flask-based login application
* Static security analysis using Bandit
* Detection of SQL Injection vulnerability
* Detection of Flask Debug Mode vulnerability
* Security recommendations
* Secure coding best practices

---

## Prerequisites

* macOS
* Python 3.13 or later
* pip
* Virtual Environment (venv)

---

## Installation

### Clone the repository

```bash
git clone https://github.com/Abhi27-09-star/SecureCodingReview.git
```

### Navigate to the project

```bash
cd SecureCodingReview
```

### Create a virtual environment

```bash
python3 -m venv venv
```

### Activate the virtual environment

```bash
source venv/bin/activate
```

### Install dependencies

```bash
pip install flask bandit
```

### Save installed packages

```bash
pip freeze > requirements.txt
```

---

## Running the Application

```bash
python3 login.py
```

The Flask application starts locally for testing.

---

## Running the Security Scan

Scan a single file:

```bash
bandit login.py
```

Scan the complete project:

```bash
bandit -r .
```

Bandit analyzes the source code and reports potential security vulnerabilities.

---

## Security Vulnerabilities Identified

### 1. SQL Injection (CWE-89)

**Severity:** Medium

Bandit detected SQL queries constructed using Python f-strings.

Example:

```python
query = f"SELECT * FROM users WHERE username='{username}' AND password='{password}'"
```

**Risk**

User input can manipulate SQL queries and gain unauthorized database access.

**Recommendation**

Use parameterized SQL queries.

---

### 2. Flask Debug Mode Enabled (CWE-94)

**Severity:** High

Example:

```python
app.run(debug=True)
```

**Risk**

Running Flask in debug mode exposes the interactive debugger, which can allow arbitrary code execution.

**Recommendation**

Disable debug mode in production.

```python
app.run(debug=False)
```

---

## Sample Bandit Output

Bandit detected the following important issues:

* B608 – Possible SQL Injection
* B201 – Flask Debug Mode Enabled

Additional warnings generated inside the **venv** directory belong to installed third-party libraries and are not part of the project's source code.

---

## Best Practices

* Use parameterized SQL queries.
* Never enable debug mode in production.
* Validate all user input.
* Hash passwords instead of storing plain text.
* Use HTTPS for secure communication.
* Keep dependencies updated.
* Perform regular static code analysis.

---

## Learning Outcomes

After completing this project, you will understand:

* Secure coding principles
* Static Application Security Testing (SAST)
* SQL Injection vulnerabilities
* Flask security practices
* Secure authentication design
* Code auditing techniques

---

## Future Enhancements

* Implement password hashing using bcrypt.
* Add secure session management.
* Implement input validation.
* Integrate automated security scanning into CI/CD.
* Generate HTML and JSON security reports.

---

## Requirements

```text
Python >= 3.13
Flask
Bandit
```

Install dependencies:

```bash
pip install flask bandit
```

---

## Author

**Abbadi Abilash**

---

## License

This project is licensed under the MIT License.

---

## Disclaimer

This project is intended for educational purposes only. The vulnerable code is intentionally included to demonstrate common security issues and should not be used in production environments.
