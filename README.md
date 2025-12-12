# Asset Discovery and Prioritization Pipeline

This repository contains an open-source pipeline designed to improve IT asset visibility in local government environments by automating asset discovery, inventory reconciliation, and vulnerability prioritization.

Local governments often rely on manual spreadsheets or fragmented tools to track IT assets, which can result in missing devices, inconsistent records, and limited visibility into unmanaged systems. Public audit reports in Maryland and across the United States have repeatedly identified asset inventory and tracking as persistent weaknesses. This project aims to address those gaps by providing a lightweight, repeatable workflow that works with existing inventory practices rather than replacing them.

## Project Overview

The goal of this project is to bridge the gap between automated network scanning and real-world asset inventories. While many open-source tools can identify hosts and services, their outputs are often raw, unreconciled, and difficult to act on. This pipeline focuses on transforming scan results into structured, audit-ready artifacts that small and resource-constrained IT teams can use for security and compliance efforts.

The pipeline is built entirely using open-source tools and emphasizes simplicity, transparency, and adaptability for local government use cases.

## Research Context

This project builds on prior research examining cybersecurity practices in resource-limited local government environments. In particular, it is informed by findings presented in:

Trivedi, D., & Despeignes, S. *Local Government Supply Chain Cybersecurity: Addressing the Implementation Gap in Resource-Limited Municipalities.* ResearchGate, 2024.  
https://www.researchgate.net/publication/396960966_Local_Government_Supply_Chain_Cybersecurity_Addressing_the_Implementation_Gap_in_Resource-Limited_Municipalities

That research identified persistent gaps in asset inventory management, visibility, and implementation capacity across Maryland municipalities. These findings directly motivated the design of a lightweight, open-source pipeline that works with existing tools and processes rather than requiring costly enterprise replacements.

## Pipeline Workflow

The pipeline is organized into the following stages:

1. **Discovery**
   - Uses Ansible to automate scan execution across targeted hosts.
   - Uses Rustscan for rapid port discovery.
   - Uses Nmap to collect service, operating system, and basic vulnerability data.

2. **Normalization**
   - Python scripts convert raw scan outputs into standardized CSV files:
     - `assets.csv`
     - `findings.csv`

3. **Reconciliation**
   - Scan results are compared against an existing `inventory.csv`.
   - The pipeline identifies:
     - Shadow IT (discovered devices not in inventory)
     - Missing or outdated records
     - Version drift across assets

4. **Prioritization**
   - Findings are scored using CVSS data, asset criticality, and service exposure.
   - High-risk findings are surfaced in a prioritized `topN.csv` list.

5. **Reporting**
   - Generates a `summary.html` report and supporting CSV files.
   - Outputs are designed to support remediation workflows and audit documentation.

## Intended Audience

This project is designed for:
- Small and resource-constrained IT teams
- Local and municipal government environments
- Organizations that rely on spreadsheets or basic inventory tools
- Teams seeking low-cost, open-source approaches to asset visibility

## Project Status

This project is currently **under active development**. Initial work focuses on:
- Environment setup
- Scan automation
- CSV schema design for normalization and reconciliation

The repository will be updated incrementally as implementation progresses.

## Disclaimer

This repository represents an academic research project. It does not contain production data, sensitive information, or environment-specific configurations. All examples and artifacts are intended for demonstration and research purposes only.
