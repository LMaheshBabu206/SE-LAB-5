# Lab 5: Static Code Analysis – Domain & SSL Certificate Expiry Alert System

**Problem Statement #47 – Domain & SSL Certificate Expiry Alert System**

This project adapts the Lab 5 workflow demonstrated by the reference Parcel Tracker repository. The static-analysis practical is preserved, while the application domain is changed to domain registration and TLS certificate expiry monitoring.

## What the program does

The corrected program models a monitored domain with separate registration-expiry and TLS-certificate-expiry dates. It calculates days remaining, classifies each date as `expired`, `critical`, `warning`, or `healthy`, creates alert records for non-healthy assets, and writes a JSON report. A separate RDAP helper demonstrates retrieving registration data over verified HTTPS with a request timeout; it is not called by the offline demo.

## Lab workflow

1. Run `domain_ssl_monitor_before.py`, the intentionally flawed baseline.
2. Run Pylint, Bandit and Flake8 against the baseline and save the `*_before.txt` reports.
3. Review `issues.md` and identify the findings.
4. Run `domain_ssl_monitor.py`, the corrected version.
5. Execute `python -m pytest -v` to check that the expected functionality remains.
6. Run the three static-analysis tools against the corrected version and save the `*_after.txt` reports.
7. Answer the reflection questions in `reflection.md`.

## Setup (Windows PowerShell)

```powershell
py -m venv .venv
.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
```

## Run

```powershell
python domain_ssl_monitor_before.py
python domain_ssl_monitor.py
python -m pytest -v
```

## Static analysis commands

See `commands.txt` for commands that save before/after reports. The `*_before.txt` and `*_after.txt` files should be generated on the student's machine with the installed versions of Pylint, Bandit and Flake8; do not replace these with invented results.

## Security note

`domain_ssl_monitor_before.py` intentionally contains insecure patterns for the static-analysis exercise. It is for analysis only. Do not use its unsafe RDAP request, temporary-file creation, or weak alert-ID generation in a real system. Use `domain_ssl_monitor.py` for the corrected implementation.
