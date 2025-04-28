# :shield: Incident Simulation Report: T1070 - Indicator Removal on Host

---

## :bookmark_tabs: Overview

This report summarizes the adversary simulation activities performed against a controlled Windows target to emulate MITRE ATT&CK Technique **T1070 - Indicator Removal on Host**. Activities were detected and categorized using Sysmon logs, Sigma rules, and Chainsaw analysis.

---

## :triangular_flag_on_post: Summary of Activity

| Tactic | Detection | Command Observed | Impact |
|:------|:----------|:-----------------|:-------|
| Discovery | File System Discovery using `fsutil.exe` | `fsutil file seteof C:\Temp\artifact.txt 1024` | File system manipulation; possible timestomping attempts |
| Defense Evasion | Clearing Security and System Logs | `Clear-EventLog -LogName Security` | Loss of key forensic evidence (logins, privilege escalation) |
| Defense Evasion | Clearing Logs via `wevtutil` | `wevtutil cl Application` | Event log disruption, hiding traces |
| Defense Evasion | Deleting PowerShell Command History | `Remove-Item (Get-PSReadlineOption).HistorySavePath` | Loss of executed command history, impeding investigation |

---

## :mag_right: Detailed Findings

### :page_facing_up: Discovery

**Detection:** File System Discovery via `fsutil`

- **Command:**

  ```powershell
  fsutil file seteof C:\Temp\artifact.txt 1024
  ```

- **Summary:**
  - The adversary used `fsutil` to manipulate or examine file attributes.
  - Commonly used to alter timestamps or hide artifacts.

- **Impact:**
  - Timestomping attempts obscure true file creation/modification times.


### :page_facing_up: Defense Evasion

**Detection:** Clearing Event Logs via PowerShell

- **Command:**

  ```powershell
  Clear-EventLog -LogName Security
  Clear-EventLog -LogName System
  Clear-EventLog -LogName Application
  ```

- **Summary:**
  - Attempted to erase critical security and operational logs.

- **Impact:**
  - Forensic gaps prevent detection of credential abuse and persistence.


**Detection:** Clearing Logs via `wevtutil`

- **Command:**

  ```powershell
  wevtutil cl Application
  ```

- **Summary:**
  - Used native Windows utilities to wipe event logs.

- **Impact:**
  - Makes adversary actions harder to detect after the fact.


**Detection:** Deleting PowerShell Command History

- **Command:**

  ```powershell
  Remove-Item (Get-PSReadlineOption).HistorySavePath
  ```

- **Summary:**
  - Attempted to erase traces of executed PowerShell commands.

- **Impact:**
  - Hinders investigation into post-exploitation activities.


---

## :clipboard: Recommendations

- Implement **Windows Event Forwarding (WEF)** to ensure copies of logs are stored remotely.
- Monitor the use of sensitive commands like `wevtutil`, `Clear-EventLog`, and `Remove-Item`.
- Set up **file integrity monitoring (FIM)** on important system files and logs.
- Audit unusual usage of `fsutil.exe` for signs of file manipulation.

---

## :link: References

- [MITRE ATT&CK T1070 - Indicator Removal on Host](https://attack.mitre.org/techniques/T1070/)

---

# :sparkles: End of Report
