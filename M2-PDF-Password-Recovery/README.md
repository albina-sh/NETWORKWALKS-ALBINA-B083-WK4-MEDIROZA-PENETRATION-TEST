# M2 — PDF Password Recovery

## Objective

The objective of M2 was to recover the passwords protecting the three confidential laboratory reports obtained during M1.

Each password-protected PDF was processed separately by generating a suitable hash and performing dictionary-based password cracking.

## Method

A dictionary-based password recovery approach was used for the three PDF reports.

The following process was performed:

1. Each password-protected PDF was processed to generate a crackable hash.
2. The generated hash was provided to the password-cracking tool.
3. The initial wordlist was used to test possible passwords.
4. For PDF 1 and PDF 2, the passwords were successfully recovered using the initial wordlist.
5. For PDF 3, the initial wordlist did not recover the password.
6. A larger wordlist, `JTR_default_password.txt`, was then used for PDF 3.
7. The recovered passwords were used to open the original PDFs and verify the results.

---

## PDF 1 — Hashing and Password Cracking

The first laboratory report was processed to generate a suitable hash for password recovery.

### Hash Generation

The password-protected PDF was processed and the resulting hash was obtained.

**Evidence:**
<img width="1622" height="905" alt="Screenshot 2026-10-01 192847" src="https://github.com/user-attachments/assets/045d82a9-db96-4215-8b5a-be53cd335654" />

### Password Cracking

The generated hash was tested using the initial wordlist.

The password was successfully recovered using the initial wordlist.

**Evidence:**
<img width="1698" height="917" alt="Screenshot 2026-10-01 193058" src="https://github.com/user-attachments/assets/6c4e0e25-6bb7-4d63-a1ba-3f33013e2bab" />


### Verification

The recovered password was used to open the original PDF successfully, confirming that the recovered password was valid.

**Evidence:**
<img width="1183" height="847" alt="Screenshot 2026-10-01 193333" src="https://github.com/user-attachments/assets/b486846e-4da9-4905-a8f1-9b807d1187e5" />

---

## PDF 2 — Hashing and Password Cracking

The second laboratory report was processed independently using the same methodology.

### Hash Generation

A suitable hash was generated from the password-protected PDF.

**Evidence:**
<img width="1547" height="870" alt="Screenshot 2026-10-01 193424" src="https://github.com/user-attachments/assets/c2c61b2b-9ca0-49c2-8d90-455bb8fb72d3" />


### Password Cracking

The generated hash was tested using the initial wordlist.

The password was successfully recovered using the initial wordlist.

**Evidence:**
<img width="1256" height="901" alt="Screenshot 2026-10-01 193434" src="https://github.com/user-attachments/assets/fbf3e10c-0cf2-4fbc-8932-e1ac79e8e218" />


### Verification

The recovered password was used to open the original PDF successfully, confirming the result.

**Evidence:**
<img width="1072" height="847" alt="Screenshot 2026-10-01 193448" src="https://github.com/user-attachments/assets/4311ad7e-3035-4774-bf38-9bc7417ab175" />

---

## PDF 3 — Hashing and Password Cracking

The third laboratory report was processed using the same initial approach.

### Hash Generation

The password-protected PDF was processed and a suitable hash was generated for password recovery.

**Evidence:**
<img width="1312" height="905" alt="Screenshot 2026-10-01 193502" src="https://github.com/user-attachments/assets/f621e120-4e1c-41ff-a11b-a0a152657315" />

### Initial Cracking Attempt

The generated hash was first tested using the initial wordlist.

The initial wordlist was unable to recover the password.

**Evidence:**
<img width="1388" height="900" alt="Screenshot 2026-10-01 193635" src="https://github.com/user-attachments/assets/a3a13eec-5c75-48bc-a38d-cdaa147b9378" />

### Larger Wordlist

Because the initial wordlist was unsuccessful, a larger dictionary was selected.

The `JTR_default_password.txt` wordlist, containing approximately 3,556 password candidates, was used for a second cracking attempt.

The password was successfully recovered using the larger wordlist.

**Evidence:**
<img width="1347" height="912" alt="Screenshot 2026-10-01 194944" src="https://github.com/user-attachments/assets/17b66d45-1486-4407-ba6a-6dcca015263a" />

### Verification

The recovered password was used to open the original PDF successfully, confirming that the password had been correctly recovered.

**Evidence:**
<img width="1035" height="856" alt="Screenshot 2026-10-01 194648" src="https://github.com/user-attachments/assets/fbd7d183-7885-47da-96f5-6a4fd32657c7" />

---

## Overall Result

All three password-protected laboratory reports were successfully recovered.

* **PDF 1:** Successfully cracked using the initial wordlist.
* **PDF 2:** Successfully cracked using the initial wordlist.
* **PDF 3:** Initial wordlist unsuccessful; password successfully recovered using `JTR_default_password.txt`.

The recovered passwords were verified by successfully opening the corresponding PDF reports.

## Evidence

The M2 evidence includes the following:

### PDF 1

* Hash generation
* Successful password cracking
* Successfully opened PDF

### PDF 2

* Hash generation
* Successful password cracking
* Successfully opened PDF

### PDF 3

* Hash generation
* Initial unsuccessful cracking attempt
* Larger `JTR_default_password.txt` wordlist
* Successful password cracking
* Successfully opened PDF

## Security Impact

If an attacker obtains password-protected confidential PDF reports, the passwords may be vulnerable to offline dictionary-based attacks. The successful recovery of all three passwords demonstrates that PDF password protection alone may not provide sufficient protection when passwords are weak or predictable.

## Recommendations

* Use strong and unpredictable passwords for sensitive documents.
* Avoid common or easily guessable passwords.
* Protect confidential reports through application-level authentication and authorization.
* Store sensitive documents in access-controlled locations.
* Prevent unauthorized direct access to protected files.
