# KQL Threat Hunting Queries

A working set of Kusto Query Language (KQL) queries for proactive threat hunting across Microsoft Defender XDR and Microsoft Sentinel. Organized by MITRE ATT&CK tactic so it's easy to navigate whether you're hunting for a specific technique or building out detection coverage.

These are generalized, sanitized versions of queries I maintain for security operations. Hostnames, tenant identifiers, and org-specific values have been replaced with placeholders.

## Structure

| Folder | Tactic | Covers |
|---|---|---|
| `malware-detection/` | Execution (T1059) | Suspicious process trees, LOLBins, encoded PowerShell |
| `persistence/` | Persistence (T1547, T1053) | Registry run keys, scheduled tasks, new services |
| `credential-access/` | Credential Access (T1003, T1110) | LSASS access, impossible travel, brute force |
| `lateral-movement/` | Lateral Movement (T1021, T1570) | PsExec, WMI remote exec, host-scanning patterns |
| `exfiltration/` | Exfiltration (T1567, T1048) | Cloud storage transfers, shadow SaaS, archive staging |

## Usage

Each `.kql` file is standalone and commented — run individual queries in the Microsoft Defender **Advanced Hunting** console or **Microsoft Sentinel Logs**. Adjust table names if your environment uses Sentinel's `SecurityEvent`/`DeviceEvents` schema variants instead of Defender's native tables.

Time windows (`ago(7d)`, etc.) and thresholds are starting points — tune them to your environment's baseline to reduce false positives.

## Why this exists

Most of these patterns come from real detection engineering work — building out ASR rule coverage, tuning alerts, and reducing analyst fatigue from noisy queries. The goal here is queries that are precise enough to act on, not just technically "correct."

## Disclaimer

These queries are provided as-is for educational and defensive security purposes. Test in a non-production environment before deploying broadly, and always validate against your own data schema and retention settings.
