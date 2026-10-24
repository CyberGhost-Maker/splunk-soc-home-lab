
# Splunk SOC Home Lab: Authentication Monitoring

## Project Overview

This project demonstrates foundational Security Operations Center (SOC) skills using Splunk Enterprise. It analyzes synthetic authentication events, detects repeated login failures, and presents findings through SPL searches and a monitoring dashboard.

## Objectives

- Ingest and validate authentication logs.
- Analyze authentication activity using SPL.
- Detect repeated failed logins within a five-minute window.
- Identify user/source IP combinations with repeated failures and successful logins.
- Build a security monitoring dashboard.
- Document findings in an incident report.

## Tools and Environment

- Splunk Enterprise
- macOS on Apple silicon
- Splunk Search Processing Language (SPL)
- CSV synthetic authentication data
- Git and GitHub

## Lab Architecture

Synthetic CSV logs
    -> Splunk Enterprise ingestion
    -> SPL searches and detection logic
    -> Dashboard and investigation report

## Repository Structure

- `data/` — synthetic authentication events.
- `queries/` — SPL searches and detections.
- `screenshots/` — screenshots of validation, queries, and dashboard.
- `reports/` — incident investigation documentation.

## Detection Use Cases

1. Authentication event overview.
2. Failed login analysis by user and source IP.
3. Detection of at least three failures in a five-minute time bin.
4. Identification of accounts with repeated failures and successful logins.

## Validation Results

The sample dataset contains 22 synthetic events:
- 10 successful authentications.
- 12 failed authentications.

The threshold detection is expected to identify three user/source IP combinations.

## Investigation Findings

The synthetic dataset includes:
- Repeated failures for Alice from `198.51.100.25`.
- Repeated failures for Bob from `203.0.113.50`.
- Repeated failures for Carol from `198.51.100.25`.
- A successful login for Alice from the same source IP after her failed attempts.

These are simulated events, not evidence of an actual security incident.

## Screenshots

Screenshots of the ingestion validation, SPL searches, and completed dashboard will be added here.

## Limitations

- All authentication data is synthetic.
- The threshold is illustrative and requires tuning before operational use.
- A repeated-failure pattern alone does not prove malicious activity.
- No production systems or real user credentials were used.

## Future Improvements

- Configure scheduled alerts.
- Test detection against additional scenarios.
- Add investigation and escalation procedures.
- Integrate authorized endpoint or identity logs in an isolated lab.

## Disclaimer

This project is for educational and defensive cybersecurity purposes only.

