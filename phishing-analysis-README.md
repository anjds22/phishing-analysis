# 🎣 Phishing Email Analysis

A real-world phishing email analysis project investigating a spoofed Banco do Bradesco email. This project demonstrates core blue team skills including email header analysis, sender verification, IOC identification, and incident reporting.

## Tools Used

- **MXToolbox** — Email header analysis and SPF/DKIM/DMARC verification
- **VirusTotal** — IP reputation and threat intelligence lookup
- **PhishingPot (GitHub)** — Source of real phishing email samples

## What Was Analysed

A phishing email impersonating **Banco do Bradesco (Livelo)** claiming the victim had expiring reward points, designed to trick users into clicking a malicious link.

## Key Findings

| Indicator | Details |
|---|---|
| Sender Email | banco.bradesco@atendimento.com.br |
| Legitimate Domain | @bradesco.com.br |
| Sender IP | 137.184.34.4 |
| IP Verdict | Malicious (Criminal IP), Suspicious (GreyNoise) |
| SPF | TempError — DNS manipulation detected |
| DKIM | Not signed |
| DMARC | Failed |
| Malicious URL | hxxps://blog1seguimentmydomaine2bra[.]me/ |

## Red Flags Identified

- Sender domain `atendimento.com.br` does not match the legitimate Bradesco domain
- SPF authentication failed with a DNS timeout error
- Email was not DKIM signed — no cryptographic proof of legitimacy
- Sending IP flagged as malicious by threat intelligence vendors
- Urgency tactic used — "your points expire TODAY"

## Recommended Actions

- Block IP `137.184.34.4` at the firewall level
- Block domain `atendimento.com.br`
- Alert users to avoid clicking links from unverified senders
- Report the phishing domain to PhishTank

## Files

- `sample.eml` — Original phishing email sample (safe to open in text editor)
- `incident_report.md` — Full incident report with IOCs and remediation steps
- `README.md` — Project documentation

## Author

**anjds22** — [github.com/anjds22](https://github.com/anjds22)

> ⚠️ This project is for educational purposes only. The phishing email was obtained from a public dataset. Do not visit any URLs found in the sample.
