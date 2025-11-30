# SOC Playbook: Suspicious PowerShell Execution (T1059)

## Purpose

This playbook provides guidance for a SOC analyst when detecting **suspicious PowerShell activity**. Attackers commonly use PowerShell to run commands, download files, or move laterally within a network.

---

## Detection

Alerts may be triggered by:

* PowerShell launched with unusual flags: `-enc`, `-nop`, `-w hidden`
* PowerShell started by unexpected parent processes (e.g., Word, Excel)
* Execution of encoded or obfuscated commands
* Unexpected PowerShell network connections
* PowerShell running on endpoints that normally don’t use it

**Relevant MITRE Technique:**
**T1059 – Command and Scripting Interpreter (PowerShell)**

---

## Initial Triage

When an alert fires, gather:

* Username
* Device name / IP
* Full command line
* Parent process
* Timestamp
* Whether similar alerts fired recently

**Quick checks:**

* Is this a known admin running normal scripts?
* Is the command encoded?
* Does it download files or connect externally?
* Did the user report unusual behavior?

---

## Investigation Steps

1. **Review the full PowerShell command**
   Look for signs of malicious intent:

   * Base64 encoding
   * Download commands (`iwr`, `wget`)
   * Invoke-Expression (`iex`)
   * Execution policy bypass attempts

2. **Check related logs**

   * Process creation logs
   * Script block logs (if enabled)
   * Alerts for malware or unusual network activity

3. **Look for follow-up activity**

   * New processes after PowerShell
   * Suspicious files in Temp or Downloads
   * Failed logins or lateral movement attempts

---

## Containment

If suspicious or malicious:

* Isolate the host (EDR or network quarantine)
* Terminate the PowerShell process
* Disable user account if compromised
* Block malicious IPs or URLs

If activity is normal/admin, document and close the alert.

---

## Eradication

* Remove malicious scripts/files
* Run full antivirus/EDR scan
* Remove any scheduled tasks or persistence mechanisms
* Reset compromised accounts

---

## Recovery

* Reconnect the host after verification
* Monitor for additional PowerShell alerts
* Confirm user accounts are functioning normally

---

## Lessons Learned / Follow-Up

* Was Script Block Logging helpful?
* Restrict PowerShell usage for non-admins
* Update detection rules if new behavior was found
