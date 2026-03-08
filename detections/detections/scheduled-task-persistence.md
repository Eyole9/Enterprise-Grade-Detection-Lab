# Suspicious PowerShell Execution Detection

## Purpose
Detect potentially malicious PowerShell execution involving encoded commands or suspicious script execution patterns.

## Data Source
- Windows Security Log
- Event ID 4688 – Process Creation

## Logic Summary
This detection searches for process creation events involving `powershell.exe` and suspicious command-line indicators such as:
- `-enc`
- `-EncodedCommand`
- `IEX`
- `DownloadString`

## Why It Matters
Attackers frequently use PowerShell for stealthy code execution, payload retrieval, and in-memory attacks. Encoding is often used to hide malicious intent from analysts and basic security tools.

## MITRE ATT&CK Mapping
- Tactic: Execution
- Technique: Command and Scripting Interpreter
- Related behavior: Obfuscated / Encoded Commands

## Possible False Positives
- Legitimate administrative scripting
- Internal automation
- Security testing
- IT maintenance tasks

## Tuning Notes
- Focused on high-risk command indicators instead of all PowerShell usage
- Reviewed service and Splunk-generated process noise
- Confirmed process creation telemetry was enabled through Event ID 4688

## Test Performed
Enabled process creation auditing and validated that Event ID 4688 was visible in Splunk. Searched for suspicious PowerShell command patterns and confirmed no malicious execution occurred in the clean lab environment.

## Outcome
Built a working execution-focused detection logic for suspicious PowerShell behavior.
