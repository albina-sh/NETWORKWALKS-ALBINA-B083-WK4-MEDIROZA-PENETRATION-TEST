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
Screenshot showing the `/old/` directory listing and the exposed database backup.

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
Screenshots showing the relevant SQL table structures and records.

## Staff Information Exposure

The exposed `staff` table contained sensitive employee information, including salary-related information and personal identification data.

The presence of this information in a publicly accessible database backup means that an unauthorized user could obtain employee information without requiring access to the hospital's internal systems.

**Evidence:**
Screenshot showing the `staff` table and relevant fields.

## Salary Information Exposure

The `monthly_salary_zar` field in the `staff` table contained salary information for hospital employees.

This demonstrated that employee compensation information was included in the publicly accessible database backup.

**Evidence:**
Screenshot showing the salary-related records.

## Shareholder Information Exposure

The database backup also contained a `shareholders` table with information about hospital shareholders.

The records included ownership percentages, shares held, and share classes.

This represents exposure of sensitive business and ownership information.

**Evidence:**
Screenshot showing the shareholder table and relevant records.

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
