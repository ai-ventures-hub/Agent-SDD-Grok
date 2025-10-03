# sdd-task --evolve

PURPOSE: Evolve and optimize the Agent-SDD framework via analytics-driven improvements and validation.

WORKFLOW_STEPS:

SEQUENCE_GUARDS:
- PRE_FLIGHT:
  - REQUIRE dispatcher pre-flight validations completed
  - IF not → ATTEMPT framework_health_check
- FRAMEWORK_HEALTH_CHECK:
  - READ {{agents.agent_registry_validator}} for agent_registry_validator guidance
- EXECUTE agent_registry_validator using appropriate grok tools → health_status
  - IF health_check="ok" → CONTINUE with reduced_validation_mode
  - IF health_check="not_ok" → RETURN {{errors.shared.ERR_014}}
- ORDER_ENFORCEMENT:
  - IF steps executed out of order → RETURN {{errors.shared.ERR_012}}

DEPENDENCIES:
- Requires active .grok framework
- May reference {{paths.changelog_file}} and {{paths.analytics_dir}} data

REDUCED_VALIDATION_MODE:
- SKIP full registry validation when paths_ok
- TRUST framework integrity for analytics operations
- ENABLE self-healing capabilities during evolution
- LOG validation state for monitoring

1. COLLECT_METRICS: READ {{agents.analytics_collector}} for analytics_collector guidance
- EXECUTE analytics_collector using appropriate grok tools → usage_stats, perf_data, error_patterns
2. ANALYZE_PATTERNS: READ {{agents.framework_improver}} for framework_improver guidance
- EXECUTE framework_improver using appropriate grok tools → bottlenecks, opportunities
3. VALIDATE_FRAMEWORK: READ {{agents.framework_improver}} for framework_improver guidance
- EXECUTE framework_improver using appropriate grok tools → self_test_report
4. GENERATE_REPORTS: READ {{agents.analytics_collector}} for analytics_collector guidance
- EXECUTE analytics_collector using appropriate grok tools → health_report, recommendations
5. APPLY_OPTIMIZATIONS: READ {{agents.framework_improver}} for framework_improver guidance
- EXECUTE framework_improver using appropriate grok tools → changes_applied
6. EVOLVE_FEATURES: READ {{agents.framework_improver}} for framework_improver guidance
- EXECUTE framework_improver using appropriate grok tools → enhancements
7. VALIDATE_CHANGES: READ {{agents.code_reviewer}} for code_reviewer guidance
- EXECUTE code_reviewer using appropriate grok tools → review_ok
8. UPDATE_DOCUMENTATION: READ {{agents.file_creator}} for file_creator guidance
- EXECUTE file_creator using appropriate grok tools → version_bump, changelog_updates

WORKFLOW_SUCCESS_CRITERIA:
- Framework health score >= 90
- No critical issues introduced
- Performance improvements demonstrated
- Backward compatibility maintained
- Documentation updated and accurate

ERROR_HANDLING:
- {{errors.evolve.ERR_025}}: Framework health check failed
- {{errors.evolve.ERR_026}}: Optimization application failed
- {{errors.evolve.ERR_027}}: Validation tests failed
- {{errors.evolve.ERR_028}}: Documentation update failed
- {{errors.evolve.ERR_029}}: Framework corruption detected, self-healing failed
- {{errors.evolve.ERR_030}}: Critical path validation failed, framework integrity compromised

EXECUTION_FREQUENCY:
- Trigger conditions: Error rate spikes, performance degradation, user feedback
- Automated: Can be scheduled or triggered by analytics thresholds

IMPROVEMENT_PRIORITIES:
1. **Critical**: Security fixes, stability improvements, error rate reduction
2. **High**: Performance optimizations, usability enhancements
3. **Medium**: Feature additions, workflow streamlining
4. **Low**: Minor improvements, experimental features

ROLLBACK_MECHANISMS:
- Automatic backup of framework state before changes
- Incremental application with validation checkpoints
- Quick rollback capability for failed improvements
- Impact assessment before permanent deployment

MONITORING_POST_EVOLUTION:
- Track improvement effectiveness and user impact
- Monitor for unintended side effects or regressions
- Collect feedback on implemented changes
- Schedule follow-up evolution cycles based on results

FRAMEWORK_EVOLUTION_METRICS:
- Health score improvement percentage
- Error rate reduction metrics
- Performance improvement measurements
- User satisfaction indicators
- Adoption rate of new features

SUCCESS_OUTPUT:
- health_score: number
- improvements_applied: number
- performance_gain_pct: number
- error_reduction_pct: number
