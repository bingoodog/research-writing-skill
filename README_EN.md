# Research Writing Assistant

Upgrade "paper writing" from one-off chat sessions into a trackable, recoverable, and reusable engineering-style collaboration workflow.  
This Skill is designed for undergraduates, graduate students, and early-stage researchers with a clear goal: fewer detours, less rework, and more time spent on research that truly matters.

![Research Writing Assistant Workflow](assets/readme/workflow.png)

## What This Is

This is not a prompt pack that only polishes sentences. It is a complete research writing collaboration system.  
Before starting any task, it aligns goals and constraints, automatically manages the `plan/` project context, and routes to the appropriate module based on your discipline and task type.

If you are working on a thesis, a course project paper, or a submission draft, this Skill is more reliable than ordinary conversational writing tools — because it emphasizes process, documentation, and write-back, without depending on single-session memory.

## Core Capabilities

- **End-to-end collaboration**: From topic development, body writing, and figure generation to pre-submission self-review, executed with stage gates
- **De-AI writing**: Constrains mechanical transition words, hollow emphasis phrases, subjective expressions, and bullet-point dumping
- **Discipline-specific writing support**: Routed modules for engineering, social sciences, medicine, and law
- **Literature review support**: Integration of English-language search and Chinese literature organization
- **Environment automation**: Miniconda installation, virtual environment creation, plotting dependency setup, and troubleshooting
- **Recoverable plans**: `plan/` continuously records goals, deliverables, decisions, and next steps

## Supported Platforms

This Skill uses a directory-based design compatible with mainstream local skill-loading workflows. Currently supported platforms:

- Cursor
- Windsurf
- Antigravity
- Qoder
- CC
- OpenCode

## What You Get

By default, Skill outputs are project files — not finished Word documents.

| Output Type | Default Format | Notes |
|---|---|---|
| Written body | `.md` / plain text / `.tex` | Suitable for version control and further processing |
| Process records | `plan/*.md` | Contains goals, progress, stage gates, preferences, and decisions |
| Figure scripts | `.py` | Reproducible figure generation logic |
| Prompt assets | `.md` | Reusable templates for translation, polishing, and de-AI-ification |

## Important Boundaries (Read First)

1. The Skill does not automatically generate or write directly to `.docx` files by default.  
2. The Skill does not open Word and apply formatting on your behalf — you will need to copy manually or use a conversion tool.  
3. The Skill can generate plain-text paragraphs ready to paste into Word, but final styling (heading levels, headers/footers, table of contents, reference fields) must be handled in Word.  
4. References and data are never fabricated; all citations must be traceable. Please independently verify high-risk conclusions.

## Installation

Download the repository, extract it, and copy `research-writing-skill/` into your paper writing directory.

Recommended steps:

1. Download and extract this repository.
2. Copy the `research-writing-skill/` folder into your paper project directory.
3. Load the local Skill directory in your platform (or copy it to the platform's required skills directory).

## Real Usage Example (Input → Output)

![Real Usage Example: Input to Output](assets/readme/real-case-input-output.png)

## Standard Collaboration Workflow (Recommended)

1. Define the task goal, deliverables, and deadline for this session
2. Have the Skill create or read the `plan/` context
3. Have the Skill produce a reviewable Markdown draft first
4. Run the style check script to handle de-AI-ification and formatting issues
5. Verify terminology, data, and citations before finalizing
6. Manually migrate to Word and apply your institution's template

## Delivering Markdown to Word

### Option A: Manual Copy (Default Recommendation)

1. Ask the Skill to output a "plain-text paragraph version" of the body (avoiding Markdown markers)
2. Copy the body in your editor and paste it into Word
3. Apply your institution's template styles in Word (headings, body text, figure captions, table captions)
4. Manually check equations, references, figure/table numbers, and cross-references

### Option B: Pandoc Conversion (Optional)

If you have Pandoc installed locally, you can try:

```bash
pandoc draft.md -o draft.docx
```

Note: This only handles format conversion — it does not replace your institution's template styling or final manual review.

## Common Scripts

- Initialize plan directory  
  macOS/Linux: `bash research-writing-skill/scripts/init_plan.sh`  
  Windows PowerShell: `powershell -ExecutionPolicy Bypass -File research-writing-skill/scripts/init_plan.ps1`

- De-AI and style check  
  macOS/Linux: `bash research-writing-skill/scripts/style_check.sh <file.md>`  
  Windows PowerShell: `powershell -ExecutionPolicy Bypass -File research-writing-skill/scripts/style_check.ps1 -FilePath <file.md>`

## Module Map

| Scenario | Module |
|---|---|
| Full workflow progression and submission prep | `modules/workflow-lifecycle.md` |
| General academic writing | `modules/writing-core.md` |
| Humanities / social science writing | `modules/writing-humanities.md` |
| Medical / biology writing | `modules/writing-medical.md` |
| Law writing | `modules/writing-law.md` |
| Literature review | `modules/literature-review.md` |
| Translation / polishing / de-AI-ification | `modules/prompts-collection.md` |
| Pre-submission self-review | `modules/peer-review.md` |
| Statistical analysis | `modules/statistical-analysis.md` |
| Python figures | `modules/figures-python.md` |
| Flowcharts / architecture diagrams | `modules/figures-diagram.md` |
| Environment setup and troubleshooting | `modules/environment-setup.md` |
| LaTeX typesetting | `modules/latex-guide.md` |

## FAQ

### Why are the default outputs not Word files?

Research collaboration needs text assets that are trackable, reusable, and version-controlled. Markdown is better suited for iterative work. Word is appropriate for final delivery, so it is handled as the last step.

### Can it generate the final submittable version for me?

It can produce content close to a final draft, but your institution's template, table of contents fields, page numbers, reference fields, and formatting details should still be finalized in Word. Most md-to-docx and md-to-pdf converters on the market are unreliable — manual copy-paste is recommended. A practical trick: paste the paragraphs into a WeChat chat first, then copy from WeChat into Word to avoid carrying over Markdown formatting.

### Will this Skill fabricate references?

No. The rules explicitly prohibit fabricating references or data. All citations must be traceable.

## Repository Structure

```text
research-writing-skill/
├── SKILL.md
├── modules/
│   ├── module-guide.md
│   ├── workflow-lifecycle.md
│   ├── writing-core.md
│   ├── writing-humanities.md
│   ├── writing-medical.md
│   ├── writing-law.md
│   ├── literature-review.md
│   ├── prompts-collection.md
│   ├── peer-review.md
│   ├── statistical-analysis.md
│   ├── figures-python.md
│   ├── figures-diagram.md
│   ├── environment-setup.md
│   └── latex-guide.md
├── templates/
│   ├── figure-template.py
│   ├── color-palettes.md
│   └── paper-outline.md
├── plan-template/
│   ├── project-overview.md
│   ├── stage-gates.md
│   ├── outline.md
│   ├── progress.md
│   └── notes.md
└── scripts/
    ├── init_plan.sh
    ├── init_plan.ps1
    ├── style_check.sh
    └── style_check.ps1
```

## Images and Download Notes

- README display images are stored in `assets/readme/`.
- The repository includes `.gitattributes` marking `assets/readme/**` as `export-ignore` to reduce image size in source code archives.

## Before Publishing to GitHub

1. Replace the workflow diagram above with a PNG from your next iteration
2. Maintain consistent README image naming under `assets/readme/`
3. Add a LICENSE file (e.g., MIT)
4. Optionally create a `CHANGELOG.md` to track version history

## Version

- Version: 2.5.0
- Updated: 2026-03-04
- Maintenance goal: Stable workflow, traceable content, deliverable outputs
