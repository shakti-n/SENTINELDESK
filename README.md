A small, host-ready defensive cybersecurity incident reporting application built with Python + Flask + SQLite.
Features
Dashboard with incident statistics
Incident reporting form
Incident list with status/severity filtering
Incident detail pages
Status workflow: Open → Investigating → Contained → Resolved
10 common cyber incident categories
Demo incident data
Entire database schema + seed data in `schema.sql`
SQLite foreign keys and indexes
Production-friendly Gunicorn entry point
`/health` endpoint for hosting health checks
Responsive dark security-themed interface
10 incident categories
Phishing
Ransomware
Malware Infection
Credential Theft
DDoS Attack
SQL Injection
Cross-Site Scripting (XSS)
Unauthorized Access
Data Exfiltration
Insider Threat
All example identities use `example.test` addresses and are fictional demo records.
Run locally
```bash
python -m venv .venv
# Windows:
.venv\Scripts\activate
# Linux/macOS:
source .venv/bin/activate

pip install -r requirements.txt
python app.py
```
Open `http://127.0.0.1:5000`.
The first run automatically creates `incident_reporting.db` from `schema.sql`.
Production
Set a strong secret:
```bash
SECRET_KEY="replace-with-a-long-random-secret"
```
Then:
```bash
gunicorn app:app
```
For a public deployment, put the application behind HTTPS and a reverse proxy, and replace the demo authentication with real authentication/authorization.
Database
For SQLite, the complete schema and demo seed data are in `schema.sql`.
To reset the database:
```bash
rm incident_reporting.db
python app.py
```
On Windows PowerShell:
```powershell
Remove-Item incident_reporting.db
python app.py
```
Security notes
This is an incident-reporting/demo application, not a full enterprise SIEM/SOC platform. Before real deployment, add authentication, role-based access control, CSRF protection, audit logging, rate limiting, centralized logging, secure secret storage, database backups, and PostgreSQL/MySQL if concurrent production workloads require it.
