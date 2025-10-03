# sdd-task --init

PURPOSE: Initialize SDD for a new or existing project; analyze state, generate overview, recommend tech stack, plan roadmap, and validate setup.

WORKFLOW_STEPS:

SEQUENCE_GUARDS:
- PRE_FLIGHT:
  - REQUIRE dispatcher pre-flight validations completed
  - IF not → RETURN {{errors.shared.ERR_014}}
- AGENT_GATES:
  - REQUIRE project_analyzer/context_manager invoked before recommendations
  - IF missing → RETURN {{errors.shared.ERR_013}}
- ORDER_ENFORCEMENT:
  - IF steps executed out of order → RETURN {{errors.shared.ERR_012}}

FRAMEWORK_VALIDATION:
- READ {{agents.agent_registry_validator}} for validation guidance
- EXECUTE framework validation using read_file, grep, and run_terminal_cmd tools
- IF any invalid → RETURN {{errors.shared.ERR_014}}
- LOG validation results using search_replace tool for framework health monitoring

1. PROJECT_STATE_ANALYSIS:
   - CHECK {{paths.product_dir}}/overview.md existence
   - DETECT project type: empty vs existing
   - FOR EMPTY PROJECTS:
     - READ {{agents.project_analyzer}} for project analysis guidance
     - EXECUTE project analysis using read_file and grep tools → overview_fields
     - IF analysis_fails → FALLBACK to {{templates.project.overview}} defaults
   - FOR EXISTING PROJECTS:
     - READ {{agents.project_analyzer}} for tech stack scanning guidance
     - EXECUTE tech stack analysis using read_file, grep, and glob_file_search tools → tech_stack, patterns
     - IF scan_fails → FALLBACK to manual_detection_mode
   - DETERMINE routing strategy
   - IF routing_fails → DEFAULT to empty_project_flow

2. OVERVIEW_GENERATION:
   - PARSE arguments: project_name (optional)
   - IF missing_arguments → READ {{agents.project_analyzer}} for interactive prompt guidance
   - EXECUTE interactive prompting using tool-based user interaction patterns
   - READ {{agents.file_creator}} for file creation guidance
   - EXECUTE file creation using search_replace tool with template="{{templates.project.overview}}"
   - POPULATE: mission, goals, target_users, success_criteria
   - IF generation_fails → RETURN {{errors.init.ERR_040}}
   - VALIDATE completeness → minimum_required_fields

3. TECH_STACK_ANALYSIS:
   - READ {{agents.project_analyzer}} for tech recommendations guidance
   - EXECUTE tech analysis using read_file and grep tools → framework_suggestions
   - IF analysis_fails → FALLBACK to {{framework.supported_types}} defaults
   - READ {{agents.file_creator}} for file creation guidance
   - EXECUTE file creation using search_replace tool with template="{{templates.project.tech_stack}}"
   - IF creation_fails → RETURN {{errors.init.ERR_041}}
   - DOCUMENT: frameworks, styling, testing, build_tools

4. ROADMAP_PLANNING:
   - READ {{agents.file_creator}} for roadmap creation guidance
   - EXECUTE file creation using search_replace tool with template="{{templates.project.roadmap}}"
   - ANALYZE project_complexity → phase_breakdown
   - IF complexity_analysis_fails → DEFAULT to 3_phase_structure
   - IF creation_fails → RETURN {{errors.init.ERR_042}}
   - VALIDATE: phases, milestones, dependencies

4.5. ARCHITECTURE_INITIALIZATION:
   - READ {{agents.architecture_visualizer}} for architecture guidance
   - EXECUTE architecture visualization using read_file and search_replace tools → initial_architecture
   - GENERATE Mermaid diagrams based on tech stack analysis
   - CREATE living architecture documentation
   - IF generation_fails → FALLBACK to basic_template
   - INTEGRATE component relationships from tech_stack analysis

5. USER_REVIEW:
   - PRESENT overview.md content
   - SHOW tech stack recommendations
   - DISPLAY roadmap
   - COLLECT approval for each section
   - ALLOW modifications

6. DIRECTORY_SETUP:
   - ENSURE {{paths.product_dir}} exists
   - ENSURE {{paths.standards_dir}} exists
   - IF directory_creation_fails → RETURN {{errors.bootstrap.ERR_019}}

7. FILE_CREATION_SEQUENCE:
   - CREATE overview.md (template={{templates.project.overview}}) → IF fails → RETRY with minimal_template
   - CREATE roadmap.md (template={{templates.project.roadmap}}) → IF fails → RETRY with basic_roadmap
   - CREATE tech-stack.md (template={{templates.project.tech_stack}}) → IF fails → RETRY with default_stack
   - CREATE best-practices.md (template={{templates.project.best_practices}}) → IF fails → RETRY with generic_practices
   - CREATE architecture.md (template={{templates.project.architecture}}) → IF fails → RETRY with basic_architecture
   - IF all_retries_fail → RETURN {{errors.init.ERR_043}}

8. FINAL_VALIDATION:
   - READ {{agents.logger}} for logging guidance
   - EXECUTE logging using search_replace tool with summary="init completed"
   - VERIFY minimum_files_created: [overview.md, roadmap.md]
   - IF critical_files_missing → RETURN {{errors.init.ERR_044}}
   - CONFIRM framework_ready_state

AGENT_SPEC_REFERENCES:
- {{agents.project_analyzer}} - reference for project analysis guidance and tool execution patterns
- {{agents.file_creator}} - reference for file creation guidance and search_replace tool usage
- {{agents.architecture_visualizer}} - reference for architecture visualization guidance and diagram generation
- FOR EMPTY PROJECTS: Use project_analyzer guidance to populate overview template before continuing

ERROR_HANDLING:
- ANALYSIS_FAILURE: {{errors.init.ERR_035}} → fallback_to_defaults
- MISSING_ARGUMENTS: {{errors.init.ERR_036}} → interactive_prompt_mode
- OVERVIEW_GENERATION_FAILED: {{errors.init.ERR_040}} → minimal_template_fallback
- TECH_STACK_CREATION_FAILED: {{errors.init.ERR_041}} → default_recommendations
- ROADMAP_CREATION_FAILED: {{errors.init.ERR_042}} → basic_3phase_template
- FILE_CREATION_FAILED: {{errors.init.ERR_043}} → retry_with_fallbacks
- CRITICAL_FILES_MISSING: {{errors.init.ERR_044}} → incomplete_init_warning
- DIRECTORY_CREATION_FAILED: {{errors.bootstrap.ERR_019}} → permission_check_required

FALLBACK_STRATEGIES:
- analysis_fails → use_framework_defaults
- file_creation_fails → retry_with_simpler_templates
- missing_arguments → trigger_interactive_prompts
- directory_fails → suggest_manual_creation
