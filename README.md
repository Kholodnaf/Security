# Security
# Overview

# Steps to run the application (Windows)
1. python -m venv venv
2. venv\Scripts\activate
3. pip install flask flask-sqlalchemy bcrypt
4. python app.py


# How to Test Security Features:
1. SQL Injection Test
Attempt to log in using the following credentials:

Username: ' OR 1=1 --

Password: any value (example: 1)
If the system is vulnerable, it will allow you to log in without valid credentials.

2. Weak Password Storage Test
Check whether passwords are stored in plain text.
Run the following command in the terminal to inspect the user table:

python -c "import sqlite3; conn = sqlite3.connect('instance/database.db'); cursor = conn.cursor(); cursor.execute('SELECT id, username, role FROM user'); rows = cursor.fetchall(); [print(f'ID: {r[0]} | Username: {r[1]} | Role: {r[2]}') for r in rows]; conn.close()"

If the database exposes unhashed passwords or weak storage, it indicates a security flaw.

3. Cross-Site Scripting (XSS)
In the Dashboard’s comment section, enter:

<script>alert('You have been hacked!')</script>

If an alert pops up in the browser, then XSS protection is missing.

4. Access Control Test
As a regular (non-admin) user, try accessing:

/admin
If you can open the admin panel without permission, access control is not enforced correctly.

5. Insecure Communication Test
Check whether the website is using HTTPS.
Look for the padlock icon next to the URL in the browser.
If no lock is shown, the connection is not encrypte




