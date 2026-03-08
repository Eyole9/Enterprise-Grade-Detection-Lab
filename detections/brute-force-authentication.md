# Brute Force Authentication Detection

## Purpose
Detect potential brute-force or password-guessing activity by identifying multiple failed Windows logons followed by a successful logon for the same account.

## Data Source
- Windows Security Log
- Event ID 4625 – Failed Logon
- Event ID 4624 – Successful Logon

## Logic Summary
This detection looks for repeated failed authentication attempts for a user account and checks whether a successful logon occurs afterward within a short time window.

## Why It Matters
Attackers often guess passwords repeatedly before gaining access. A success after multiple failures can indicate account compromise.

## MITRE ATT&CK Mapping
- Tactic: Credential Access
- Technique: Brute Force

## Possible False Positives
- User mistypes password multiple times
- Password manager sync issue
- Keyboard layout issue

## Test Performed
Reviewed failed and successful logon telemetry in Splunk and validated authentication event patterns.

## Outcome
Built and saved a working Splunk alert for brute-force style authentication behavior.
