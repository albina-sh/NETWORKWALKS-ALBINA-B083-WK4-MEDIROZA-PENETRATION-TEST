# M3 — Sensitive Data Exposure

## Objective

The objective of M3 was to identify sensitive information exposed through publicly accessible files and directories on the Mediroza General Hospital website.

The assessment focused on identifying exposed data that could provide unauthorized access to employee, salary, and shareholder information.

## Discovery of the `/old/` Directory

During the assessment, the website's `robots.txt` file was reviewed.

The file contained a reference to the following directory:

`/old/`

Direct access to the directory revealed that directory listing was enabled.

The directory contained the following file:

`mediroza_db_backup_2019.sql`

The database backup was accessible directly through the website without authentication.

**Evidence:**
<img width="1222" height="546" alt="Screenshot 2026-10-01 214035" src="https://github.com/user-attachments/assets/cadae459-4e06-4ef6-a7a5-f5d0fba98bbe" />

## Database Backup Analysis

The exposed SQL backup was downloaded and reviewed to determine what information it contained.

The backup included database table definitions and records associated with hospital staff and shareholders.

A review of the SQL structure identified the following relevant tables:

* `staff`
* `shareholders`

The `staff` table contained fields including:

* Full name
* Job title
* Department
* Email address
* Phone number
* National identification number
* Monthly salary
* Date joined

The `shareholders` table contained information relating to:

* Shareholder names
* Ownership percentages
* Shares held
* Share classes

**Evidence:**
<img width="1392" height="910" alt="Screenshot 2026-10-01 195316" src="https://github.com/user-attachments/assets/6dbadbea-640d-416b-ab8a-ceb62694d1b1" />

<img width="1686" height="920" alt="Screenshot 2026-10-01 195345" src="https://github.com/user-attachments/assets/0e035beb-d6f2-4507-b5ec-ddbd6bc9a236" />


## Staff Information Exposure

The exposed `staff` table contained sensitive employee information, including salary-related information and personal identification data.

The presence of this information in a publicly accessible database backup means that an unauthorized user could obtain employee information without requiring access to the hospital's internal systems.


## Salary Information Exposure

The `monthly_salary_zar` field in the `staff` table contained salary information for hospital employees.

This demonstrated that employee compensation information was included in the publicly accessible database backup.


## Shareholder Information Exposure

The database backup also contained a `shareholders` table with information about hospital shareholders.

The records included ownership percentages, shares held, and share classes.

This represents exposure of sensitive business and ownership information.


## Result

M3 successfully identified a publicly accessible database backup containing sensitive organizational information.

The exposed backup contained:

* Employee personal information
* Employee contact information
* National identification information
* Employee salary information
* Employee joining dates
* Shareholder information
* Ownership percentages
* Shares held
* Share classes

The exposure occurred because the database backup was stored within a publicly accessible web directory.

## Security Impact

An unauthorized user who discovers the exposed backup could download and analyze the database without requiring application authentication.

Exposure of employee and shareholder information could result in privacy violations, targeted attacks, misuse of personal information, and disclosure of confidential business information.

## Recommendations

* Remove database backups from publicly accessible web directories.
* Store backups outside the web root.
* Disable unnecessary directory listing.
* Restrict access to backup files using appropriate server-side access controls.
* Encrypt sensitive backups at rest.
* Regularly scan web directories for accidentally exposed backup files.
* Remove obsolete files and directories from production systems.
* Review the server for other publicly accessible sensitive files.

## Evidence

The M3 evidence includes:

1. `robots.txt` revealing the `/old/` directory.
2. `/old/` directory listing showing `mediroza_db_backup_2019.sql`.
3. SQL backup showing the `staff` table structure.
4. Staff records showing salary-related information.
5. SQL backup showing the `shareholders` table.
6. Shareholder records showing ownership and share information.

## Key Finding

**Publicly Accessible Database Backup → Staff & Salary Information Exposure → Shareholder Information Exposure**
