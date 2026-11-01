# Awesome-Mission-Critical-Cloud-Data-Security

## Top Mission-Critical Cloud Data Security Ecosystem



**Curated List of SaaS Products & Open-Source GitHub Projects**  

*Focused on Secrets Management, Privileged Access & Self-Hosted Cloud Security Posture*  

**Last updated: November 2026**



This repository tracks notable **SaaS platforms** and **open-source projects** for **Mission-Critical Cloud Data Security**. These tools enable organizations to protect the crown jewels—encryption keys, privileged credentials, sensitive data stores, and cloud configurations—with the controls, auditability, and resilience that regulated and high-stakes environments demand.



**Examples** include Snowflake Business Critical Edition, AWS Key Management Service, HashiCorp Vault Cloud, CyberArk Privileged Cloud, Vanta, Drata, TrustArc, OneTrust, BigID, and Imperva Data Security (the category leaders).



**Open-source emphasis**: Mission-Critical Cloud Data Security is a domain where open-source tooling is **genuinely capable but requires assembly across distinct security layers**. The strongest active projects are **JumpServer** (a mature, GPLv3-licensed Privileged Access Management platform for SSH, RDP, Kubernetes, and databases via browser) and **Secrets** (a lightweight MIT-licensed secrets manager with envelope encryption, transit encryption, and audit logs, explicitly inspired by Vault but intentionally simpler). For cloud security posture, **Mantissa Stance** provides an open-source CSPM/DSPM/CIEM combination with 300+ policies and attack path analysis, and **Poirot DSPM** detects sensitive data across MySQL, S3, Kafka, and cloud drives with TheHive integration. The critical caveat: **no open-source project matches the integrated breadth** of Vanta's compliance automation or CyberArk's enterprise PAM—open-source tools address specific layers (secrets, PAM, posture, data discovery) and require you to own the integration and operational responsibility.



Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.



## Table of Contents

- [SaaS/Hosted Platforms](#saas-products)

- [Open-Source GitHub Projects](#open-source-github-projects)

- [How to Contribute](#how-to-contribute)

- [Disclaimer](#disclaimer)



## SaaS/Hosted Platforms



- **[Snowflake Business Critical Edition](https://www.snowflake.com/)**  

  Snowflake's highest standard tier with **Tri-Secret Secure** (composite master key combining Snowflake and customer-owned key), customer-managed keys, private connectivity, and enhanced security monitoring for regulated workloads.



- **[AWS Key Management Service (KMS)](https://aws.amazon.com/kms/)**  

  Managed service for creating and controlling encryption keys used to protect data across AWS services and applications; integrates with CloudTrail for audit logging and supports customer-managed keys.



- **[HashiCorp Vault Cloud](https://www.hashicorp.com/)**  

  Managed secrets management platform for storing, accessing, and rotating secrets, credentials, and encryption keys; provides dynamic secrets, leasing, renewal, and audit devices.



- **[CyberArk Privileged Cloud](https://www.cyberark.com/)**  

  SaaS privileged access management with credential vaulting, session isolation, least-privilege controls, and audit trails for privileged accounts across hybrid environments.



- **[Vanta](https://www.vanta.com/)**  

  Compliance automation platform with continuous control monitoring, evidence collection, and trust center; supports SOC 2, ISO 27001, HIPAA, and other frameworks.



- **[Drata](https://drata.com/)**  

  Compliance automation with continuous monitoring, control management, and auditor workflows; positioned as a Vanta alternative.



- **[TrustArc](https://trustarc.com/)**  

  Privacy and compliance management platform; provides assessments, certifications, and regulatory tracking for data protection.



- **[OneTrust](https://www.onetrust.com/)**  

  GRC platform unifying privacy, AI governance, risk management, and third-party monitoring; trusted by 14,000+ global brands.



- **[BigID](https://bigid.com/)**  

  Data intelligence platform for discovery, classification, and protection of sensitive data across cloud and on-premises environments.



- **[Imperva Data Security](https://www.imperva.com/)**  

  Data security platform with discovery, classification, activity monitoring, and protection for databases and data stores.



## Open-Source GitHub Projects



### Secrets Management (Vault Alternatives)



- **[Secrets](https://github.com/allisson/secrets)**  

  A **lightweight, MIT-licensed secrets manager** explicitly inspired by HashiCorp Vault but intentionally simpler . Features: **envelope encryption** (Master Key → KEK → DEK → Secret Data) with key rotation; **KMS integration** for master key encryption at rest (Google Cloud KMS, AWS KMS, Azure Key Vault, HashiCorp Vault) ; **transit encryption** for encrypt/decrypt as a service; **tokenization API** with token generation, detokenization, validation, revocation, and TTL; **capability-based authorization** with path-matching policies; **cryptographic audit log signing** (HMAC-SHA256) for tamper detection, PCI DSS 10.2.2 aligned ; and **OpenTelemetry metrics** with Prometheus export. Docker-first deployment. **Best for teams wanting a simple, auditable secrets manager** without Vault's operational complexity—but it is not designed to compete with Vault's full feature set .



- **[kvlt](https://github.com/retr0h/kvlt)**  

  A **single-binary, local-first secrets vault** that encrypts with **age using your existing SSH keys** . Features: **no daemon, no service**—pure CLI; **named vaults** for stable call sites (`kvlt get prod API_KEY`); **multi-recipient** encryption (encrypt to N SSH public keys); **stdin/TTY input modes** to keep secrets out of shell history; shell-friendly `kvlt env` for direnv integration; and a **pluggable backend interface** (AWS Secrets Manager planned via build tags). **Security model**: delegates the lock to the SSH protection chain (passphrase + ssh-agent + Touch ID via Secretive), meaning an attacker with user-level code execution cannot decrypt without the in-memory unlock state . **Best for developers** wanting a minimal, secure vault that borrows existing SSH security—not for team-scale secrets management with centralized policy.



### Privileged Access Management (PAM)



- **[JumpServer](https://github.com/jumpserver/jumpserver)**  

  The **leading open-source Privileged Access Management (PAM) platform** (GPLv3, ~25k GitHub stars) . Provides **on-demand, secure access to SSH, RDP, Kubernetes, Database, and RemoteApp endpoints through a web browser** . Components include Lina (Web UI), Luna (Web Terminal), KoKo (character protocol connector), Lion (graphical protocol connector), and Chen (Web DB). Quick start via `curl` script on a Linux server (4c8g minimum). **Best for organizations wanting a self-hosted PAM** with browser-based access and audit trails—but it is a substantial platform requiring proper deployment and maintenance.



- **[Thand Agent](https://github.com/thand-io/agent)**  

  A **distributed, open-source agent for PAM and just-in-time (JIT) access** to cloud infrastructure, SaaS applications, and local systems (BSL 1.1) . Features: **zero standing privileges**—no permanent admin access; **JIT permissions** requested when needed and revoked after; **serverless workflows via Temporal** for deterministic execution and revocation; **complete audit trail** of every request and action . Deployable via Docker, Kubernetes, AWS Lambda, or GCP Cloud Functions. **Best for organizations wanting JIT access** to eliminate standing privileges—but it is a newer project with BSL licensing (not OSI-approved) and requires integration effort.



### Cloud Security Posture (CSPM/DSPM/CIEM)



- **[Mantissa Stance](https://github.com/mantissa-labs/stance)**  

  An **open-source CSPM, DSPM, CIEM, and vulnerability management** tool for AWS, GCP, and Azure . Features: **agentless collection** via 37 collectors; **300+ YAML policies** with CIS benchmark scoring; **DSPM** with sensitive data classification and exposure mapping; **CIEM** with effective permissions and over-privilege detection; **attack path analysis** with trust graphs, blast radius, and toxic combination detection; **natural language to SQL** querying (Claude/GPT-4/Gemini) . **Deterministic core**: all detection, policy evaluation, and risk scoring use transparent algorithmic logic—AI is only used for querying and content generation . **Best for teams wanting multi-cloud security posture** with attack path analysis—but it is a newer project and the AI querying requires API keys.



- **[Poirot DSPM](https://github.com/safernandez666/poirot-public)**  

  An **open-source Data Security Posture Management (DSPM)** scanner . Features: **multi-source scanning** (MySQL, S3, Apache Kafka, Google Drive, OneDrive); **sensitive data detection** (credit cards, credentials, PII) with severity classification; **TheHive 5 integration** for automatic case creation; **multi-channel notifications** (Slack, Email, Teams, Webhooks); **scheduled scans**; and **PDF/Excel/JSON reports** with AI-powered analysis via Ollama . **Best for organizations already using TheHive** wanting DSPM with incident management integration—but it is a focused scanner, not a full CSPM.



### Cloud Compliance & Evidence



- **[aws-compliance-as-code](https://pypi.org/project/aws-compliance-as-code/)**  

  Open-source **automated compliance evidence** for AWS mapped to NIST 800-53, SOC 2, ISO 27001, and CIS AWS Foundations . Features: **control catalog** with crosswalk to multiple frameworks (test once, satisfy many); **read-only API checks** returning PASS/FAIL with raw responses; **SHA-256 hashed evidence** for tamper detection; **OSCAL 1.1.2 export** for GRC tool ingestion; and **offline testing** via moto with unit tests . **Best for AWS teams** wanting repeatable, auditable evidence without manual screenshots—but it covers only 15 controls currently (VPC flow logs and AWS Config recorder not yet implemented) .



- **[compliancekit](https://pkg.go.dev/github.com/darpanzope/compliancekit)**  

  Open-source **compliance and security scanner** for cloud and Linux infrastructure (Go, v0.2.0) . Generates **audit-ready evidence packs** for SOC 2, ISO 27001, and CIS benchmarks; supports DigitalOcean checks and Linux SSH collection . **Best for teams wanting a lightweight compliance scanner** for cloud and Linux—but it is early-stage (v0.2.0) with limited provider coverage.



### Data Sanitization & Privacy



- **[SDSA (Secure Data Sanitization App)](https://pypi.org/project/sdsa/)**  

  Open-source **self-hostable tool for sanitizing tabular data** before it leaves a trusted environment . Features: **PII detection** (email, phone, card number, government ID, DOB, name, address); **per-column privacy policies** (retain, mask, hash, tokenize, redact, drop, numeric bin, date truncate, string truncate, Laplace noise); **k-anonymity enforcement** over quasi-identifiers; **preflight suppression estimates**; and **JSON/Markdown privacy reports** . **Best for teams** wanting to safely share datasets with external parties—but it is a sanitization tool, not a full data security platform.



- **[CloakDB](https://pypi.org/project/cloakdb/)**  

  Open-source **database anonymization** tool (Python) with **strict O(1) memory** on large dumps . Features: supports Postgres, MySQL, SQLite, Parquet, CSV, JSONL; **format-preserving encryption** (NIST SP 800-38G FF1/FF3-1); **Luhn/checksum preservation** for credit cards and SSNs; **differential privacy budget tracking**; **signed SOC2/ISO 27001 audit trails** (HMAC-SHA256); **referential integrity** with automatic multi-table mapping; and **schema drift/PII linting** . Benchmarks show ~180k-204k rows/s on 10GB-50GB datasets with ~50-68MB peak RAM . **Best for teams** needing to sanitize large database dumps for staging/development—not a runtime data security tool.



**Frameworks for building custom systems**: For **secrets management**, Secrets provides a lightweight, auditable MIT-licensed Vault alternative with envelope encryption and transit APIs . For **PAM**, JumpServer provides mature, GPLv3 browser-based privileged access , while Thand offers JIT access with zero standing privileges . For **cloud security posture**, Mantissa Stance combines CSPM, DSPM, and CIEM with attack path analysis , and Poirot DSPM focuses on sensitive data discovery with TheHive integration . For **compliance evidence**, aws-compliance-as-code provides hashed, OSCAL-exportable AWS evidence . No open-source project matches the **integrated compliance automation and auditor workflows** of Vanta or Drata—those require commercial platforms or significant custom integration.



## How to Contribute



1. Fork the repo.

2. Add/edit entries in `README.md` (follow existing format).

3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.

4. Submit PR with a short explanation.



Star the repo if you find it useful!



## Disclaimer



- This is a **community-curated** list — not exhaustive and not an endorsement.

- Mission-critical data security platforms handling encryption keys, privileged credentials, and sensitive data must comply with applicable regulations (PCI DSS, SOC 2, ISO 27001, GDPR) and organizational security policies; **self-hosted solutions place full responsibility for key management, access controls, and audit integrity on the operator**.

- **Open-source mission-critical data security is capable but fragmented across layers**—Secrets provides lightweight secrets management , JumpServer provides mature PAM , Mantissa Stance provides multi-cloud posture , and aws-compliance-as-code provides AWS evidence . However, **no open-source project matches the integrated breadth and managed reliability** of Vanta (compliance automation) or CyberArk (enterprise PAM). Choose based on whether you need secrets (Secrets), privileged access (JumpServer, Thand), posture (Mantissa Stance, Poirot), or compliance evidence (aws-compliance-as-code)—and plan for integration across these layers.

- Verify license terms for commercial use; Secrets uses MIT , JumpServer uses GPLv3 , Thand uses BSL 1.1 , and aws-compliance-as-code is open-source (check repository).



---



**Made for security architects, platform engineers, and organizations protecting mission-critical cloud data.**  

Let's make cloud data security more open, but with clear eyes about the integrated compliance and enterprise PAM gaps that commercial platforms still fill.
