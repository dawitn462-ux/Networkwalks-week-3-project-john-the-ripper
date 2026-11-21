# Password Cracking with John the Ripper (JTR) & Johnny GUI

A hands-on cybersecurity lab from **Networkwalks Academy** — cracking the password on a protected PDF using **John the Ripper (JTR)** and its GUI front-end, **Johnny**, on Windows.

> ⚠️ **Ethical use only.** This exercise was performed in a controlled training environment against a file I was explicitly authorized to test. Password cracking tools must only be used on systems/files you own or have written permission to assess.

---

## 🧠 What I learned

- How **John the Ripper** and **Johnny** work together — JTR does the cracking, Johnny gives it a GUI so you don't need to memorize CLI flags.
- How to pull a crackable **hash** out of a password-protected PDF (the same format used by `pdf2john`/`pdf2hashcat`).
- How a dictionary/brute-force attack recovers a plaintext password from that hash.
- Why weak, common passwords (dictionary words, keyboard patterns) fall almost instantly to this kind of attack — and why that matters for real-world password policy.

---

## 🛠️ Tools Used

| Tool | Purpose |
|---|---|
| [John the Ripper](https://www.openwall.com/john/) | Core password-cracking engine |
| [Johnny](https://openwall.info/wiki/john/johnny) | GUI front-end for JTR |
| Online PDF hash extractor | Converts the locked PDF into a JTR-compatible hash |
| Notepad | Save the extracted hash to a `.txt` file |

---

## 🚶 Step-by-Step Walkthrough

### Step 1 — Install John the Ripper
Downloaded the Windows build of JTR (jumbo version) from the official site.

### Step 2 — Install & configure Johnny
Downloaded and installed Johnny, the GUI for JTR.

![Download Johnny](01-download-johnny.jpg)
![Installing Johnny](02-install-johnny.jpg)

On first launch, Johnny has no JTR executable configured yet:

![Johnny settings - no JTR path set](03-johnny-settings-empty.jpg)

Pointed Johnny at `john.exe` inside the extracted JTR `run` folder, so it could detect and use the engine:

![Browsing to john.exe](05-browse-john-exe.jpg)
![Johnny detects John the Ripper](04-johnny-settings-john-detected.jpg)

### Step 3 — Extract the hash from the locked PDF
Uploaded the protected file (`My Locked PDF1.pdf`) to an online PDF-hash-extraction tool, which outputs the hash in the same format JTR's `pdf2john` utility produces.

![Hash extractor tool](06-hash-extractor-site.jpg)
![PDF uploaded, hash extracted](07-pdf-uploaded-extracted.jpg)

Copied the extracted `$pdf$...` hash value:

![Copy the hash value](08-copy-hash-value.jpg)

Pasted it into Notepad and saved it as `hash1.txt` (making sure no stray characters like a leading `b'` were left in from copy/paste):

![Save hash as hash1.txt](09-save-hash1-txt.jpg)

### Step 4 — Load the hash into Johnny and attack
Opened the saved hash file inside Johnny:

![Open password file menu](10-open-password-file-menu.jpg)
![Browse to hash1.txt](11-browse-hash1-file.jpg)

Started the attack:

![Start new attack](12-start-new-attack.jpg)

JTR cracked the hash and recovered the plaintext password:

![Password cracked](13-password-cracked.jpg)

### Step 5 — Unlock the PDF
Opened the originally locked PDF, entered the recovered password at the prompt, and the document opened successfully.

![Password prompt on the locked PDF](14-open-locked-pdf-prompt.jpg)
![Entering the cracked password](15-enter-cracked-password.jpg)

✅ **Result:** PDF unlocked, lab objective completed.

---
Author :
Dawit Nigus Mamo

## 🔑 Key Takeaway

This lab is a good reminder that document-level password protection is only as strong as the password itself — a hash extracted from a protected PDF can be cracked offline, at speed, the moment the password is weak or guessable. Strong, unique, high-entropy passwords (or better, passphrase + proper encryption key management) are what actually hold up against this class of attack.

---

## 📚 Reference

Lab: *Week 3 – Project Module 1: Password Cracking with JTR* — Networkwalks Academy
🔗 [www.networkwalks.com](https://www.networkwalks.com)
