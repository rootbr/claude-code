# Update CLAUDE Context

Perform a comprehensive codebase analysis and context update:

1. **Codebase Scanning**:
   - Analyze all source files for current architecture
   - Extract actual dependencies and versions from package files
   - Map module relationships and data flow
   - Identify all external integrations

2. **Documentation Mining**:
   - WebFetch official docs for major dependencies
   - Search for migration guides if using older versions
   - Find security advisories for our dependencies
   - Research performance best practices

3. **Pattern Analysis**:
   - Document actual vs intended architecture
   - Identify where we deviate from framework conventions
   - Find repeated code patterns and abstractions
   - Analyze error handling and edge cases

4. **Technical Debt Assessment**:
   - Locate outdated code patterns
   - Find TODO/FIXME comments
   - Identify performance bottlenecks
   - Document security concerns

5. **Context Generation**:
   - Update CLAUDE.md with findings
   - Include working code examples
   - Add troubleshooting guides
   - Document team-specific conventions

Use WebFetch liberally to get accurate, up-to-date information about our tech stack.