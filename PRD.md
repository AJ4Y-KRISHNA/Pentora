# Pentora (v1.0) - Product Requirements Document

## Project Vision
To create the fastest, high-fidelity web vulnerability scanner that proves every finding and maps the road to full compromise.

## 1. Executive Summary
Pentora is a terminal-first vulnerability scanner designed to bridge the gap between signature-based scanning (Nuclei) and enterprise auditing (Nessus). Unlike traditional tools that output "potential" bugs, Pentora focuses on validated exploitation and attack path visualization.

## 2. Core Features (The "Power Seven")

### F1: Recon-to-Scan Pipeline ("Asset Radar")
*   **Description:** Continuous discovery engine that feeds the scanner.
*   **Requirement:** Integration with passive OSINT (Shodan/Censys) and active subdomain brute-forcing.
*   **Workflow:** User inputs a root domain (example.com) -> Pentora finds all subdomains -> Automatically starts scanning new subdomains as they appear.

### F2: "JS-Deep" Analyzer
*   **Description:** A headless browser engine that "reads" client-side code.
*   **Requirement:** Must de-obfuscate JavaScript files to extract hidden API endpoints, hardcoded credentials, and developer "TODO" comments.
*   **Goal:** Discover the "hidden" attack surface that standard crawlers miss.

### F3: Verified Exploit Badge (Zero False Positives)
*   **Description:** A "Confirmed" status for high-confidence bugs.
*   **Requirement:** If a vulnerability is found, Pentora cross-references it with a second "active" check.
*   **Output:** Findings are marked with a green checkmark if they are 100% verified.

### F4: Automated Proof of Concept (PoC)
*   **Description:** Instant reproduction for every verified bug.
*   **Requirement:** For every SQLi, XSS, or SSRF found, Pentora generates a curl command or a Python script that reproduces the bug safely.
*   **Goal:** Allow the user to copy-paste the proof directly into a report.

### F5: AI-Driven Attack Path Analysis
*   **Description:** A logical map of how small bugs lead to big breaches.
*   **Requirement:** Uses an LLM to analyze a cluster of low/medium findings (e.g., Info Leak + Weak Config + Old Plugin) and predicts a path to RCE or Data Exfiltration.

### F6: Auto-Remediation "Fix-it" Scripts
*   **Description:** One-click solutions for developers.
*   **Requirement:** For every finding, generate the exact fix (e.g., the specific line of Nginx config to add a missing header or the code snippet to sanitize an input).

### F7: One-Click Bug Bounty Report Generator
*   **Description:** Automation of the most tedious part of pentesting.
*   **Requirement:** Export findings into a pre-formatted Markdown file ready for HackerOne, Bugcrowd, or custom PDF reporting.

## 3. Technical Requirements

| Component | Technology | Description |
| :--- | :--- | :--- |
| **Core Engine** | Go (Golang) | For concurrency and speed. |
| **Parsing** | Colly / Playwright | For deep JS crawling. |
| **AI Layer** | OpenAI API / Local Llama | For Attack Path Analysis. |
| **Database** | PostgreSQL | To store history and asset discovery logs. |
| **CLI** | Cobra / Viper | For a professional terminal experience. |

## 4. User Experience (UX)
*   **Installation:** Must be a one-liner: `curl -sL https://pentora.io/install.sh | bash`
*   **Interface:** Color-coded terminal output (Aura/Dracula theme style) with progress bars for each asset.
*   **Commands:**
    *   `pentora scan -u https://target.com` (Quick scan)
    *   `pentora radar -d target.com` (Continuous recon)
    *   `pentora report --format h1` (Export to HackerOne)

## 5. Success Metrics
*   **Time to Proof:** A user should have a verified PoC within 5 minutes of starting a scan.
*   **Accuracy:** 0% false positives on "Verified" badged findings.
*   **Discovery:** Finding at least 20% more API endpoints than traditional crawlers via the JS-Deep Analyzer.
