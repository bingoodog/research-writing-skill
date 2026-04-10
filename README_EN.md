# Writing Assistant

> 📄 中文版：[README.md](README.md)

Upgrade "writing tasks" from one-off chat sessions into a trackable, recoverable, and reusable engineering-style collaboration workflow.  
Supports both **academic paper writing** and **engineering/software project document writing**, designed for undergraduates, graduate students, engineers, and project managers.

![Writing Assistant Workflow](assets/readme/workflow.png)

## What This Is

This is not a prompt pack that only polishes sentences. It is a complete writing collaboration system.  
Before starting any task, it aligns goals and constraints through a brainstorming process to confirm document type, background, and structure, then routes to the appropriate skill module based on task type.

Use cases:
- Undergraduate/graduate theses, journal submissions, conference papers, course papers
- Software Requirements Specifications (SRS), technical design documents
- Project feasibility reports, project closure reports, progress reports
- System architecture documents, test reports

## Core Capabilities

- **Brainstorming**: Q&A to confirm document type, audience, background, methods, and chapter structure
- **AI-assisted writing**: From topic/project initiation, body writing, and figure generation to pre-delivery self-review, executed with stage gates
- **De-AI writing**: Constrains mechanical transition words, hollow emphasis phrases, subjective expressions, and bullet-point dumping (papers)
- **Project document standards**: SMART requirements, conclusion-first structure, audience-oriented writing, verifiability checks (project docs)
- **Discipline-specific writing support**: Routed modules for engineering, social sciences, medicine, and law
- **Literature review support**: Integration of English-language search and Chinese literature organization
- **LaTeX template support**: Provide your institution/journal template; auto-generates a compilable LaTeX project
- **Environment automation**: Miniconda installation, virtual environment creation, plotting dependency setup and troubleshooting

## Supported Platforms

This Skill uses a directory-based design, adapted for the following platforms:

| Platform | Configuration |
|----------|---------------|
| Claude Code | `.claude-plugin/plugin.json` |
| Cursor | `.cursor-plugin/plugin.json` |
| Codex | `.codex/INSTALL.md` |
| OpenCode | `.opencode/INSTALL.md` |
| Gemini CLI | `GEMINI.md` |
| Others | `AGENTS.md` |

## What You Get

By default, Skill outputs are project files — not finished Word documents.

| Output Type | Default Format | Notes |
|---|---|---|
| Paper body | `.md` / `.tex` | Suitable for version control and further processing |
| Project document body | `.md` / `.docx` (via Pandoc) | One file per chapter/section |
| Chapter/section files | `chapters/*.md` | One file per chapter/section |
| LaTeX project | `chapters/*.tex` + `main.tex` | Directly compilable (papers) |
| Figure scripts | `.py` | Reproducible figure generation logic |
| Prompt assets | `.md` | Reusable templates for translation, polishing, and de-AI-ification |

## Important Boundaries (Read First)

1. The Skill does not automatically generate or write directly to `.docx` files by default.
2. The Skill does not open Word and apply formatting on your behalf — you will need to copy manually or use a conversion tool.
3. The Skill can generate plain-text paragraphs ready to paste into Word, but final styling (heading levels, headers/footers, table of contents, reference fields) must be handled in Word.
4. References and data are never fabricated; all citations must be traceable. Please independently verify high-risk conclusions.

## Installation

### Option 1: Direct Download

Download the repository, extract it, and copy `research-writing-skill/` into your writing project directory.

### Option 2: Git Clone

```bash
git clone https://github.com/bingoodog/research-writing-skill.git
cd research-writing-skill
```

### Platform-specific Installation

- **Codex**: See `.codex/INSTALL.md`
- **OpenCode**: See `.opencode/INSTALL.md`
- **Others**: Place the entire directory in your project root

## Real Usage Example (Input → Output)

![Real Usage Example: Input to Output](assets/readme/real-case-input-output.png)

## Standard Collaboration Workflow (Recommended)

1. **Brainstorming**: Say "I want to write a paper" or "I want to write a requirements document", the Skill will guide you to confirm document type, background, audience, etc.
2. **Chapter/section planning**: After confirming structure, the Skill creates a framework in `chapters/`
3. **Section-by-section writing**: Write one section at a time, one file per section
4. **Figure generation**: When data figures or architecture diagrams are needed, the Skill generates corresponding scripts or diagram descriptions
5. **Self-review**: Use the peer-review skill for pre-delivery self-review
6. **Delivery**: Manually migrate to Word/LaTeX for final formatting

## Skill Map

| Scenario | Skill |
|---|---|
| Entry and routing | `skills/using-research-writing/` |
| Brainstorming (papers and project docs) | `skills/brainstorming-research/` |
| Paper chapter writing | `skills/writing-chapters/` |
| Project document writing (SRS/design/reports) | `skills/writing-project/` |
| LaTeX output | `skills/latex-output/` |
| General writing standards | `skills/writing-core/` |
| Humanities / social science writing | `skills/writing-humanities/` |
| Medical / biology writing | `skills/writing-medical/` |
| Law writing | `skills/writing-law/` |
| Literature review | `skills/literature-review/` |
| Translation / polishing / de-AI | `skills/prompts-collection/` |
| Pre-submission / pre-delivery self-review | `skills/peer-review/` |
| Statistical analysis | `skills/statistical-analysis/` |
| Python figures | `skills/figures-python/` |
| Flowcharts / architecture diagrams | `skills/figures-diagram/` |
| Environment setup and troubleshooting | `skills/environment-setup/` |

## LaTeX Template Usage

If you have a LaTeX template from your institution or journal:

1. Place template files (`.cls`, `.sty`, `.tex`, etc.) in `latex-templates/` directory
2. Tell the AI "use my LaTeX template"
3. The AI will parse template structure and generate corresponding `.tex` chapter files

See `latex-templates/README.md` for details.

## Delivering Markdown to Word

### Option A: Manual Copy (Default Recommendation)

1. Ask the Skill to output a "plain-text paragraph version" (avoiding Markdown markers)
2. Copy the body in your editor and paste it into Word
3. Apply your institution's template styles in Word (headings, body text, captions)
4. Manually check equations, references, figure/table numbers, and cross-references

### Option B: Pandoc Conversion (Optional)

If you have Pandoc installed locally:

```bash
pandoc draft.md -o draft.docx
```

Note: This only handles format conversion — it does not replace your institution's template styling or final manual review.

## FAQ

### Why are the default outputs not Word files?

Writing collaboration needs text assets that are trackable, reusable, and version-controlled. Markdown is better suited for iterative work. Word is appropriate for final delivery, so it is handled as the last step.

### Can it generate the final submittable version for me?

It can produce content close to a final draft, but your institution's template, table of contents fields, page numbers, reference fields, and formatting details should still be finalized in Word.

### Will this Skill fabricate references?

No. The rules explicitly prohibit fabricating references or data. All citations must be traceable.

### Does it support project documents in addition to papers?

Yes. Since v3.2.0, the Skill fully supports engineering/software project documents including SRS, design documents (HLD/LLD), feasibility reports, project closure reports, progress reports, system architecture documents, and test reports. The brainstorming flow automatically routes to the appropriate questions and writing norms based on document type.

## Repository Structure

```text
research-writing-skill/
├── SKILL.md                    # Main entry (legacy platform compatible)
├── AGENTS.md                   # General agent configuration
├── GEMINI.md                   # Gemini CLI configuration
├── CHANGELOG.md                # Version history
├── .claude-plugin/             # Claude Code configuration
├── .cursor-plugin/             # Cursor configuration
├── .codex/                     # Codex configuration
├── .opencode/                  # OpenCode configuration
├── hooks/                      # Session start scripts
│   ├── session-start
│   ├── hooks.json
│   └── hooks-cursor.json
├── skills/                     # Skill modules directory
│   ├── using-research-writing/
│   ├── brainstorming-research/
│   ├── writing-chapters/       # Paper chapter writing
│   ├── writing-project/        # Project document writing
│   ├── latex-output/
│   ├── literature-review/
│   ├── figures-python/
│   ├── figures-diagram/
│   ├── peer-review/
│   ├── statistical-analysis/
│   ├── environment-setup/
│   ├── prompts-collection/
│   ├── writing-core/
│   ├── writing-humanities/
│   ├── writing-medical/
│   └── writing-law/
├── latex-templates/            # User LaTeX templates directory
├── modules/                    # Legacy modules (kept for compatibility)
├── templates/                  # Code templates
├── plan-template/              # Plan templates
└── scripts/                    # Utility scripts
```

## Version

- Version: 3.2.0
- Updated: 2026-04-10
- Maintenance goal: Stable workflow, traceable content, deliverable outputs, multi-platform support
