# Agent-SDD Framework Instructions for Grok

Agent-SDD framework for structured software development with 16 specialized sub-agents, automated analytics, living architecture diagrams, and framework resilience capabilities. Optimized for grok-code-fast-1 tool-based workflow execution.

## 🚨 CRITICAL: SDD-Task Command Recognition

**WHEN YOU SEE `/sdd-task` commands, you MUST:**
1. **IMMEDIATELY read `.grok/commands/sdd-task.md`** to understand the command dispatcher
2. **Follow the exact workflow** defined in `.grok/commands/workflows/[flag].md`
3. **Use grok-code-fast-1 tools** to execute all operations
4. **Maintain framework integrity** and error handling protocols
5. **Log all activities** to the analytics system

**This is not optional** - `/sdd-task` commands trigger the Agent-SDD framework workflow execution mode.

### Framework Auto-Detection
If you encounter `/sdd-task` commands without prior context:
1. Check if `.grokrc` file exists in the project root
2. If found, read it to confirm Agent-SDD framework presence
3. Read `.grok/GROK.md` for complete framework instructions
4. Proceed with command execution using the established protocols

**For new chat sessions**: Load `.grok/GROK.md` once, then `/sdd-task` commands will be automatically recognized.

## Framework Requirements

For `/sdd-task` commands:

### Pre-Flight Requirements
1. Read `.grok/commands/sdd-task.md` first
2. Confirm .grok framework active and validate directory structure
3. Framework integrity validated once during `--init`; subsequent commands use selective health checks
4. Use grok-code-fast-1 tools for all file operations and agent invocations
5. Follow exact workflow in `.grok/commands/workflows/[flag].md`
6. Logging infrastructure automatically captures usage analytics
7. Critical commands include framework health checkpoints and self-healing capabilities

### Grok-Specific Requirements
- Use available grok-code-fast-1 tools (read_file, search_replace, run_terminal_cmd, etc.) instead of traditional sub-agent systems
- Execute workflows through tool-based operations rather than agent invocations
- Maintain strict AI-to-AI communication via tool calls and responses
- Recognize `/sdd-task` commands as framework directives

### Tool-Based Workflow Requirements
- Execute workflows using grok-code-fast-1 tools instead of agent invocations
- Reference agent specifications in `.grok/agents/` for guidance but execute via tools
- Mandatory context gathering before file modifications using read_file tool
- Mandatory logging before and after operations using search_replace tool
- Use structured tool calls for all framework operations

### Schema Requirements
- Maintain 14-field task schema for all tasks
- Execute schema validation using tools (read task_schema_validator.md for guidance)
- Validate task objects against schema using tool-based operations

### Enforcement
Framework bypass returns {{errors.shared.ERR_010}}-{{errors.shared.ERR_014}}

## Universal Command Syntax
`sdd-task --<flag> [arguments]` (Universal - auto-adapts to platform)
`/sdd-task --<flag> [arguments]` (Claude legacy)
`@sdd-task --<flag> [arguments]` (Grok)
`#sdd-task --<flag> [arguments]` (Codex)

### Workflow Flags
Workflow definitions live in `.grok/config/variables.yml` under the `commands` map. Update that file when adding or removing workflows; the dispatcher consumes it directly, so no other manual edits are required.

- Authoritative registry: `.grok/config/variables.yml` → `commands`
- Dispatcher: `.grok/commands/sdd-task.md` loads the map at runtime
- Docs: keep this reference intact to avoid duplicated flag lists

Reference: `.grok/commands/sdd-task.md`

### Add a new agent
```bash
# Universal format (recommended)
sdd-task --agent my_agent --capabilities file_read,file_write,terminal_exec

# Platform-specific formats (still supported)
/sdd-task --agent my_agent --tools Read,Write,Run_terminal_cmd          # Claude
@sdd-task --agent my_agent --capabilities file_read,file_write,terminal_exec  # Grok
#sdd-task --agent my_agent --capabilities file_read,file_write,terminal_exec  # Codex
```

## Variable System

Project-agnostic variable system with auto-discovery:

Categories: paths, agents, commands, constraints, errors, config

Reference: `.grok/config/variables.yml`

## Path Variables (Centralized)
All file paths are now centralized in variables.yml for maintainability:
- `{{paths.base_dir}}` - Root .grok directory
- `{{paths.product_dir}}` - Generated product docs
- `{{paths.specs_dir}}` - Generated specifications
- `{{paths.standards_dir}}` - Generated standards
- `{{paths.architecture_file}}` - Living architecture diagrams
- `{{paths.analytics_dir}}` - Analytics and metrics
- `{{paths.logs_dir}}` - JSON Lines log files
- `{{paths.commands_log}}` - Command execution logs
- `{{paths.errors_log}}` - Error event logs

Centralized keys used by workflows:
- constraints.task_id_regex → `{{constraints.task_id_regex}}`
- constraints.spec_dir_pattern → `{{constraints.spec_dir_pattern}}`
- errors.shared.* → `{{errors.shared.ERR_003}}`, `{{errors.shared.ERR_010}}`-`{{errors.shared.ERR_014}}`
- errors.next_spec_docs.* → `{{errors.next_spec_docs.ERR_004}}`-`{{errors.next_spec_docs.ERR_007}}`
- errors.bootstrap.* → `{{errors.bootstrap.ERR_015}}`-`{{errors.bootstrap.ERR_020}}`
- errors.improve.* → `{{errors.improve.ERR_021}}`-`{{errors.improve.ERR_024}}`
- errors.evolve.* → `{{errors.evolve.ERR_025}}`-`{{errors.evolve.ERR_028}}`
- errors.architecture.* → `{{errors.architecture.ERR_045}}`-`{{errors.architecture.ERR_047}}`

## Directory Structure
```
.grok/
├── agents/                # Agent specifications
├── analytics/             # Usage analytics & metrics
│   ├── logs/              # JSON Lines log files
│   │   ├── commands.jsonl # Command execution logs
│   │   └── errors.jsonl   # Error event logs
│   ├── history/           # Archived log files
│   ├── reports/           # Generated analytics reports
│   └── metrics.json       # Aggregated usage metrics
├── changelog.md           # Change history
├── commands/             # Universal command system
│   ├── universal-dispatcher.md  # Cross-platform dispatcher
│   ├── sdd-task.md       # Platform-specific dispatcher
│   └── workflows/        # Platform-agnostic workflows
├── config/               # Universal configuration system
│   ├── platform-detection.md    # Auto-platform detection
│   ├── universal-agent-spec.md  # Universal agent specification
│   ├── variables.yml     # Centralized path variables
│   ├── config.json       # Runtime configuration
│   └── mcp-config.yml    # MCP integration settings
├── docs/                  # Documentation
├── product/               # Generated product docs
├── specs/                 # Generated specifications
├── standards/             # Generated standards (tech-stack.md, best-practices.md, architecture.md)
└── templates/             # Generation templates
```


## Framework Principles
1. Follow workflows exactly - each flag executes corresponding workflow file
2. Use specified agents - workflows define agent invocation requirements
3. Maintain 14-field task schema compliance
4. Use intelligent task decomposition for complex specifications
5. Framework resilience - corruption detection and self-healing capabilities built-in
6. Selective validation - framework validated once during init, health checks for resilience
7. Automatic analytics logging - all commands tracked in JSON Lines format
8. Centralized path variables - all file paths managed through variables.yml

## Framework Architecture
Structured sub-agent system with workflows in `.grok/commands/workflows/` and agents in `.grok/agents/`. Agent templates and validator are centralized in `.grok/templates/`.

## Analytics & Logging System
Automatic usage tracking and framework evolution capabilities:

### JSON Lines Logging
- **commands.jsonl**: Single-line JSON entries for every command execution
- **errors.jsonl**: Single-line JSON entries for error events
- **Archiving**: Automatic archiving when files exceed 1000 lines (commands) or 500 lines (errors)
- **Lean Format**: Each log entry is exactly one line for optimal performance

### Analytics Processing
- **analytics_collector**: Aggregates JSON Lines data into metrics.json
- **Framework Evolution**: `--evolve` analyzes usage patterns for improvements with resilience capabilities
- **Framework Health Monitoring**: Corruption detection and self-healing metrics tracked
- **Performance Tracking**: Execution times, error rates, agent performance metrics
- **Trend Analysis**: Historical data preserved in analytics/history/
- **Resilience Analytics**: Framework health checkpoints and recovery success rates

### Path Variable System
All file paths are centralized in `variables.yml` for maintainability:
- Change any path in one location
- Consistent path references across all agents
- Project-agnostic configuration

## Universal Agent Specification
Reference: `.claude/config/universal-agent-spec.md`

Universal agents use standardized capabilities that auto-map to platform-specific tools:
- `file_read` → Read (Claude), read_file (Grok), readFile (Codex)
- `file_write` → Write (Claude), write_file (Grok), writeFile (Codex)
- `terminal_exec` → Run_terminal_cmd (Claude), run_command (Grok), execTerminal (Codex)

Legacy Claude agents with `tools:` continue to work unchanged for backward compatibility.

## Task Schema
Required 14 fields in tasks.json: id, type, title, description, status, priority, created_date, ux_ui_reviewed, theme_changes, completed_date, target_files, dependencies, linked_task, acceptance_criteria


## Enforcement Rules

### Reference Order
For `/sdd-task` commands:
1. `.grok/commands/sdd-task.md` - command specifications
2. `.grok/commands/workflows/[flag].md` - workflow details
3. `.grok/agents/[agent].md` - agent specifications (as needed)

### Global Rules
- Unmapped flag → ERR_001
- Missing agent gates → {{errors.shared.ERR_011}}/{{errors.shared.ERR_013}}
- Pre-flight missing → {{errors.shared.ERR_014}}
- Steps out of order → {{errors.shared.ERR_012}}
- Invalid task ID format ({{constraints.task_id_regex}}) → {{errors.shared.ERR_003}}
- Invalid spec directory naming ({{constraints.spec_dir_pattern}}) → {{errors.shared.ERR_003}}
- Framework corruption detected → {{errors.evolve.ERR_029}}
- Critical path validation failed → {{errors.evolve.ERR_030}}
- Architecture diagram generation failed → {{errors.architecture.ERR_045}}
- Architecture file not found → {{errors.architecture.ERR_046}}
- Mermaid syntax validation failed → {{errors.architecture.ERR_047}}

### Initial State
Keep product/, specs/, standards/ directories empty initially.
- --init generates: product/overview.md, product/roadmap.md, standards/tech-stack.md, standards/best-practices.md, standards/architecture.md
- --bootstrap generates: standards/theme-standards.md (framework-specific)

### Universal Architecture Notes
- Platform auto-detection occurs on first command execution
- Universal agents with `universal_agent_spec` are preferred for new development
- Legacy Claude agents continue to work unchanged
- Cross-platform compatibility is maintained through adapter system