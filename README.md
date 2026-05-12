# Network Standards Repository
## Purpose
This repository defines the standardized baseline configuration, deployment method, and governance model for network infrastructure.

It exists to ensure:
- Consistent switch deployments
- Repeatable configuration management
- Reduced human error during provisioning
- A documented reference architecture for current and future engineers
- Auditability and operational continuity independent of indiviaul staff

## Scope
This standard currently applies to:
- Layer 2 / Layer 3 network switches
- Baseline device hardening
- Management plane configuration
- VLAN, trunking, and access port standards
- SSH, logging, NTP, SNMP, and management access controls
- Ansible-based automated deployment using YAML configuration templates

Future expansions may include:
- Firewalls
- Wireless infrastructure
- Routing standards
- Network monitoring standards

## Standard State Definition
A switch is considered **compliant** when it matches the configuration defined by the YAML template and deployed via the Ansible playbook in this repository.

No device should be deployed manually outside this standard.

## Repository Structure
network-standards/
├── ansible/
│   ├── playbooks/
│   ├── templates/
│   └── inventory/
├── templates/
│   └── switch_baseline.yml
├── docs/
│   └── switch_standard.md
└── README.md

## Configuration Templatae (Source of Truth)
The YAML file in:
`/templates/switch_baseline.yml`
is the **authoritative source** for switch configuration.

Site-specific values are filled in during deployment, but the structure and required controls must not be altered.

## Deployment Method
Switches are deployed using:
- [Ansible](https://docs.ansible.com/) playbooks in `/ansible/playbooks`
- YAML-driven configuration input
- Idempotent execution to guarantee consistent state
Manual CLI confiugration is discouraged and considered non-standard.

## Governance
Changes to the standard must:
1. Be documented
2. Be reviewed
3. Preserve compatibility with automated deployment
4. Improve security, reliability, or maintability
This repository is intended to outlive individual contributors and serve as long-term engineering reference.

## Why This Exists
Network deployments historically depend on tribal knowledge and manual configuration. This standard replaces that with:
  **Documented, repeatable, automation-driven engineering practice**

## How to Use This Standard
1. Populate the YAML template with site values
2. Run the Ansible playbook
3. Verify compliance
4. Commit any improvements back to this repository

## Ownership
This repository represents the **network engineering standard,** not a personal project. It is designed to be forked, referenced, and adopted as the authoritative baseline for deployments.


