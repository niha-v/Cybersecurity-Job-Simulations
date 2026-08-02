# AIG  Cybersecurity Job Simulation
<img src = "https://github.com/niha-v/Cybersecurity-Job-Simulations/blob/main/aig_image.png" width ="400" >

**Role simulated:** Information Security Analyst, Cyber & Information Security Team

AIG's simulation places you in the role of an analyst responsible for staying on top of emerging vulnerabilities and CISA advisories, then responding before an attacker can exploit them — followed by a live incident when a vulnerability is exploited in practice.

### Task 1 — Zero-Day Vulnerability Response (Log4j)

Reviewed a CISA advisory on the Apache Log4j zero-day vulnerability (Log4Shell, CVE-2021-44228) and cross-referenced it against a company infrastructure list to identify which team owned the affected system.

- Identified that the Product Development Staging Environment was the only asset running Log4j
- Researched the vulnerability mechanism: remote code execution via attacker-controlled JNDI lookup strings evaluated during logging
- Drafted a formal security advisory email to the infrastructure owner, explaining the vulnerability, its risk/impact, and concrete remediation steps (version upgrade, interim mitigation flag, log review for indicators of compromise)

### Task 2 — Ransomware Incident: Bruteforcing a Decryption Key

After the Log4j vulnerability was exploited, an attacker attempted to deploy ransomware. Incident Detection & Response stopped it before full encryption, but one zip file was encrypted. With leadership declining to pay the ransom, I was tasked with recovering the file myself.

- Wrote a Python script using `zipfile.ZipFile` to attempt extraction against each password in a wordlist (a Rockyou-derived sample)
- Handled failed attempts via exception handling and confirmed a successful password on match
- Recovered the encrypted document, cracking the password (`SPONGEBOB`) — consistent with the scenario's premise of a low-sophistication attacker using default, copy-pasted ransomware tooling

```python
from zipfile import ZipFile

def attempt_extract(zf_handle, password):
    try:
        zf_handle.extractall(pwd=password)
        return True
    except Exception:
        return False

def main():
    print("[+] Beginning bruteforce ")
    with ZipFile('enc.zip') as zf:
        with open('rockyou.txt', 'rb') as f:
            for line in f:
                password = line.strip()
                if attempt_extract(zf, password):
                    print(f"[+] Password found: {password.decode()}")
                    return
    print("[+] Password not found in list")

if __name__ == "__main__":
    main()
```

### Skills demonstrated
`CISA advisory research` · `vulnerability triage` · `stakeholder communication` · `incident response` · `Python scripting` · `password/hash bruteforcing`

