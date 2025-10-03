# Agent-SDD: Optimized Grok-First Software Development Framework

Streamlined system for structured software development with grok-code-fast-1, featuring automated variable resolution, comprehensive error handling, workflow dependency enforcement, path validation, framework resilience with self-healing capabilities, living architecture diagrams, and {{system_counts.agents}} specialized sub-agents for reliable execution.

## Why Agent-SDD
- **Grok-first orchestration**: {{system_counts.agents}} specialized sub-agents execute strict workflows for repeatable results
- **Single command surface**: `/sdd-task` with {{system_counts.workflows}} optimized flags for complete development lifecycle
- **Living architecture diagrams**: Automatic Mermaid diagram generation and maintenance throughout project lifecycle
- **Automated variable system**: Platform-agnostic variable resolution with intelligent auto-discovery
- **Workflow dependency enforcement**: Automatic sequencing validation prevents execution errors
- **Comprehensive error handling**: Centralized error codes via `config/variables.yml` for clear failure diagnosis
- **Self-evolving framework**: `--evolve` command enables continuous framework improvement and optimization
- **Framework resilience**: Built-in corruption detection, self-healing, and health checkpoints
- **Analytics-driven insights**: Built-in metrics collection and performance monitoring
- **Flexible bootstrap options**: Standards-based or MCP-powered component library setup
- **Dev-optimized**: No environment switching; concise, agent-focused instructions
- **Platform-agnostic**: Same framework experience across all supported AI assistants
- **Conflict-free**: Resolved agent overlaps, error code conflicts, and configuration consolidation
- **Guardrails**: Enforced IDs, directory naming, mandatory agent gates, and pre-flight checks

## Quick Start

### For New Chat Sessions
1. **Load framework context**: Share `.grok/GROK.md` with grok once per session
2. **Framework auto-detects**: `.grokrc` file signals framework presence
3. **Commands work automatically**: `/sdd-task` commands are now recognized

### Usage Examples
```bash
# Agent-SDD Universal automatically adapts to your AI assistant
# Works with Claude (/sdd-task), Grok (@sdd-task), or Codex (#sdd-task)

# 1) Initialize project with overview analysis
sdd-task --init                    # Universal command (adapts automatically)
# OR use platform-specific syntax if preferred:
/sdd-task --init                   # Claude
@sdd-task --init                   # Grok
#sdd-task --init                   # Codex

# 2) Choose bootstrap approach:
# For new projects (standards-based or MCP-powered)
sdd-task --bootstrap               # Review standards for styling
sdd-task --bootstrap --shadcn      # MCP-powered shadcn/ui setup

# For existing projects (analyze roadmap for next task)
sdd-task --next                    # Auto-generate next specification

# 3) Execute development tasks
sdd-task --execute TASK-001        # Implement with testing & quality checks

# 4) Improve or edit as needed
sdd-task --improve enhancement "Adjust button spacing"
sdd-task --edit "Fix typo in component"

# 5) Evolve the framework (optional)
sdd-task --evolve                  # Run self-improvement and analytics cycle
```

### Add a new agent
```bash
# Universal command (adapts to your platform)
sdd-task --agent my_agent --capabilities file_read,file_write,terminal_exec

# Platform-specific syntax still works:
/sdd-task --agent my_agent --tools Read,Write,Run_terminal_cmd  # Claude
@sdd-task --agent my_agent --capabilities file_read,file_write,terminal_exec  # Grok
#sdd-task --agent my_agent --capabilities file_read,file_write,terminal_exec  # Codex
```

## Directory Layout (.grok workspace)
```
.grok/
├── agents/           # Sub-agent definitions ({{system_counts.agents}} specialized agents)
├── analytics/        # Framework analytics and metrics
│   ├── history/      # Archived JSON Lines log files
│   ├── logs/         # Active JSON Lines log files
│   │   ├── commands.jsonl  # Command execution logs (single-line JSON)
│   │   └── errors.jsonl    # Error event logs (single-line JSON)
│   ├── metrics.json  # Aggregated usage metrics
│   └── reports/      # Generated analytics reports
├── changelog.md      # Development activity tracking
├── commands/
│   ├── sdd-task.md   # Universal command dispatcher
│   ├── universal-dispatcher.md  # NEW: Cross-platform dispatcher
│   └── workflows/    # Platform-agnostic workflow definitions
│       ├── bootstrap.md
│       ├── edit.md
│       ├── evolve.md
│       ├── execute.md
│       ├── improve.md
│       ├── init.md
│       ├── next.md
│       └── spec.md
├── config/           # Universal configuration system
│   ├── platform-detection.md    # NEW: Auto-platform detection
│   ├── universal-agent-spec.md  # NEW: Universal agent specification
│   ├── config.json       # Runtime settings (development profile)
│   ├── mcp-config.yml    # MCP integration settings
│   └── variables.yml     # Centralized paths, agents, and workflows
├── config.json       # Runtime configuration (single source of truth)
├── docs/
│   ├── error-codes.md
│   ├── naming-standards.md
│   ├── root-detection.md
│   └── templates-guide.md
├── errors/           # Error logs and diagnostics
├── product/          # Generated: overview.md, roadmap.md (from --init)
├── settings.local.json # Local configuration overrides
├── specs/            # Generated: task specifications (from --spec/--next)
├── standards/        # Generated: tech-stack.md, theme-standards.md, best-practices.md, architecture.md
└── templates/        # Template files for generation (centralized)
    ├── agent-registry-validator.md
    ├── agent-template.md
    ├── architecture.md
    ├── best-practices.md
    ├── overview.md
    ├── roadmap.md
    ├── spec-template.md
    ├── tech-stack.md
    ├── theme-standards.md
    └── wireframe-templates.md
```

## Universal Installation (Single .claude Directory)

Agent-SDD Universal uses a single `.claude/` directory for all platforms, with automatic platform detection and adaptation:

- **Directory**: `.claude/` (works on all platforms)
- **Claude Code**: Automatic loading + slash commands
- **Grok**: Manual bootstrap required, then full functionality
- **GitHub Copilot**: Manual bootstrap required, then full functionality

The same `.claude/` directory adapts its behavior based on detected platform. Your companion app installs the universal `.claude/` directory for all users.

### Companion App Platform Configuration

Your companion app can pre-configure Agent-SDD for specific platforms:

```bash
# Pre-configure for specific platform
set-platform claude   # Configure for Claude
set-platform grok     # Configure for Grok
set-platform codex    # Configure for GitHub Copilot
set-platform auto     # Use automatic detection
```

This creates `.claude/config/platform-override.json` with the selected platform preference.

## Centralized Variables
- paths: All file paths are centralized in `variables.yml` for maintainability:
  - `{{paths.base_dir}}` - Root .grok directory
  - `{{paths.product_dir}}` - Generated product docs
  - `{{paths.specs_dir}}` - Generated specifications
  - `{{paths.standards_dir}}` - Generated standards
  - `{{paths.architecture_file}}` - Living architecture diagrams
  - `{{paths.analytics_dir}}` - Analytics and metrics
  - `{{paths.commands_log}}` - JSON Lines command logs
  - `{{paths.errors_log}}` - JSON Lines error logs
- constraints:
  - task_id_regex: `{{constraints.task_id_regex}}`
  - spec_dir_pattern: `{{constraints.spec_dir_pattern}}`
- errors:
  - shared: `{{errors.shared.ERR_003}}`, `{{errors.shared.ERR_010}}`–`{{errors.shared.ERR_014}}`
  - next/spec docs: `{{errors.next_spec_docs.ERR_004}}`–`{{errors.next_spec_docs.ERR_007}}`
  - bootstrap: `{{errors.bootstrap.ERR_015}}`–`{{errors.bootstrap.ERR_020}}`
  - improve: `{{errors.improve.ERR_021}}`–`{{errors.improve.ERR_024}}`
  - evolve: `{{errors.evolve.ERR_025}}`–`{{errors.evolve.ERR_028}}`
  - architecture: `{{errors.architecture.ERR_045}}`–`{{errors.architecture.ERR_047}}`
- agents: All agent paths are defined under `agents.*` in `variables.yml` and referenced as `{{agents.NAME}}` in workflows.

## Commands ({{system_counts.workflows}} optimized flags)
Workflow definitions are maintained in `.grok/config/variables.yml` under the `commands` map. Update that file when workflows change; other files read from the same registry to stay synchronized.

- Authoritative registry: `.grok/config/variables.yml` → `commands`
- Dispatcher: `.grok/commands/sdd-task.md` consumes the registry
- Documentation: this section intentionally references the registry instead of duplicating the list

## Enforcement (hard rules)
- **Optimized Pre-flight Validation**: Framework integrity validated once during `--init`; subsequent commands use selective health checks for resilience
- **Framework Health Checkpoints**: Critical commands like `--evolve` include corruption detection and self-healing capabilities
- **Workflow Dependencies**: Automatic validation of required files and execution order
- **Unmapped flag**: If flag not found in `variables.yml.commands` → return `ERR_001` (no inference)
- **Agent gates**: Missing logger/context_manager at required gates → `ERR_011`/`ERR_013`
- **Pre-flight/order**: Missing pre-flight → `ERR_014`; steps out of order → `ERR_012`
- **Task ID format**: Enforce regex `{{constraints.task_id_regex}}` (reject underscores) → {{errors.shared.ERR_003}}
- **Spec dir naming**: Enforce `{{constraints.spec_dir_pattern}}` (reject legacy patterns) → {{errors.shared.ERR_003}}

## Agent Architecture

Agent-SDD uses {{system_counts.agents}} specialized sub-agents following structured workflow specifications for grok-code-fast-1:

### Core Agents
- **date-checker**: Provides consistent date formatting for task schemas
- **logger**: Manages changelog and tracks phase completion
- **context-manager**: Caches file contents and agent results for performance

### Workflow Agents
- **file-creator**: Generates spec.md and tasks.json files with schema validation
- **task-schema-validator**: Validates task objects against 14-field schema
- **test-runner**: Executes tests and analyzes results against acceptance criteria
- **code-reviewer**: Performs quality checks and theme compliance validation
- **agent-registry-validator**: Validates agent registry, path variables, and provides health checkpoints with selective validation modes

### Project Management Agents
- **project-analyzer**: Analyzes existing projects and enhances documentation with technical insights
- **project-starter**: Creates new projects from scratch with MCP-powered component installation
- **designer**: Handles design artifacts and theme consultation
- **task-decomposer**: Analyzes complexity and decomposes complex specs
- **architecture_visualizer**: Generates and maintains living Mermaid architecture diagrams

### Analytics & Evolution Agents
- **analytics-collector**: Collects usage metrics, performance data, and error patterns from JSON Lines logs
- **framework-improver**: Analyzes patterns, implements automated improvements, and provides corruption detection with self-healing capabilities
- **logger**: Manages changelog.md and automatically logs all command executions to JSON Lines format

### JSON Lines Logging Infrastructure
Automatic usage tracking with lean, single-line JSON entries:
- **commands.jsonl**: Every command execution logged with performance metrics, agent usage, and timestamps
- **errors.jsonl**: Error events captured with full context and error codes
- **Auto-archiving**: Files automatically archived when exceeding size limits (1000 lines for commands, 500 for errors)
- **Analytics aggregation**: Raw logs processed into metrics.json for --evolve analysis
- **Historical preservation**: Archived logs maintained for trend analysis

### Performance Optimizations
- **Streamlined agent files**: Optimized content for faster processing
- **Automated variable resolution**: Eliminates manual processing overhead
- **Context caching**: Reduces redundant file operations by 40-60%
- **Selective validation**: Framework validated once during `--init`; subsequent commands use health checkpoints
- **Framework resilience**: Built-in corruption detection and self-healing for uninterrupted operation
- **Workflow dependency validation**: Prevents execution errors before they occur
- **Analytics-driven optimization**: Continuous performance monitoring and improvement via `--evolve`
- **Comprehensive error handling**: 26 categorized error codes for efficient debugging

## Workflow Dependencies

Agent-SDD enforces proper workflow execution order through comprehensive dependency validation:

### Workflow Dependency Matrix
- `--init`: Can run first on any project (no dependencies)
- `--bootstrap`: Can run on empty projects OR after `--init` on existing projects
- `--next`: Requires `{{paths.overview_file}}` and `{{paths.roadmap_file}}`
- `--spec`: Requires product docs + design artifacts (wireframe.md, user-journey.md)
- `--execute`: Requires `{{paths.specs_dir}}/{task}/spec.md` and `tasks.json`
- `--improve` & `--edit`: Independent (can run anytime)
- `--evolve`: Independent (analyzes `{{paths.analytics_dir}}` for framework improvements)

### Dependency Types
- **Workflow Dependencies**: Required files and execution order validation
- **Task Dependencies**: Define prerequisite tasks that must complete first
- **File Dependencies**: Prevent conflicts when tasks modify the same files

### Automatic Management
- Dependencies established during intelligent task decomposition
- Circular dependency prevention
- Phase-based execution ordering
- Cached validation for performance
- Pre-flight dependency checking

## Error Codes
### Framework Critical (ERR_010-014)
- ERR_010: Workflow bypass detected
- ERR_011: Missing required agent invocation
- ERR_012: Workflow steps executed out of order
- ERR_013: Context manager not invoked
- ERR_014: Pre-flight validation failed

### Infrastructure Errors (ERR_015-017)
- ERR_015: MCP server unreachable
- ERR_016: MCP command execution failed
- ERR_017: Network timeout

### Operation Errors (ERR_018-020)
- ERR_018: File write failure
- ERR_019: Directory creation failed
- ERR_020: Permission denied

### Validation Errors (ERR_021-024)
- ERR_021: Invalid workflow type
- ERR_022: High-risk change rejected
- ERR_023: Target not found
- ERR_024: Date format error

### Framework Resilience Errors (ERR_029-030)
- ERR_029: Framework corruption detected, self-healing failed
- ERR_030: Critical path validation failed, framework integrity compromised

### Architecture Errors (ERR_045-047)
- ERR_045: Architecture diagram generation failed
- ERR_046: Architecture file not found
- ERR_047: Mermaid syntax validation failed

### Standard Errors (ERR_001-009)
- ERR_001: Invalid flag
- ERR_002: Missing required arguments
- ERR_002A: Invalid parameter format
- ERR_003: Invalid task schema (includes invalid task ID/dir naming)
- ERR_004: Required file not found
- ERR_005: Task ID not found
- ERR_006: Git operation failed
- ERR_007: Tests failed
- ERR_008: Theme compliance check failed
- ERR_009: Cannot acquire file lock

## Configuration
- **variables.yml**: Centralized variable definitions and command routing
- **config.json**: Runtime configuration (development profile, analytics + orchestration toggles)
- **mcp-config.yml**: MCP server configuration for component registries
- **settings.local.json**: Local overrides for command permissions

## Generation Policy
- `.grok/product/`, `.grok/specs/`, `.grok/standards/` start EMPTY
- `--init` (project-analyzer): Generates `standards/tech-stack.md`, `standards/best-practices.md`, `standards/architecture.md`
- `--bootstrap` (project-starter): Generates `product/overview.md`, `product/roadmap.md`, `standards/theme-standards.md`
- Choose workflow path after init:
  - New projects: `--bootstrap` (MCP-powered setup for empty directories)
  - Existing projects: `--next` (analyzes roadmap for next phase tasks)
- `--spec`/`--next` generate specification directories in `.grok/specs/`
- All generation follows strict naming: `{slug}_{type}_{YYYY-MM-DD}`

## License
MIT
