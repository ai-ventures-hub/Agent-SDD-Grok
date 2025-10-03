# Universal Framework: Single .claude Directory

Agent-SDD Universal uses one `.claude/` directory that automatically adapts to Claude, Grok, and GitHub Copilot through intelligent platform detection.

## Universal Directory Strategy

### Single .claude Directory for All Platforms
One directory serves all platforms through adaptive configuration:

- **`.claude/`** - Universal directory (automatic platform detection)
- **Claude Code** - Automatic loading + slash commands (native support)
- **Grok** - Manual bootstrap required, then full functionality
- **GitHub Copilot** - Manual bootstrap required, then full functionality

### Adaptive Internal Structure
The same directory structure works across all platforms:

```
.claude/
├── platforms/        # Platform adapters (auto-selected based on detection)
│   ├── claude/       # Claude Code configuration
│   ├── grok/         # Grok configuration
│   └── codex/        # GitHub Copilot configuration
├── agents/          # Universal agents (adapt to platform capabilities)
├── commands/        # Workflows and dispatchers (platform-aware)
├── config/          # Configuration (platform-specific loading)
├── templates/       # Generation templates (universal)
└── [all other files] # Identical across platforms
```

## Distribution Model

### Simplified GitHub Strategy
Single repository with universal directory:

```
Agent-SDD/
├── main (development)
└── .claude/         # Universal directory for all platforms
```

### Companion App Integration
Your companion app installs the same `.claude/` directory for all users:

1. **Single Download**: Always download `.claude/` directory
2. **Automatic Adaptation**: Framework detects platform and adapts automatically  
3. **Bootstrap Guidance**: Guide Grok/Codex users through initial setup

## Platform-Specific Behavior

### Claude Code (Automatic)
- Directory: `.claude/` (recognized automatically)
- Commands: `/sdd-task --init` (work immediately)
- Agent Execution: Native sub-agent orchestration
- Setup: Zero configuration required

### Grok (Bootstrap Required)
- Directory: `.claude/` (standard naming)
- Commands: `sdd-task --init` (after bootstrap)
- Agent Execution: Sequential simulation
- Setup: Manual framework knowledge loading

### GitHub Copilot (Bootstrap Required)
- Directory: `.claude/` (standard naming)  
- Commands: `sdd-task --init` (after bootstrap)
- Agent Execution: Sequential simulation
- Setup: Manual framework knowledge loading

## Benefits of Universal Approach

### For Users
- **Consistent Directory**: Always `.claude/` regardless of platform
- **Clear Expectations**: Same directory structure everywhere
- **Automatic Adaptation**: Framework handles platform differences
- **Future-Proof**: Easy to add new platforms without directory changes

### For Companion App
- **Simplified Distribution**: Single directory to install
- **No Platform Detection**: Framework handles platform adaptation
- **Unified Updates**: Same directory works across all platforms
- **Easier Maintenance**: One codebase, multiple platform behaviors

### For Framework Development
- **Unified Codebase**: Single implementation with platform adapters
- **Centralized Logic**: Core functionality in one place
- **Platform Extensions**: Easy to add platform-specific features
- **Testing Efficiency**: Test platform behaviors within single directory
