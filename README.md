# Mediroza General Hospital — Penetration Testing

## Project Overview

This repository documents an authorized black-box penetration testing assessment conducted against the Mediroza General Hospital web application.

**Target:** https://medirozahospital.com

The assessment focused on identifying vulnerabilities that could lead to unauthorized access to patient information and exposure of sensitive organizational data.

## Assessment Milestones

### M1 — Patient Report Access

Identification and exploitation of a vulnerability in the patient authentication mechanism, followed by authorized retrieval of three confidential laboratory reports.

→ [View M1 — Patient Report Access](./M1-Patient-Report-Access/)

### M2 — PDF Password Recovery

Password recovery testing performed against the three retrieved password-protected laboratory reports using dictionary-based techniques.

→ [View M2 — PDF Password Recovery](./M2-PDF-Password-Recovery/)

### M3 — Sensitive Data Exposure

Investigation of publicly accessible files and an exposed database backup containing staff, salary, and shareholder information.

→ [View M3 — Sensitive Data Exposure](./M3-Sensitive-Data-Exposure/)

### M4 — Penetration Testing Report

Formal documentation of the assessment findings, risk ratings, proof of exploitation, and recommended remediation.

→ [View M4 — Penetration Testing Report](./M4-Penetration-Test-Report/)

## Scope

Testing was limited to the authorized target:

`https://medirozahospital.com`

Denial-of-service testing, social engineering, destructive testing, and testing of systems outside the authorized scope were not performed.

## Disclaimer

This repository documents security testing performed under authorized conditions for educational and security assessment purposes. The techniques and findings described here should only be applied to systems where explicit authorization has been provided.
