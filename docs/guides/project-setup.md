# Setting Up a Project

How to use the AIS framework on your project. The framework lives in
`ais-internal/AIS-spec` — client and project work goes in a **separate repo**
in the appropriate GitHub organization.

## Why a Separate Repo?

- Client work should never live in the AIS internal org
- Each project gets its own commit history, CI/CD, and access controls
- The framework repo stays clean — only framework improvements go here

## Quick Start

### 1. Create the Project Repo

Create a new repo in the client or project GitHub org. Initialize it with a
README and `.gitignore`.

### 2. Copy the Framework Files

From a clone of `ais-internal/AIS-spec`, copy these into your new project repo:

**Required — the framework engine:**

```
.specify/                  # Prompts, templates, scripts, playbooks
  VERSION                  # Copied framework version
  prompts/
  templates/
  scripts/
  playbooks/
  repo-instructions.md
PLANS.md                   # Rules for spec-level implementation plans
CONTRIBUTING.md            # Operating model and conventions
.gitignore                 # Includes .project-context/ exclusion
.markdownlint.jsonc        # Markdown lint rules
Skills/                    # Portable Agent Skills and supporting assets
```

**Required — pick your AI tool(s):**

| Tool | Files to copy |
|------|--------------|
| Claude Code | `.claude/commands/`, `CLAUDE.md` |
| GitHub Copilot | `.github/agents/`, `AGENTS.md` |
| Codex | `AGENTS.md`, `.agents/skills/` |
| Cursor | `.cursor/skills/` |

Copy only the tool(s) your team uses, or copy all four if the team is mixed.

**Optional — CI and PR template:**

```
.github/workflows/ci.yml
.github/pull_request_template.md
```

### 3. Don't Copy

- `docs/` — these are framework docs (demos, reference). Your project will
  generate its own docs.
- `specs/` — start empty. The workflow creates these.
- `README.md` — write a project-specific README.
- `.project-context/` — this is gitignored. Add project inputs locally.

### 4. Initialize the Project

```bash
mkdir -p .project-context specs
```

Drop your raw inputs (SOWs, RFPs, transcripts, requirements) into
`.project-context/`, then run the workflow:

```
/ais.setup.plan
/ais.setup.architecture
/ais.setup.constitution
```

### 5. Start Building

Pick the first unblocked spec from the project plan and run the spec lifecycle:

```
/ais.spec.specify
/ais.spec.design
/ais.spec.tasks
/ais.spec.implement
```

## Keeping the Framework Updated

When the framework gets improvements (new prompts, better templates, updated
scripts), pull them into your project:

1. Keep a local clone of `ais-internal/AIS-spec` up to date
2. Diff the framework files against your project
3. Copy updated files, being careful not to overwrite project-specific
   customizations (e.g., `constitution.md`, project-specific `.gitignore` rules)

Use the [upgrade guide](upgrade.md) when updating an existing project. It
compares the copied framework version against AIS Spec, summarizes the
changelog, identifies local drift, and separates safe updates from files that
need manual review.

The files most likely to change are in `.specify/prompts/`,
`.specify/templates/`, and `Skills/`. Command files (`.claude/commands/`,
`.github/agents/`, `.agents/skills/`, `.cursor/skills/`) are generated from
prompts. If you update prompts, copy or regenerate the command surfaces for the
AI tools your team uses (see
[multi-tool-commands.md](../reference/multi-tool-commands.md)).

## Project-Specific Customization

After copying, you'll typically customize:

- **`specs/constitution.md`** — created by `/ais.setup.constitution`,
  defines your project's standards
- **`.specify/playbooks/`** — add or select domain-specific playbooks
- **`CONTRIBUTING.md`** — adjust team roles, review requirements, and CI checks
- **`.github/workflows/`** — add project-specific build, test, and deploy pipelines

## Repo Structure After Setup

```
your-project-repo/
  .project-context/          # Raw inputs (gitignored)
  PLANS.md                   # Implementation-plan rules
  Skills/                    # Portable Agent Skills
  .specify/                  # Framework engine
    VERSION                  # Copied framework version
    prompts/                 # Command prompts
    templates/               # Output templates
    scripts/                 # Automation
    playbooks/               # Domain playbooks
  .claude/commands/          # Claude Code (if used)
  .agents/skills/            # Codex (if used)
  .github/
    agents/                  # Copilot (if used)
    workflows/               # CI/CD
  .cursor/skills/            # Cursor (if used)
  specs/
    constitution.md          # From /ais.setup.constitution
    .project-plan/           # From /ais.setup.plan
    .architecture/           # From /ais.setup.architecture
    YYMM-NNN-feature/        # From spec lifecycle
  source/                    # Application code
  tests/                     # Tests
  infra/                     # Infrastructure as code
  CONTRIBUTING.md
  README.md                  # Your project README
```
