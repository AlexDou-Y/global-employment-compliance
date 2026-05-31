[English](README.md) | [中文](README.zh-CN.md)

# Global HR Compliance Playbook

[![Version](https://img.shields.io/badge/version-1.0-blue.svg)]()
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Skill-orange.svg)](https://docs.claude.com/en/docs/claude-code)
[![Language](https://img.shields.io/badge/lang-English-blue.svg)](README.md)

> Global HR Compliance & Operations Expert — A Claude Code Skill for generating country-specific employment compliance handbooks, querying local labor law details, and answering overseas HR practical questions.

Target users: Multinational HR teams, expatriate project managers, global employment service providers, labor law consultants.

---

## Core Features

- **Four-Mode Auto Dispatch**: Workflow scales to request complexity — simple queries get direct answers, complex tasks trigger the full 9-step process. No more "running a 9-step research workflow just to ask about minimum wage"
- **Hard Anti-Hallucination Constraints**: Every fact must carry a source URL; conflicting sources are flagged with `⚠️ Conflicting interpretations — consult local counsel` rather than fabricating certainty; if search tools fail, the skill explicitly degrades to "based on model knowledge, requires human verification" instead of silently relying on memory
- **14-Chapter Standard Structure**: Covers the full employee lifecycle — preface, country overview, recruitment, compensation, income tax, social security, contracts, leave, unions & employee handbook, data compliance, labor disputes, forex, risk warnings, resources
- **Three-Layer Content Model**: Rules layer (legal provisions) + Practice layer (how companies execute) + Risk layer (common issues & prevention)
- **Persistent Research**: Research content is written to disk in real time, avoiding auto-compact context loss. The skill explicitly names "outputting from memory" as failure mode #1
- **Three-Stage Quality Validation**: Structure pass (numbering, headings) → Content pass (gaps, tables, links) → Practice pass (numbers, steps, executability), each pass run independently
- **Incremental Update Support**: Update specific chapters individually without regenerating the entire handbook

---

## Operating Modes (Mode Dispatch)

The skill auto-detects the right mode for your request — **you don't pick manually**:

| Mode | Trigger | Workflow Depth | Output |
|:-----|:--------|:---------------|:-------|
| **A. Full Handbook** | "Generate a [country] employment compliance handbook" | Full 9-step workflow | 14-chapter handbook `.md` file |
| **B. Quick Lookup** | "What's the minimum wage in X" | Targeted search → concise answer | Direct answer + source links, no file |
| **C. Practice Q&A** | "How do we terminate compliantly in Germany" | Simplified multi-step | "Steps + Risks + Documents" answer, no file |
| **D. Incremental Update** | "Update the minimum wage section of the Korea handbook" | Diff workflow | Updates relevant chapters |

> Modes B/C don't require file creation, but **still enforce source citation, uncertainty flagging, and professional-review prompts**.

---

## Installation

### Prerequisites

- [Claude Code](https://docs.claude.com/en/docs/claude-code) installed
- System: Windows / macOS / Linux

### Method 1: Clone to skills directory

```bash
# Linux / macOS
git clone https://github.com/AlexDou-Y/global-hr-compliance-playbook.git \
  ~/.claude/skills/global-hr-compliance-playbook

# Windows (Git Bash / PowerShell)
git clone https://github.com/AlexDou-Y/global-hr-compliance-playbook.git \
  "$HOME/.claude/skills/global-hr-compliance-playbook"
```

### Method 2: Manual download

1. Download this repository as ZIP and extract
2. Copy the entire `global-hr-compliance-playbook/` directory to:
   - Linux / macOS: `~/.claude/skills/`
   - Windows: `%USERPROFILE%\.claude\skills\`

### Verify Installation

Launch Claude Code, type `/skills` to view available skills list, you should see `global-hr-compliance-playbook`.

---

## Usage

Just describe your need in natural language — the skill picks the right mode automatically.

### Mode A: Generate Complete Compliance Handbook

```
Generate a Singapore employment compliance handbook for me
Make a South Korea employment compliance handbook
```

**Output**:
- File: `新加坡用工合规手册_YYYYMMDD_V1.0.md` (Chinese filename, current default)
- Location: same directory as the skill itself (relative path, so the skill can be renamed/moved)
- Format: Markdown (compatible with Lark, Notion, Confluence), with tables, diagrams, legal links
- Current version outputs Chinese handbooks; multilingual output is on the [roadmap](#roadmap)

### Mode B: Quick Labor Law Queries

```
What is the minimum wage in South Korea?
What are the probation period regulations in UAE DIFC?
How is overtime pay calculated in California, USA?
```

→ Concise answer + official source links, no file created.

### Mode C: Compliance Practice Consultation

```
We need to terminate an employee in Germany, what should we pay attention to?
What procedures are required for foreign employees to work in Japan?
How to conduct large-scale layoffs compliantly in France?
```

→ "Steps + Risks + Required documents" practical answer.

### Mode D: Incremental Updates to Existing Handbooks

```
Update the minimum wage section of the South Korea handbook to 2026 latest data
Based on current regulatory changes, add a remote work policy section to the Dubai handbook
```

---

## Output Example

Full handbooks follow a unified 14-chapter structure:

```
Chapter 1   Preface (Scope, Version Notes)
Chapter 2   Country/Region Overview
Chapter 3   Recruitment
Chapter 4   Compensation
Chapter 5   Personal Income Tax
Chapter 6   Social Insurance & Provident Fund
Chapter 7   Employment Contract (incl. termination & severance)
Chapter 8   Leave & Time Off
Chapter 9   Unions & Employee Handbook
Chapter 10  Data Compliance
Chapter 11  Labor Disputes
Chapter 12  Foreign Exchange & Cross-Border Payments
Chapter 13  Risk Warnings
Chapter 14  Resources (links, templates, toolkits)
```

Each provision follows the "Rules → Practice → Risk" three-layer structure, with legal source links attached.

---

## Anti-Hallucination Mechanism

Compliance handbooks have asymmetric error costs (one wrong severance rule can trigger litigation), so this skill treats anti-hallucination as a **hard constraint**, not a guideline:

| Mechanism | Implementation |
|:----------|:---------------|
| **Source priority** | Government sites / official legal text > top-tier law firms / Big Four > professional media; explicitly banned: anonymous wikis, personal blogs, AI-generated content |
| **Mandatory citations** | Every extracted fact must carry URL + retrieval timestamp; output principle #9: "no fabrication permitted" |
| **Explicit uncertainty** | Conflicting sources → `⚠️ Conflicting interpretations`; high-risk matters → flag for local counsel / tax / immigration review |
| **Degrade, don't go silent** | If tools fail: "⚠️ No official source retrieved — based on model knowledge, requires human verification". Silently using memory is forbidden |
| **No "from memory" output** | The skill explicitly states "outputting from memory is failure mode #1"; spec must be re-read before drafting each chapter |
| **Persistent on disk** | Research is written to a draft file in real time, so auto-compact can't force you to reconstruct from impressions |
| **Rule-tier separation** | Legal mandate / official enforcement practice / market convention / company discretion / requires-professional-review — prevents "common practice" being dressed up as "the law" |

> Note: these are process constraints, not technical interception. The model can still err, so **a licensed local attorney must review before formal use** (see [Disclaimer](#disclaimer)).

---

## How It Works (Mode A Full Flow)

```
User Request
   ↓
[Mode Detection]  ── B/C/D ──→ Simplified flow
   ↓ A
[1. Scope confirmation + create draft file]
   ↓
[2. Broad information collection → real-time write to draft]
   ↓
[3. Information distribution → assign by chapter, mark gaps]
   ↓
[4. Per-module deep research → real-time draft update, check against spec]
   ↓
[5. Pre-output spec compliance check]  ⚠️ Mandatory — cannot be skipped
   ↓
[6. Batch output handbook to conversation]
   ↓
[7. Mandatory write to final file (Edit batch append)]
   ↓
[8. Three-stage quality validation]  Structure → Content → Practice
   ↓
[9. Closeout]  Targeted re-search, finalize file
```

See [ARCHITECTURE.md](ARCHITECTURE.md) for details.

---

## Directory Structure

```
global-hr-compliance-playbook/
├── skill.md                    # Main entry (Claude loads this file)
├── README.md                   # This document (English)
├── README.zh-CN.md             # Chinese version
├── ARCHITECTURE.md             # Architecture documentation
├── CHANGELOG.md                # Version changelog
├── LICENSE                     # MIT License
├── 1_core/                     # Role, capabilities, output principles
├── 2_tools/                    # Tool configuration (Web Search strategy)
├── 3_workflow/                 # Workflow (research process, quality validation, incremental update — 13 sub-flows)
├── 4_output/                   # Output specifications (format templates, terminology, chapter scale)
├── 5_spec/                     # Chapter specifications (14 chapters + mandatory questions + naming)
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
