# Mediroza General Hospital — Penetration Testing

## Project Information

**Project:** Web Application Penetration Testing
**Target:** https://medirozahospital.com
**Assessment Type:** Authorized Black-Box Penetration Testing
**Training Program:** Networkwalks
**Batch:** B083

---

## About the Project

This project involved an authorized black-box penetration testing assessment of the Mediroza General Hospital web application.

The assessment focused on identifying security vulnerabilities that could lead to unauthorized access to patient reports and exposure of sensitive hospital information.

The testing was performed within the authorized scope and followed the provided project requirements.

---

## Objectives

The main objectives of the assessment were:

* Identify exposed directories and files.
* Test the patient authentication mechanism.
* Identify vulnerabilities that could allow unauthorized access.
* Retrieve the three confidential laboratory reports specified in the assessment.
* Perform password recovery testing on the retrieved PDF reports.
* Investigate exposed files and database backups.
* Identify sensitive staff, salary, and shareholder information.
* Document the findings and provide remediation recommendations.

---

## Assessment Milestones

### M1 — Patient Report Access

Testing of the patient portal and authentication mechanism, resulting in the identification of SQL injection and successful authentication bypass.

Three confidential laboratory reports were retrieved as part of the authorized assessment.

→ [View M1 — Patient Report Access](./M1-Patient-Report-Access/)

### M2 — PDF Password Recovery

Password recovery testing was performed on all three retrieved laboratory reports.

PDF 1 and PDF 2 were successfully cracked using the initial wordlist, while PDF 3 required the larger `JTR_default_password.txt` wordlist.

→ [View M2 — PDF Password Recovery](./M2-PDF-Password-Recovery/)

### M3 — Sensitive Data Exposure

Investigation of publicly accessible directories identified an exposed database backup containing staff and shareholder information.

The assessment identified exposure of employee details, salary information, and shareholder ownership data.

→ [View M3 — Sensitive Data Exposure](./M3-Sensitive-Data-Exposure/)

### M4 — Penetration Testing Report

A formal penetration testing report containing the assessment scope, methodology, findings, risk ratings, proof of exploitation, recommendations, and conclusion.

→ [View M4 — Penetration Testing Report](./M4-Penetration-Test-Report/)

---

## Tools Used

The following tools and techniques were used during the assessment:

* WHOIS
* Nslookup
* DNSRecon
* cURL
* WAFW00F
* Gobuster
* Browser-based testing
* SQL injection testing
* PDF hash generation
* Dictionary-based password cracking

---

## Key Findings

The assessment identified the following security weaknesses:

1. SQL injection in the patient login functionality.
2. Authentication bypass through SQL injection.
3. Unauthorized access to confidential patient laboratory reports.
4. Password recovery of all three retrieved PDF reports.
5. Publicly accessible database backup.
6. Exposure of staff and salary information.
7. Exposure of shareholder and ownership information.

---

## Scope

Testing was limited to:

`https://medirozahospital.com`

The following activities were outside the authorized scope and were not performed:

* Denial-of-service testing
* Social engineering
* Destructive testing
* Testing systems outside the target domain

---

## Repository Structure

```text
Mediroza-General-Hospital-Pentest/
│
├── M1-Patient-Report-Access/
│   ├── README.md
│   └── evidence/
│
├── M2-PDF-Password-Recovery/
│   ├── README.md
│   └── evidence/
│
├── M3-Sensitive-Data-Exposure/
│   ├── README.md
│   └── evidence/
│
├── M4-Penetration-Test-Report/
│   └── Penetration_Testing_Report.pdf
│
└── README.md
```

---

👨‍🏫 Mentor
---

Waqas Karim (CCIE)

Thank you for the valuable technical guidance and hands-on learning experience throughout the internship.


---

👤 Author
---

Albina Shakil

Cybersecurity Learner B083

LinkedIn: https://www.linkedin.com/in/albina-shakil-3a08952a4/

---

📌 Project Information
---

Program Name: Cybersecurity at Networkwalks | Week: 04 | Repository: GitHub

---

## Disclaimer

This project was conducted under authorized conditions for educational and security assessment purposes.

The techniques demonstrated in this repository should only be used against systems where explicit permission to perform security testing has been provided.
