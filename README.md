[English](README.md) | [中文](README.zh-CN.md)

# Global Employment Compliance

[![Version](https://img.shields.io/badge/version-16.0-blue.svg)]()
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Skill-orange.svg)](https://docs.claude.com/en/docs/claude-code)
[![Language](https://img.shields.io/badge/lang-English-blue.svg)](README.md)

> Global HR Compliance & Operations Expert — A Claude Code Skill for generating country-specific employment compliance handbooks, querying local labor law details, and answering overseas HR practical questions.

Target users: Multinational HR teams, expatriate project managers, global employment service providers, labor law consultants.

---

## Core Features

- **14-Chapter Standard Structure**: Covers full employee lifecycle — preface, country overview, recruitment, compensation, income tax, social security, contracts, termination, leave, unions, data compliance, labor disputes, forex, risk warnings, resources
- **Three-Layer Content Model**: Rules layer (legal provisions) + Practice layer (how companies execute) + Risk layer (common issues & prevention)
- **Three-Stage Research Workflow**: Official regulations → Authoritative interpretations → Targeted supplementation, automated phased research
- **27-Point Quality Checklist**: Mandatory pre-output validation ensuring complete coverage, accurate content, standardized format
- **Persistent Research**: Research content written to disk in real-time, avoiding auto-compact context loss
- **Incremental Update Support**: Update specific chapters individually without regenerating the entire handbook

---

## Installation

### Prerequisites

- [Claude Code](https://docs.claude.com/en/docs/claude-code) installed
- System: Windows / macOS / Linux

### Method 1: Clone to skills directory

```bash
# Linux / macOS
git clone https://github.com/AlexDou-Y/global-employment-compliance.git \
  ~/.claude/skills/global-employment-compliance

# Windows (Git Bash / PowerShell)
git clone https://github.com/AlexDou-Y/global-employment-compliance.git \
  "$HOME/.claude/skills/global-employment-compliance"
```

### Method 2: Manual download

1. Download this repository as ZIP and extract
2. Copy the entire `global-employment-compliance/` directory to:
   - Linux / macOS: `~/.claude/skills/`
   - Windows: `%USERPROFILE%\.claude\skills\`

### Verify Installation

Launch Claude Code, type `/skills` to view available skills list, you should see `global-employment-compliance`.

---

## Usage

### Scenario 1: Generate Complete Compliance Handbook

Simply describe your need in Claude Code:

```
Generate a Singapore employment compliance handbook for me
```

Or explicitly invoke:

```
/global-employment-compliance Generate South Korea employment compliance handbook
```

**Output**:
- File: `Singapore_Employment_Compliance_Handbook_YYYYMMDD_V1.0.md`
- Location: `~/.claude/skills/global-employment-compliance/`
- Format: Markdown (compatible with Lark, Notion, Confluence), with tables, diagrams, legal links

### Scenario 2: Quick Labor Law Queries

```
What is the minimum wage in South Korea?
What are the probation period regulations in UAE DIFC?
How is overtime pay calculated in California, USA?
```

### Scenario 3: Compliance Practice Consultation

```
We need to terminate an employee in Germany, what should we pay attention to?
What procedures are required for foreign employees to work in Japan?
How to conduct large-scale layoffs compliantly in France?
```

### Scenario 4: Incremental Updates to Existing Handbooks

```
Update the minimum wage section of the South Korea handbook to 2026 latest data
Based on current regulatory changes, add a remote work policy section to the Dubai handbook
```

---

## Output Example

Generated handbooks follow a unified structure:

```
Chapter 1  Preface (Scope, Version Notes)
Chapter 2  Country/Region Overview
Chapter 3  Recruitment & Onboarding
Chapter 4  Compensation & Benefits
Chapter 5  Personal Income Tax
Chapter 6  Social Insurance & Provident Fund
Chapter 7  Employment Contracts
Chapter 8  Contract Termination & Compensation
Chapter 9  Leave & Time Off
Chapter 10 Unions & Employee Representatives
Chapter 11 Data Protection & Compliance
Chapter 12 Labor Disputes & Litigation
Chapter 13 Foreign Exchange & Cross-Border Payments
Chapter 14 Risk Warnings & Resource Summary
```

Each provision follows the "Rules → Practice → Risk" three-layer structure, with legal source links attached.

---

## Directory Structure

```
global-employment-compliance/
├── skill.md                    # Main entry (Claude loads this file)
├── README.md                   # This document (English)
├── README.zh-CN.md             # Chinese version
├── ARCHITECTURE.md             # Architecture documentation
├── CHANGELOG.md                # Version changelog
├── LICENSE                     # MIT License
├── 1_core/                     # Core rules (compliance expert positioning, principles)
├── 2_tools/                    # Tool configuration (Web Search strategy, etc.)
├── 3_workflow/                 # Workflows (research process, quality validation, incremental updates)
├── 4_output/                   # Output specifications (format templates, terminology standards, chapter scale)
├── 5_spec/                     # Chapter specifications (14 chapters detailed requirements)
└── 6_meta/                     # Metadata
```

---

## Supported Countries/Regions

Theoretically supports any country/region, tested and verified:

- **East Asia**: Japan, South Korea, Hong Kong (China)
- **Southeast Asia**: Singapore, Malaysia, Indonesia, Vietnam, Thailand
- **Middle East**: UAE (including DIFC), Saudi Arabia
- **Europe & Americas**: USA (Federal & California), UK, Germany, France

> Note: For regions with rapidly changing regulations (e.g., EU), manual review of latest legislative updates is recommended after handbook generation.

---

## How It Works

```
User Request
   ↓
[Scope Confirmation] → Create draft file
   ↓
[Stage 1] Official regulations collection → Real-time write to draft
   ↓
[Stage 2] Authoritative interpretation supplementation → Real-time write to draft
   ↓
[Stage 3] Information distribution → Assign by chapter
   ↓
[Quality Validation] 27-point checklist
   ↓
[Final Write] Batch Edit write to formal file
   ↓
[HRBP Perspective Review] Completeness + Practical executability
```

See [ARCHITECTURE.md](ARCHITECTURE.md) for details.

---

## Disclaimer

Compliance handbooks generated by this skill are **for reference only** and **do not constitute legal advice**. Labor laws vary greatly across countries and change frequently. Before formal application:

1. Have local licensed attorneys or professional consulting firms review
2. Monitor regulatory updates (validity periods noted in handbooks)
3. Adjust execution details based on company-specific circumstances

Authors and contributors assume no responsibility for any legal or business consequences arising from use of this tool.

---

## Roadmap

- [x] English README (International Edition)
- [ ] Multi-language handbook output support (English / 日本語 / 한국어)
- [ ] Integration with Claude Code Plugin Marketplace
- [ ] Chapter template visual preview

---

## Contributing

Issues and Pull Requests are welcome:

- **Report Issues**: Regulatory errors, template defects, workflow improvement suggestions
- **Add Countries**: Contribute tested country handbooks as reference samples
- **Improve Prompts**: Optimize research stage search strategies, quality validation checklists

Please read [CHANGELOG.md](CHANGELOG.md) before submitting PRs to understand version evolution.

---

## License

[MIT](LICENSE) © 2026

---

## Related Resources

- [Claude Code Official Documentation](https://docs.claude.com/en/docs/claude-code)
- [Anthropic Skills Repository](https://github.com/anthropics/skills)
- [Skill Development Guide](https://docs.claude.com/en/docs/claude-code/skills)
