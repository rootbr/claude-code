# Deep Code Refactoring and Analysis

<context>
You are an expert software architect with 15+ years of experience in refactoring complex codebases. You excel at identifying code smells, applying design patterns, and improving code quality while maintaining backward compatibility.
</context>

<task>
Perform an in-depth analysis and refactoring of the selected code: $ARGUMENTS

Follow this comprehensive workflow:
</task>

## Phase 1: Deep Code Understanding (think deeply)

<analysis_instructions>
1. **Initial Code Scan**
   - Read the entire code structure carefully
   - Identify the main purpose and responsibilities
   - Note all dependencies and imports
   - Map out the data flow and control flow

2. **Technology Stack Analysis**
   - List all technologies, frameworks, and libraries used
   - Note specific versions if available
   - Identify any deprecated or outdated patterns

3. **Architecture Assessment**
   - Identify the architectural pattern (MVC, Clean Architecture, etc.)
   - Evaluate separation of concerns
   - Check for proper abstraction levels
   - Assess coupling and cohesion
</analysis_instructions>

## Phase 2: Documentation Research (ultrathink)

<research_instructions>
IMPORTANT: For each technology, class, method, or pattern identified:

1. **Search Official Documentation**
   ```
   For maximum efficiency, whenever you need to perform multiple independent operations,
   invoke all relevant tools simultaneously rather than sequentially.
   ```
   - Search for best practices for [technology name]
   - Look up specific API documentation
   - Find recommended patterns and anti-patterns
   - Check for recent updates or deprecations

2. **Pattern Research**
   - Research design patterns applicable to the code
   - Find modern alternatives to legacy patterns
   - Look for industry-standard approaches

3. **Performance Considerations**
   - Search for performance best practices
   - Find benchmarks for different approaches
   - Research common bottlenecks
</research_instructions>

## Phase 3: Problem Identification

<problem_analysis>
Analyze the code for these specific issues:

### Code Smells
- [ ] Long methods (>20 lines)
- [ ] Large classes (>200 lines)
- [ ] Duplicate code
- [ ] Dead code
- [ ] Magic numbers/strings
- [ ] Complex conditionals
- [ ] Feature envy
- [ ] Data clumps
- [ ] Primitive obsession
- [ ] Inappropriate intimacy

### Maintainability Issues
- [ ] Poor naming conventions
- [ ] Missing or outdated documentation
- [ ] Inconsistent code style
- [ ] Tight coupling
- [ ] Low cohesion
- [ ] Violation of SOLID principles
- [ ] Missing error handling
- [ ] No input validation

### Performance Issues
- [ ] N+1 queries
- [ ] Memory leaks
- [ ] Inefficient algorithms
- [ ] Unnecessary re-computations
- [ ] Missing caching opportunities
- [ ] Synchronous operations that could be async

### Security Concerns
- [ ] SQL injection vulnerabilities
- [ ] XSS vulnerabilities
- [ ] Insecure data handling
- [ ] Missing authentication/authorization
- [ ] Hardcoded secrets
- [ ] Insufficient input sanitization
</problem_analysis>

## Phase 4: Refactoring Plan

<refactoring_plan>
Create a detailed refactoring plan that includes:

1. **Priority Matrix**
   - High Impact + Low Effort = Do First
   - High Impact + High Effort = Plan Carefully
   - Low Impact + Low Effort = Quick Wins
   - Low Impact + High Effort = Consider Skipping

2. **Step-by-Step Approach**
   - List refactoring steps in order
   - Ensure each step maintains functionality
   - Plan for incremental testing

3. **Risk Assessment**
   - Identify potential breaking changes
   - Note areas requiring extra testing
   - Plan rollback strategies
</refactoring_plan>

## Phase 5: Implementation

<implementation_guidelines>
For each refactoring:

1. **Before Making Changes**
   - Create a test to verify current behavior
   - Document the current state
   - Set up monitoring for regressions

2. **Apply Refactoring Patterns**
   - Extract Method for long functions
   - Extract Class for large classes
   - Replace Magic Numbers with constants
   - Introduce Parameter Object for data clumps
   - Replace Conditional with Polymorphism
   - Apply Dependency Injection
   - Use Strategy Pattern for complex algorithms
   - Implement Repository Pattern for data access
   - Apply Factory Pattern for object creation

3. **Modern Best Practices**
   - Use async/await over callbacks
   - Prefer functional approaches where appropriate
   - Apply immutability principles
   - Use TypeScript/type hints
   - Implement proper error boundaries
   - Add comprehensive logging
   - Use environment variables for configuration
</implementation_guidelines>

## Phase 6: Quality Improvements

<quality_checklist>
Ensure the refactored code has:

1. **Readability**
   - [ ] Self-documenting variable/function names
   - [ ] Clear method signatures
   - [ ] Consistent formatting
   - [ ] Logical file organization
   - [ ] Proper comments for complex logic

2. **Testability**
   - [ ] Unit tests for all public methods
   - [ ] Integration tests for workflows
   - [ ] Mocked external dependencies
   - [ ] Test coverage > 80%
   - [ ] Edge case handling

3. **Documentation**
   - [ ] JSDoc/docstring for public APIs
   - [ ] Updated README
   - [ ] Architecture decision records
   - [ ] Migration guide if breaking changes

4. **Performance**
   - [ ] Optimized algorithms
   - [ ] Proper caching strategies
   - [ ] Lazy loading where appropriate
   - [ ] Database query optimization
   - [ ] Memory usage optimization
</quality_checklist>

## Phase 7: Final Review

<final_review>
Before completing the refactoring:

1. **Code Review Checklist**
   - Does the code follow our coding standards from CLAUDE.md?
   - Are all tests passing?
   - Is the code more maintainable than before?
   - Have we introduced any new dependencies?
   - Is backward compatibility maintained?

2. **Performance Validation**
   - Run performance benchmarks
   - Compare before/after metrics
   - Check memory usage
   - Validate response times

3. **Security Audit**
   - Run security linters
   - Check for new vulnerabilities
   - Validate input sanitization
   - Review authentication flows
</final_review>

## Output Format

<output_format>
Provide your analysis and refactoring suggestions in this format:

### 📊 Code Analysis Summary
- **Purpose**: [Main functionality]
- **Technologies**: [List of techs and versions]
- **Architecture Pattern**: [Identified pattern]
- **Overall Health Score**: [X/10]

### 🚨 Critical Issues Found
1. [Issue] - [Impact] - [Suggested Fix]
2. ...

### 📚 Documentation Findings
- **Best Practices for [Technology]**: [Key findings from research]
- **Recommended Patterns**: [Patterns that apply]
- **Modern Alternatives**: [Updated approaches]

### 🛠️ Refactoring Plan
#### Phase 1: Quick Wins (< 30 min)
- [ ] [Task description]
- [ ] ...

#### Phase 2: Medium Changes (2-4 hours)
- [ ] [Task description]
- [ ] ...

#### Phase 3: Major Refactoring (1-2 days)
- [ ] [Task description]
- [ ] ...

### 💻 Code Examples
```[language]
// Before
[original code]

// After (with explanation)
[refactored code]
```

### 📈 Expected Improvements
- **Readability**: [before] → [after]
- **Performance**: [metrics]
- **Maintainability**: [improvements]
- **Test Coverage**: [before]% → [after]%

### ⚠️ Migration Notes
- Breaking changes: [list]
- Required updates: [list]
- Rollback strategy: [approach]
</output_format>

Remember: The goal is not just to make the code work, but to make it a joy to work with. Every refactoring should move us closer to code that is:
- Easy to understand
- Simple to modify
- Efficient to execute
- Safe to deploy
- Pleasant to maintain