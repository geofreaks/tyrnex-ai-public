# TYRNEX-AI Public Runtime

**Autonomous Security Intelligence**  
Discover. Validate. Defend. - Predict. Detect. Protect.

TYRNEX-AI is a local, safe-by-default security assessment dashboard for authorized testing. It helps you discover assets, review exposure, analyze evidence, build timelines, map findings to security frameworks, and produce remediation-ready reports.

**Best for:** home labs, small-business security reviews, blue-team triage, defensive validation, evidence review, and local-first cyber assessments.

**Short version:** download the runtime kit, run it locally, assess only systems you own or are authorized to test, then export findings, topology, timelines, and remediation reports.

This public repository is the download channel for the protected local runtime kit. It does not contain the private source repository, Git history, private tests, case data, secrets, API keys, raw evidence, or local databases.

## Platform Support

TYRNEX-AI is currently supported and tested on Windows 10/11. The launchers, first-run setup, tool bootstrap, optional integrations, Host Assessment, Host Acquire, DFIR helpers, and rogue LAN probe workflows are Windows-first. Linux components are contained lab/WSL/VM pieces launched from the Windows workflow. macOS is not a supported runtime today.

## Why People Use It

- **Local-first:** case data, uploads, findings, and reports stay on the machine where the kit runs.
- **Assessment workflow:** Discover -> Findings -> Verify -> Remediate -> Report.
- **Cyber triage:** analyze mixed evidence folders, logs, exports, configs, timelines, and scanner output.
- **Defensive by design:** safe checks, evidence confirmation, and check-only validation instead of autonomous exploitation.
- **Report-ready:** remediation guidance, control mappings, timelines, topology exports, and Word/PDF-capable reporting.

## Related Project

- [CybSec-AI Community](https://github.com/geofreaks/cybsec-ai-community) is the public home for the web-based defensive AI workbench, including beta feedback, docs, roadmap, and safe issue reporting.
- Hosted CybSec-AI beta: https://www.cybsec-ai.com/

TYRNEX-AI is the local assessment, triage, and reporting runtime. CybSec-AI is the companion AI/analyzer workbench. They can exchange exported evidence and reports, but this TYRNEX-AI runtime does not require CybSec-AI to install or run.

## Download

- [Download TYRNEX-AI Local Runtime Kit](downloads/TYRNEX-AI-Local-Runtime-Kit.zip)
- [SHA256 checksum](downloads/TYRNEX-AI-Local-Runtime-Kit.zip.sha256)

If GitHub warns that the ZIP is large, use the link above from the repository page or download it from the latest public release when one is published.

## Quick Start

1. Download and extract `TYRNEX-AI-Local-Runtime-Kit.zip`.
2. Double-click `Run This First.cmd`.
3. After setup, use `Start TYRNEX-AI.cmd`.
4. Open the dashboard at `http://127.0.0.1:8765`.

The first-run setup creates a local `.venv`, installs runtime dependencies, checks the protected runtime, and can bootstrap supported free tools into the kit's own `tools` folder. If the PC has no usable Python, it downloads Python 3.11.9 into `.runtime\python` inside the kit. If the kit is moved between Windows PCs and `.venv` points to the old machine, the launchers rebuild it.

## Offline Use

The public runtime is local-first, but it is not magically offline before first setup.

Best offline prep:

1. Extract the kit on an internet-connected Windows machine.
2. Run `Run This First.cmd`.
3. Run `Install All Tools.cmd` if you want scanner/DFIR tools available offline.
4. Run `Check Optional Integrations.cmd` and confirm required tools are green.
5. Copy the entire prepared folder to USB or the offline machine, including `.venv`, `.runtime`, `tools`, and `data` if you want that local case history.
6. Launch offline with `Start TYRNEX-AI.cmd`.

Works offline after prep:

- Dashboard and local case database
- Evidence upload/folder analysis
- Host Acquire imports and built-in disk triage logic
- Cyber Triage / Host Exam over local evidence
- Reports, timelines, topology, and exports
- Any scanners or DFIR tools already installed under `tools\`

Needs internet:

- First-run Python package install
- `Install All Tools.cmd` downloads
- CVE, EPSS, KEV, public threat intel, and enrichment refreshes
- Optional ZAP/Metasploit installer downloads
- Downloading a newer public runtime kit

## What TYRNEX-AI Does

- **Discover** authorized hosts, services, web endpoints, and attack surface.
- **Findings** normalize scanner, host, web, cloud, code, and evidence results.
- **Verify** supports safe, check-only validation and manual evidence confirmation.
- **Host Assessment** reviews local or networked Windows posture without exploit actions.
- **Cyber Triage / Analyzer** ingests mixed evidence folders and uploads such as EVTX exports, logs, firewall configs, forensic summaries, memory/disk triage manifests, scanner output, SBOMs, IOC lists, and report files.
- **Timeline and Topology** build correlated event timelines and asset maps from discovered or imported evidence.
- **Reports** produce remediation-ready case outputs, including Word/PDF-capable cyber triage reporting from the local dashboard/runtime.
- **Framework Mapping** ties findings to practical security references such as NIST CSF, NIST 800-53, CIS Controls, MITRE ATT&CK, OWASP, and incident-response guidance.

## Safety Model

Use TYRNEX-AI only on systems you own or are explicitly authorized to assess.

The public runtime is designed around safe assessment workflows:

- No stealth, persistence, destructive actions, payload delivery, credential theft, or autonomous exploitation.
- Metasploit integration is for check-only/exploit-intelligence validation, not live exploit execution.
- Report redaction is optional and report-scoped; the local UI and logs preserve raw evidence for your own case work.
- Live scans and validations should be run only against authorized targets.

## Optional Tools

Run:

```powershell
.\Install All Tools.cmd
```

This installs or links bootstrap-supported tools when possible. Already-present tools are skipped.

The bootstrap-supported DFIR set includes WinPmem, Hayabusa, Chainsaw, Volatility3, Velociraptor, AVML, and Eric Zimmerman's Windows parsers. KAPE is not redistributed because the official Kroll download is gated; place it under `tools\kape\` if you use it. Velociraptor endpoint collection on Windows may require UAC/elevation.

You can also run:

```powershell
.\Check Optional Integrations.cmd
.\Install OWASP ZAP Integration.cmd
.\Install Metasploit Integration.cmd
```

OWASP ZAP wrappers can be installed and counted by TYRNEX-AI even before the full ZAP application is installed. For live ZAP scans, install OWASP ZAP from the official project site.

Metasploit is optional and may require Administrator rights on Windows. The integration script checks common install locations, tries supported package IDs when available, and can fall back to Rapid7's official Windows MSI flow. Once installed or linked, TYRNEX-AI uses it for check-only validation workflows.

## Share / Star

If TYRNEX-AI helps your lab or security review workflow:

- Star this repository so others can find it.
- Share the public runtime link: https://github.com/geofreaks/tyrnex-ai-public
- Open an issue with safe feedback, bugs, packaging notes, or feature requests.

Please do not post secrets, real customer evidence, private logs, or exploit targets in public issues.

## Local Data

TYRNEX-AI stores case data locally inside the extracted kit:

```text
data\TYRNEX-AI.db
data\cases\<case-key>\
tools\
```

The public download does not include your previous case data, uploads, reports, API keys, or `.env` files.

## Protected Runtime Notes

The public kit removes raw Python product source and ships a compiled Python-bytecode runtime. This protects the private repo and source history while still letting public testers run the product locally.

No local software distribution can be impossible to inspect or reverse engineer. Treat this as practical source protection, not cryptographic secrecy.

## Updating

The public runtime does not pull from the private TYRNEX-AI repository. New versions are published here as refreshed runtime-kit downloads.

To update:

1. Download the latest public zip.
2. Extract it to a new folder.
3. Run `Run This First.cmd`.
4. Move or export/import case data only if you intentionally want to carry it forward.

## Useful Commands

From the extracted kit folder:

```powershell
.\Run This First.cmd
.\Start TYRNEX-AI.cmd
.\Install All Tools.cmd
.\Check Optional Integrations.cmd
```

Advanced users can run:

```powershell
.\.venv\Scripts\python.exe -m tyrnex_ai.cli doctor
.\.venv\Scripts\python.exe -m tyrnex_ai.cli dashboard --db .\data\TYRNEX-AI.db --host 127.0.0.1 --port 8765 --open
```

## Public Release Contents

Safe contents:

- `README.md`
- `downloads/TYRNEX-AI-Local-Runtime-Kit.zip`
- `downloads/TYRNEX-AI-Local-Runtime-Kit.zip.sha256`

Not included:

- Private TYRNEX-AI source tree
- Private Git history
- Developer tests
- `.env` files or API keys
- Raw evidence, reports, uploads, or case databases
- Private vulnerable-lab source
