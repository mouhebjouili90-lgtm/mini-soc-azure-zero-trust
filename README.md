# Hybrid Mini-SOC — Azure and Zero Trust

> Academic hands-on security lab for host and network monitoring, event correlation, and incident management.

## Project context

This project was completed at **ENET’com, Tunisia**, during the 2025–2026 academic year as a Projet de Fin d’Année. Its official title is *Présentation et mise en œuvre d’un Mini-SOC Hybride basé sur Azure et le modèle Zero Trust*. The work was carried out by Mouheb Jouili and Mohamed Omezzine under academic supervision.

The project should be understood as an **academic hybrid Mini-SOC and security laboratory**. It is not presented as a production SOC operated for an external organization.

## Objectives

The objective was to design and validate a security-monitoring architecture that combines an Azure-hosted security core with an on-premises laboratory for network monitoring and attack simulation. The design follows Zero Trust principles by separating identities, roles, network zones, and access paths.

## Architecture

The environment separates three logical areas:

- **Management:** security-management services and administrative components.
- **Targets:** systems monitored by host and network security tools.
- **Attacker:** an isolated testing environment used to generate controlled security events.

The cloud portion uses an Azure Virtual Network and Network Security Groups to segment components and control communication. Microsoft Entra ID provides the identity layer. The architecture was designed with Azure virtual CPU constraints in mind.

See the sanitized [architecture overview](ARCHITECTURE.md) and the accompanying [architecture diagram](architecture-mini-soc.png).

## Security components

The project integrates the following components:

- **Wazuh Agents and Sysmon** for host telemetry and endpoint-security events.
- **ELK Stack** for log centralization, search, and event analysis.
- **Security Onion** for local network monitoring and network-security visibility.
- **TheHive** for incident organization, investigation workflows, and case management.
- **Kali Linux** for controlled validation scenarios from the local laboratory.

The tools form a workflow from identity and network isolation to telemetry collection, event analysis, correlation, and incident handling.

## Validation work

The architecture was validated through controlled tests launched from the local laboratory. The validation checked that host and network events reached the monitoring components, that events could be analyzed and correlated, and that TheHive could receive automated incident alerts through API integration.

The report-derived [validation matrix](VALIDATION.md) records the documented network, endpoint, anomaly-analysis, and TheHive integration tests.

No quantitative performance claims are made because the number of monitored systems, exact attack scenarios, alert rules, and benchmark measurements were not recorded in the public project documentation.

## Technical contributions

The project demonstrates practical experience in **SOC engineering, cloud security, security monitoring, incident response, network segmentation, and security-tool integration**. Its main value is the integration of several security layers into a coherent laboratory architecture rather than the isolated use of individual tools.

## Public-release safety

Before publishing configuration files, screenshots, or automation scripts, remove all private information. The repository must not contain Azure subscription identifiers, tenant identifiers, IP addresses that expose private infrastructure, API keys, TheHive credentials, Wazuh credentials, SSH keys, VPN configuration, user data, or copied proprietary material.

Use placeholders in public examples. A safe `.env.example` file may document variable names, but it must never contain real values.

## Suggested repository structure

```text
README.md                 Project overview and public architecture
architecture/             Sanitized diagrams and design notes
screenshots/              Sanitized screenshots with no secrets
configs/                  Redacted example configurations only
scripts/                  Safe automation examples, if publishable
docs/                     Methodology, validation notes, and limitations
.env.example              Variable names with placeholder values only
```

## Information to complete before publication

The public documentation can be strengthened by adding the number of virtual machines or monitored devices, operating systems, exact validation scenarios, alert rules, the integration path between Security Onion, Wazuh, and TheHive, and sanitized screenshots. These details should be added only after verification against the original project report and local files.

## Academic and professional positioning

For a CV or internship application, the accurate description is:

> Designed and implemented an academic hybrid Mini-SOC combining an Azure-hosted security core with an on-premises laboratory. Applied Zero Trust principles through Microsoft Entra ID, role separation, Azure VNet, and Network Security Groups. Integrated Wazuh, ELK Stack, TheHive, Security Onion, and Sysmon for host and network monitoring, event correlation, and incident management. Validated automated TheHive alert creation through API integration in controlled Kali Linux test scenarios.

## References

[1]: https://documentation.wazuh.com/current/ "Wazuh Documentation"
[2]: https://docs.securityonion.net/en/ "Security Onion Documentation"
[3]: https://docs.strangebee.com/thehive/ "TheHive Documentation"
[4]: https://learn.microsoft.com/en-us/entra/identity/ "Microsoft Entra ID Documentation"
[5]: https://learn.microsoft.com/en-us/azure/virtual-network/ "Azure Virtual Network Documentation"
[6]: https://www.elastic.co/guide/index.html "Elastic Documentation"

## Disclaimer

This repository is intended for academic, educational, and portfolio purposes. All security testing must be performed in an authorized and isolated environment.
