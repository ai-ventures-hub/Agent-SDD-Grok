# Platform Detection & Adaptation System

PLATFORM_DETECTION_WITH_OVERRIDE (Universal .claude Directory):

1. PLATFORM_OVERRIDE_CHECK:
   - CHECK .claude/config/platform-override.json
   - IF override exists → USE override platform (skip auto-detection)
   - IF override = "auto" → PROCEED to auto-detection

2. ENVIRONMENT_VARIABLE_CHECK (Auto-Detection):
   - IF {{CLAUDE_DIR}} exists → PLATFORM = claude
   - ELIF {{GROC_WORKSPACE}} exists → PLATFORM = grok
   - ELIF {{COPILOT_WORKSPACE}} exists → PLATFORM = codex
   - ELSE → FALLBACK_DETECTION

3. COMMAND_AVAILABILITY_CHECK (Fallback):
   - TEST /sdd-task command → CONFIRMS claude
   - TEST @sdd-task command → CONFIRMS grok
   - TEST #sdd-task command → CONFIRMS codex

4. CAPABILITY_ASSESSMENT:
   - DETECT available tools for selected platform
   - ASSESS command execution capabilities
   - IDENTIFY platform limitations

5. ADAPTER_LOADING (Single .claude Directory):
   - Directory name is ALWAYS .claude (for Claude compatibility)
   - LOAD platform-specific configuration from .claude/platforms/{platform}/
   - INITIALIZE tool mappings for selected platform
   - SET command prefixes and execution model
   - CONFIGURE environment variable mappings

PLATFORM_CAPABILITIES:
- CLAUDE: Full feature support, sub-agent orchestration, advanced tooling
- GROK: Standard tooling, adapted command syntax, grok-code-fast-1 optimizations
- CODEX: VS Code integration, GitHub Copilot features, workspace awareness

FALLBACK_STRATEGIES:
- IF platform undetected → DEFAULT to claude (backward compatibility)
- IF tools unavailable → GRACEFUL_DEGRADATION with reduced functionality
- IF commands fail → PROVIDE platform-specific setup instructions

ADAPTATION_RULES:
1. MAINTAIN backward compatibility with existing Claude workflows
2. TRANSPARENT platform switching (no user configuration required)
3. GRACEFUL feature degradation for limited platforms
4. PRESERVE all existing Agent-SDD functionality across platforms
