# Validation scenarios and results

The following validation summary is derived from the ENET’com 2025–2026 Projet de Fin d’Année report. The tests were performed in an authorized and isolated laboratory. They should not be reproduced against systems without explicit permission.

## Validation matrix

| Test area | Reported activity | Expected observation | Result described in the report |
|---|---|---|---|
| Network sensor | Suricata service and configuration checks | Sensor is active and configuration is accepted | Operational status and configuration validation were documented |
| Network reconnaissance | Controlled Nmap TCP SYN scan from Kali Linux | Network activity generates Suricata events | Events were detected and written to structured logs |
| Unauthorized access simulation | Controlled SSH connection attempts | Suspicious network activity is visible to the monitoring stack | The scenario was included among the tested activities |
| DMZ monitoring | Traffic toward an isolated target server | Target activity is observed without exposing the SOC core | The DMZ scenario was used to validate isolation and detection |
| Endpoint monitoring | Windows endpoint with Wazuh Agent and Sysmon | Host events reach the Wazuh Manager | Endpoint connectivity and event collection were validated |
| Behavioral analysis | Isolation Forest applied to structured network events | Anomaly score can produce an AI-related alert | The report documents an anomaly alert in the experiment |
| Incident integration | High-severity Wazuh event sent to TheHive through REST API | TheHive receives an alert and preserves its context | The report documents successful alert creation with HTTP 201 |

## Endpoint and network correlation

The report describes two complementary visibility paths. Wazuh and Sysmon provide endpoint telemetry, while Security Onion and Suricata provide local network visibility. The project validates the arrival and analysis of events from both paths before incident handling.

One documented endpoint test involved a Sysmon file-creation event associated with suspicious activity in a temporary directory. The report states that Wazuh transformed the event into a high-severity alert and that the alert was forwarded to TheHive for investigation.

## Automated incident creation

The integration script extracts essential alert metadata, including the rule identifier, severity, source agent, and raw event information. It then sends a JSON request to the TheHive API. The report records an HTTP `201 Created` response as evidence that the API accepted the alert and created an incident record.

The public repository does not include the original integration script because it may contain environment-specific endpoints, credentials, or implementation details that require review before release.

## AI anomaly-detection experiment

The report describes an optional Isolation Forest experiment over Suricata’s structured event output. It reports an anomaly alert for a TCP flow toward an HTTP service. This result should be presented as an **academic experiment**, not as a production-grade machine-learning detector. The report does not establish a benchmark, false-positive rate, detection rate, or generalization guarantee.

## Limitations

The report does not provide a reproducible public dataset, a complete benchmark protocol, or sanitized configuration files. Consequently, this repository makes no quantitative claims about latency, accuracy, coverage, or production readiness.

## Safety boundary

All activities described here are limited to an isolated environment owned or explicitly authorized by the project team. Do not scan, brute-force, flood, or probe third-party systems. Replace all environment-specific values with placeholders in any future public examples.

## Source

The content is derived from the authors’ ENET’com Projet de Fin d’Année report, *Présentation et mise en œuvre d’un Mini-SOC Hybride basé sur Azure et le modèle Zero Trust*, academic year 2025–2026.
