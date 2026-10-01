# M2 — PDF Password Recovery

## Objective

Recover the passwords protecting the three patient laboratory reports retrieved during M1 and assess the strength of their password protection.

## Files Tested

Three password-protected PDF laboratory reports were obtained during the authorized M1 assessment.

## Method

A dictionary-based password attack was performed against the PDF files.

The initial wordlist did not successfully recover the required passwords. A larger wordlist, `JTR_default_password.txt`, containing approximately 3,556 password candidates was then used.

The attack was repeated against the protected reports.

## Result

The passwords for all three PDF reports were successfully recovered using dictionary-based password testing.

This demonstrated that the password protection used for the reports could be defeated using a sufficiently large password wordlist.

## Evidence

Screenshots included in this milestone:

* Password prompt for the PDF reports
* Initial unsuccessful password-cracking attempt
* `JTR_default_password.txt` selected as the larger wordlist
* Successful password recovery
* Successfully opened PDF reports

## Security Impact

If sensitive documents are protected using weak or predictable passwords, an attacker who obtains the files may be able to recover their contents through offline password attacks.

## Recommendations

* Use strong, randomly generated passwords for sensitive documents.
* Avoid predictable or commonly used passwords.
* Protect sensitive documents through application-level authentication and authorization rather than relying only on PDF passwords.
* Store confidential patient documents in access-controlled locations.
