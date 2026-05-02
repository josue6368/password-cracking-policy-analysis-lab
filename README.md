# password-cracking-policy-analysis-lab
Analyzed password strength using John the Ripper in Kali Linux against fake MD5 password hashes. Demonstrated dictionary-based cracking, compared weak passwords vs. stronger passphrases, and documented password policy recommendations.
# Password Cracking and Password Policy Analysis Lab

## Overview

This project demonstrates a password cracking and password policy analysis lab using Kali Linux and John the Ripper.

The purpose of the lab was to analyze how weak, common, and predictable passwords can be cracked using dictionary-based attacks. Fake test passwords were hashed and analyzed in a controlled lab environment to compare weak passwords against stronger passphrase-style passwords.

No real credentials, production systems, or unauthorized password hashes were used.

---

### Lab Architecture

- **Platform:** Kali Linux VM
- **Cracking Tool:** John the Ripper
- **Hash Type:** MD5
- **Wordlist:** rockyou.txt
- **Environment:** Private virtual lab

---

### Ethical Scope

This lab was conducted using fake test passwords and fake hashes created specifically for this project.

No real user credentials, external systems, or unauthorized password hashes were used. The purpose of this project was to demonstrate password security concepts and defensive password policy analysis.

---

### Tools and Technologies

- Kali Linux
- John the Ripper
- rockyou.txt wordlist
- Linux command line
- MD5 hashing

---

### Lab Setup Summary

- Created a password cracking project folder in Kali Linux
- Created a list of fake test passwords
- Generated MD5 hashes from the test passwords
- Used John the Ripper with the rockyou.txt wordlist
- Reviewed cracked and uncracked passwords
- Analyzed password strength and policy implications

### Project Files

The lab workspace included the source password list, the generated MD5 hash file, and a simple password analysis file used to document cracking results and observations.

Key files created during the project included:

- `passwords.txt`
- `hashes_md5.txt`
- `password_analysis.md`

<img width="602" height="148" alt="Screenshot 2026-05-01 220811" src="https://github.com/user-attachments/assets/c3b85a14-58c5-4732-9f04-349dede83df7" />


---

### Test Password Set

The following fake passwords were used for this lab:

```text
password123
Summer2024
Welcome1
P@ssw0rd!
BlueTruck77
CorrectHorseBatteryStaple2026!
```
### Hash Generation

The fake passwords were converted into MD5 hashes using the Linux command line.
```
while read password; do echo -n "$password" | md5sum | awk '{print $1}'; done < passwords.txt > hashes_md5.txt
```
<br/>

<img width="1086" height="500" alt="Screenshot 2026-05-01 222634" src="https://github.com/user-attachments/assets/7ea0c90b-5c25-4c46-bac0-c952fa3a11f7" />


### Cracking Method

John the Ripper was used to perform a dictionary-based attack against the fake MD5 hashes.
```
john --format=Raw-MD5 --wordlist=/usr/share/wordlists/rockyou.txt hashes_md5.txt
```
The cracked results were displayed using:
```
john --format=Raw-MD5 hashes_md5.txt --show
```
<br />
<img width="1088" height="500" alt="Screenshot 2026-05-01 220349" src="https://github.com/user-attachments/assets/09ecdd3a-a8fc-4af2-830d-d2533dbfed43" />

### Results

John the Ripper cracked 3 out of 6 password hashes.

| Password                       | Result      | Analysis                                                                    |
| ------------------------------ | ----------- | --------------------------------------------------------------------------- |
| password123                    | Cracked     | Extremely common password found in many wordlists.                          |
| Welcome1                       | Cracked     | Common default-style corporate password pattern.                            |
| P@ssw0rd!                      | Cracked     | Uses character substitution but remains predictable.                        |
| Summer2024                     | Not Cracked | Seasonal password pattern, but not cracked in this test wordlist.           |
| BlueTruck77                    | Not Cracked | Less predictable phrase-style password.                                     |
| CorrectHorseBatteryStaple2026! | Not Cracked | Long passphrase-style password with strong resistance to dictionary attack. |

<br/>
<img width="1078" height="335" alt="Screenshot 2026-05-01 220619" src="https://github.com/user-attachments/assets/6b957f51-acc9-44e0-bf19-371e3f5f2631" />

### Analysis

The results show that passwords commonly considered “complex” may still be weak if they follow predictable patterns.

For example, P@ssw0rd! includes uppercase letters, lowercase letters, numbers, and symbols, but it was still cracked because it is a common substitution pattern.

Longer and less predictable passwords, especially passphrase-style passwords, were more resistant to the dictionary attack.

### Key Takeaways
* Common passwords are highly vulnerable to dictionary attacks.
* Simple substitutions, such as replacing a with @ or o with 0, do not guarantee strong security.
* Password length and unpredictability are often more effective than basic complexity rules.
* Passphrases can provide stronger resistance against wordlist-based attacks.
* Password reuse increases risk if credentials are exposed in breaches.

### Defensive Recommendations
* Enforce minimum password length requirements.
* Encourage long passphrases instead of short complex passwords.
* Block commonly used and breached passwords.
* Require multi-factor authentication.
* Use password managers to generate and store strong unique passwords.
* Monitor for exposed credentials and password reuse.
* Educate users on predictable password patterns.

### Skills Demonstrated
* Password cracking methodology
* Hash analysis
* Dictionary attack testing
* Linux command-line usage
* John the Ripper usage
* Password policy analysis
* Security awareness recommendations


### Author
:floppy_disk: josue6368 <br/>
Cybersecurity Analyst | IT Professional





