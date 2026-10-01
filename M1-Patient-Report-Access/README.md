# M1 — Patient Report Access

## Objective

Identify a vulnerability in the Mediroza General Hospital patient portal that could allow unauthorized access to confidential patient laboratory reports.

## Target

`https://medirozahospital.com`

<img width="1820" height="922" alt="Screenshot 2026-10-01 211948" src="https://github.com/user-attachments/assets/90bae3ee-23bf-422c-a43d-d07d5881e515" />


## Reconnaissance

During reconnaissance, the website's `robots.txt` file was reviewed.

The file contained the following entries:

```text
User-agent: *
Disallow: /patient/
Disallow: /staff/
Disallow: /old/

Sitemap: https://medirozahospital.com/sitemap.xml
```

The `/patient/` directory was then accessed and was found to have directory listing enabled.


<img width="753" height="481" alt="Screenshot 2026-10-01 212251" src="https://github.com/user-attachments/assets/a9e4b187-e6af-4846-b08c-3fc43e224133" />



The directory exposed several files, including:

* `login.php`
* `portal.php`
* `download.php`
* `logout.php`
* `reports/`

The `/reports/` directory itself returned a `403 Forbidden` response, so further testing focused on the patient login functionality.

## Authentication Testing

The patient login form accepted a username and password.

Initial testing with invalid credentials returned different responses depending on the username.

Testing the username `admin` with an incorrect password returned:

```text
Incorrect password
```

This indicated that the `admin` username existed.

<img width="1780" height="816" alt="Screenshot 2026-10-01 192101" src="https://github.com/user-attachments/assets/2b74b30b-44b9-44b1-a464-03931db7e8ad" />



A single quotation mark (`'`) entered into the username field produced a MySQL syntax error. This indicated that user input was being incorporated into a database query without proper input handling.


<img width="1807" height="832" alt="Screenshot 2026-10-01 192118" src="https://github.com/user-attachments/assets/4acc8acc-ee18-4406-bb08-adecb691c02e" />


Based on these observations, a controlled SQL injection test was performed against the username field.

## Authentication Bypass

The following payload was used:

```text
admin' -- 
```

The payload successfully bypassed the login authentication and provided access to the patient portal.

### Why This Was Tested

The payload was not used randomly. The testing sequence was based on the observed behavior:

1. `admin` returned an "Incorrect password" response.
2. `'` produced a MySQL syntax error.
3. These responses indicated that the username was being processed directly by a database query.
4. A controlled test was therefore performed to determine whether the authentication query could be manipulated.

## Patient Portal Access

After successful authentication bypass, the patient portal was accessible without the legitimate password.

The portal displayed three confidential patient laboratory reports, which were successfully retrieved for the authorized assessment.

All three reports were password protected when opened.

<img width="1807" height="727" alt="Screenshot 2026-10-01 192225" src="https://github.com/user-attachments/assets/eba835e6-5a42-48a5-be6b-0a431a60dfea" />


## Result

**M1 was successfully completed.**

The assessment demonstrated that a SQL injection vulnerability in the patient login functionality could be used to bypass authentication and access confidential patient laboratory reports.

## Evidence

Screenshots included in this milestone:

* `robots.txt` revealing the patient directory
* Patient login page
* MySQL syntax error
* `admin` username validation
* Patient portal displaying the three laboratory reports

> **Note:** Sensitive patient information and other unnecessary personal data should be redacted from screenshots before publishing them to GitHub.

## Key Finding

**SQL Injection → Authentication Bypass → Unauthorized Patient Report Access**

## Security Impact

An attacker exploiting this vulnerability could bypass the patient authentication mechanism and potentially access confidential medical information without valid credentials.

## Remediation

* Use prepared statements or parameterized SQL queries.
* Validate and sanitize all user input on the server side.
* Implement secure authentication mechanisms.
* Do not expose database error messages to users.
* Enforce authorization checks before allowing access to patient records.
