# Changelog

All notable changes to the compounding-engineering plugin will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [2.8.1] - 2025-11-27

### Added

- **`/plan` command** - Added "Create Issue" option to post-generation menu. Detects project tracker (GitHub or Linear) from user's CLAUDE.md (`project_tracker: github` or `project_tracker: linear`) and creates issues using `gh issue create` or Linear CLI.

## [2.8.0] - 2025-11-27

### Added

- **`julik-frontend-races-reviewer` agent** - New review agent specializing in JavaScript and Stimulus code race conditions. Reviews frontend code with Julik's eye for timing issues, DOM event handling, promise management, setTimeout/setInterval cleanup, CSS animations, and concurrent operation tracking. Includes patterns for Hotwire/Turbo compatibility and state machine recommendations.

## [2.7.0] - 2025-11-27

### Changed

- **`/codify` → `/compound`** - Renamed the documentation command to better reflect the compounding engineering philosophy. Each documented solution compounds your team's knowledge. The old `/codify` command still works but shows a deprecation notice and calls `/compound`.
- **`codify-docs` → `compound-docs`** - Renamed the skill to match the new command name.

### Updated

- All documentation, philosophy sections, and references updated to use `/compound` and `compound-docs`

## [2.6.2] - 2025-11-27

### Improved

- **`/plan` command** - Added AskUserQuestion tool for post-generation options and year note (2025) for accurate date awareness.
- **Research agents** - Added year note (2025) to all 4 research agents (best-practices-researcher, framework-docs-researcher, git-history-analyzer, repo-research-analyst) for accurate date awareness when searching documentation.

## [2.6.1] - 2025-11-26

### Improved

- **`/plan` command** - Replaced vague "keep asking questions" ending with clear post-generation options menu. Users now see 4 explicit choices via AskUserQuestion: Start `/work`, Run `/plan_review`, Simplify, or Rework.

## [2.6.0] - 2024-11-26

### Removed

- **`feedback-codifier` agent** - Removed from workflow agents. Agent count reduced from 24 to 23.

## [2.5.0] - 2024-11-25

### Added

- **`/report-bug` command** - New slash command for reporting bugs in the compounding-engineering plugin. Provides a structured workflow that gathers bug information through guided questions, collects environment details automatically, and creates a GitHub issue in the EveryInc/every-marketplace repository. Designed to be user-friendly for anyone using the plugin.

## [2.4.1] - 2024-11-24

### Improved

- **design-iterator agent** - Added focused screenshot guidance: always capture only the target element/area instead of full page screenshots. Includes browser_resize recommendations, element-targeted screenshot workflow using browser_snapshot refs, and explicit instruction to never use fullPage mode. Also added step to load relevant design skills (e.g., Swiss design) before starting iterations.

## [2.4.0] - 2024-11-24

### Fixed

- **MCP Configuration** - Moved MCP servers back to `plugin.json` following working examples from anthropics/life-sciences plugins. Removed `.mcp.json` file as it's not the correct approach.
- **Context7 URL** - Updated to use HTTP type with correct endpoint URL.

## [2.3.0] - 2024-11-24

### Changed

- **MCP Configuration** - Moved MCP servers from inline `plugin.json` to separate `.mcp.json` file per Claude Code best practices for plugin MCP integration.

## [2.2.1] - 2024-11-24

### Fixed

- **Playwright MCP Server** - Added missing `"type": "stdio"` field required for MCP server configuration to load properly.

## [2.2.0] - 2024-11-24

### Added

- **Context7 MCP Server** - Bundled Context7 for instant framework documentation lookup. Provides up-to-date docs for Rails, React, Next.js, and 100+ other frameworks.

## [2.1.0] - 2024-11-24

### Added

- **Playwright MCP Server** - Bundled `@playwright/mcp` for browser automation across all projects using this plugin. Provides screenshot, navigation, click, fill, and evaluate tools.

### Changed

- Replaced all Puppeteer references with Playwright across agents and commands:
  - `bug-reproduction-validator` agent
  - `design-iterator` agent
  - `design-implementation-reviewer` agent
  - `figma-design-sync` agent
  - `generate_command` command

## [2.0.2] - 2024-11-24

### Changed

- `design-iterator` agent - Updated description to emphasize proactive usage when design work isn't coming together on first attempt. Added examples showing how to suggest 5x or 10x iterations when initial changes don't fully resolve design issues.

## [2.0.1] - 2024-11-24

### Added

- `CLAUDE.md` - Project instructions with versioning requirements and pre-commit checklist
- `docs/solutions/plugin-versioning-requirements.md` - Detailed workflow documentation for maintaining version, CHANGELOG, and README in sync

## [2.0.0] - 2024-11-24

Major reorganization consolidating agents, commands, and skills from multiple sources into a single, well-organized plugin.

### Added

**New Agents (7)**
- `design-iterator` - Iteratively refine UI components through systematic design iterations
- `design-implementation-reviewer` - Verify UI implementations match Figma design specifications
- `figma-design-sync` - Synchronize web implementations with Figma designs
- `bug-reproduction-validator` - Systematically reproduce and validate bug reports
- `spec-flow-analyzer` - Analyze user flows and identify gaps in specifications
- `lint` - Run linting and code quality checks on Ruby and ERB files
- `ankane-readme-writer` - Create READMEs following Ankane-style template for Ruby gems

**New Commands (9)**
- `/changelog` - Create engaging changelogs for recent merges
- `/plan_review` - Multi-agent plan review in parallel
- `/resolve_parallel` - Resolve TODO comments in parallel
- `/resolve_pr_parallel` - Resolve PR comments in parallel
- `/reproduce-bug` - Reproduce bugs using logs and console
- `/prime` - Prime/setup command
- `/create-agent-skill` - Create or edit Claude Code skills
- `/heal-skill` - Fix skill documentation issues
- `/codify` - Document solved problems for knowledge base

**New Skills (10)**
- `andrew-kane-gem-writer` - Write Ruby gems following Andrew Kane's patterns
- `codify-docs` - Capture solved problems as categorized documentation
- `create-agent-skills` - Expert guidance for creating Claude Code skills
- `dhh-ruby-style` - Write Ruby/Rails code in DHH's 37signals style
- `dspy-ruby` - Build type-safe LLM applications with DSPy.rb
- `every-style-editor` - Review copy for Every's style guide compliance
- `file-todos` - File-based todo tracking system
- `frontend-design` - Create production-grade frontend interfaces
- `git-worktree` - Manage Git worktrees for parallel development
- `skill-creator` - Guide for creating effective Claude Code skills

### Changed

**Agents Reorganized by Category**
- `review/` (10 agents) - Code quality, security, performance reviewers
- `research/` (4 agents) - Documentation, patterns, history analysis
- `design/` (3 agents) - UI/design review and iteration
- `workflow/` (6 agents) - PR resolution, bug validation, linting
- `docs/` (1 agent) - README generation

**Commands Restructured**
- Workflow commands moved to `commands/workflows/` subdirectory
- `/plan`, `/review`, `/work`, `/codify` accessible via short names (autocomplete) or full path

### Summary

| Component | v1.1.0 | v2.0.0 | Change |
|-----------|--------|--------|--------|
| Agents | 17 | 24 | +7 |
| Commands | 6 | 15 | +9 |
| Skills | 1 | 11 | +10 |

---

## [1.1.0] - 2024-11-22

### Added

**gemini-imagegen Skill**
- Text-to-image generation with Google's Gemini API
- Image editing and manipulation
- Multi-turn refinement via chat interface
- Multiple reference image composition (up to 14 images)
- Model support: `gemini-2.5-flash-image` and `gemini-3-pro-image-preview`
- Python scripts: `generate_image.py`, `edit_image.py`, `multi_turn_chat.py`, `compose_images.py`

### Fixed
- Corrected component counts in documentation (17 agents, not 15)

### Documentation
- Added comprehensive README with all components listed
- Added this changelog
- Added `requirements.txt` for Python dependencies

---

## [1.0.0] - 2024-10-09

Initial release of the compounding-engineering plugin.

### Added

**17 Specialized Agents**

*Code Review (5)*
- `kieran-rails-reviewer` - Rails code review with strict conventions
- `kieran-python-reviewer` - Python code review with quality standards
- `kieran-typescript-reviewer` - TypeScript code review
- `dhh-rails-reviewer` - Rails review from DHH's perspective
- `code-simplicity-reviewer` - Final pass for simplicity and minimalism

*Analysis & Architecture (4)*
- `architecture-strategist` - Architectural decisions and compliance
- `pattern-recognition-specialist` - Design pattern analysis
- `security-sentinel` - Security audits and vulnerability assessments
- `performance-oracle` - Performance analysis and optimization
- `data-integrity-guardian` - Database migrations and data integrity

*Research (4)*
- `framework-docs-researcher` - Framework documentation research
- `best-practices-researcher` - External best practices gathering
- `git-history-analyzer` - Git history and code evolution analysis
- `repo-research-analyst` - Repository structure and conventions

*Workflow (3)*
- `every-style-editor` - Every's style guide compliance
- `pr-comment-resolver` - PR comment resolution
- `feedback-codifier` - Feedback pattern codification

**6 Slash Commands**
- `/plan` - Create implementation plans
- `/review` - Comprehensive code reviews
- `/work` - Execute work items systematically
- `/triage` - Triage and prioritize issues
- `/resolve_todo_parallel` - Resolve TODOs in parallel
- `/generate_command` - Generate new slash commands

**Infrastructure**
- MIT license
- Plugin manifest (`plugin.json`)
- Pre-configured permissions for Rails development
