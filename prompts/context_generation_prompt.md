# AI Context Generation Prompt

## 🎯 Primary Objective
Create a comprehensive CLAUDE.md context file by analyzing multiple information sources (Confluence docs, source code, documentation, etc.) to build an optimal AI assistant context for this codebase.

## 📊 Context Quality Standards

### Core Quality Principles
1. **No Duplication**: Each piece of information appears only once in its most appropriate section
   - Cross-reference related information instead of repeating
   - Use consistent terminology throughout the document
   - Link to primary definitions rather than re-explaining concepts

2. **Complete Coverage**: All technical details from source files are preserved
   - Verify every critical component is documented
   - Include edge cases and error scenarios
   - Document both happy path and failure modes
   - Preserve implementation-specific details that affect behavior

3. **Quick Lookup**: Clear table of contents and section headers enable fast navigation
   - Use hierarchical structure with predictable naming
   - Include search-friendly keywords in headers
   - Provide cross-references between related sections
   - Create index-style quick reference tables

4. **Concise Format**: Bullet points, tables, and code snippets for fast scanning
   - Prefer structured data over prose where possible
   - Use code blocks for examples and configurations
   - Implement progressive disclosure (summary → details)
   - Group related information in tables and lists

5. **Technical Accuracy**: All critical implementation details maintained with verification
   - Cross-reference documentation against actual code
   - Include version-specific information where relevant
   - Validate all code examples and configurations
   - Update context when implementation changes

### Context Optimization Targets

#### Fast Context Building
```
Goal: Enable quick understanding of system behavior and architecture
Techniques:
- Lead with system overview and key concepts
- Provide architectural diagrams and data flow
- Include performance characteristics and limitations
- Highlight critical dependencies and integration points
```

#### Quick Reference Usage
```
Goal: Immediate access to configuration and API usage patterns
Techniques:
- Comprehensive configuration tables with defaults and examples
- API endpoint reference with request/response formats
- Command cheat sheets for common operations
- Environment setup and deployment procedures
```

#### Problem Solving Support
```
Goal: Comprehensive troubleshooting with known solutions
Techniques:
- Common error patterns with specific solutions
- Debug command reference with expected outputs
- Performance troubleshooting with metrics
- Integration issue patterns and resolutions
```

#### Development Enablement
```
Goal: Complete code examples for common implementation patterns
Techniques:
- Working code snippets for typical use cases
- Test examples with setup and teardown
- Integration patterns with external services
- Extension points and customization examples
```

## 📋 Analysis Instructions

### Phase 1: Documentation Analysis
**ultrathink** about the project by examining all available documentation sources:

1. **Confluence/Wiki Analysis:**
   - Extract project overview, business requirements, and architectural decisions
   - Identify key stakeholders, user personas, and business processes
   - Document technical specifications, API designs, and system integrations
   - Note any architectural decision records (ADRs) or design patterns

2. **README & Project Documentation:**
   - Parse setup instructions, environment requirements, and deployment procedures
   - Extract feature descriptions, usage examples, and configuration details
   - Identify dependencies, build processes, and testing strategies

3. **API Documentation:**
   - Document all endpoints, request/response formats, and authentication methods
   - Note rate limits, error codes, and versioning strategies
   - Extract data models and validation rules

4. **Code Comments & JSDoc:**
   - Analyze inline documentation for business logic explanations
   - Extract method signatures, parameter descriptions, and return types
   - Document complex algorithms and domain-specific logic

### Phase 2: Source Code Architecture Analysis
**think deeper** about the codebase structure and implementation:

#### Core Architecture Assessment
```
Analyze and document:
1. **Layered Architecture**: Identify presentation, business, data, and infrastructure layers
2. **Module Organization**: How code is organized (feature-based, layer-based, domain-driven)
3. **Dependency Direction**: Flow of dependencies between modules
4. **Coupling Analysis**: Tight vs loose coupling between components
5. **Cohesion Assessment**: How well-focused each module is on its responsibility
```

#### Design Pattern Analysis
```
Identify and document patterns used:
- **Creational**: Factory, Builder, Singleton implementations
- **Structural**: Adapter, Decorator, Facade patterns
- **Behavioral**: Observer, Strategy, Command patterns
- **Architectural**: MVC, MVP, Repository, Service Layer
- **Anti-patterns**: God objects, Circular dependencies, Feature envy
```

#### Data Flow Architecture
```
Map data movement through the system:
1. **Request/Response Flow**: HTTP requests → Controllers → Services → Data layer
2. **State Management**: How application state is managed and synchronized
3. **Event Flow**: Event-driven architectures, message passing, callbacks
4. **Data Transformation**: Where and how data is transformed between layers
5. **Error Propagation**: How errors bubble up through the system
```

#### Performance Metrics & Benchmarks
```
Document actual system performance data:
1. **Load Test Results**: Real performance numbers with concurrent users, RPS, error rates
2. **Resource Usage**: Memory consumption, CPU utilization, disk I/O patterns
3. **Response Times**: 95th percentile, average, and worst-case scenarios
4. **Throughput Limits**: Maximum sustained load before degradation
5. **Scaling Characteristics**: How performance changes with load/data size
6. **Bottleneck Analysis**: Identified constraints and their impact
```

#### Critical Dependencies Assessment
```
Analyze dependency landscape:
- **Core Dependencies**: Framework dependencies that define architecture
- **Business Dependencies**: Libraries that implement business logic
- **Infrastructure Dependencies**: Database, caching, message queues
- **Development Dependencies**: Testing, building, linting tools
- **Circular Dependencies**: Identify and document circular references
- **Coupling Metrics**: Measure afferent/efferent coupling
```

### Phase 3: Quality & Pain Point Analysis
**think harder** about code quality and potential issues:

#### Code Quality Assessment
```
Evaluate codebase health:
1. **SOLID Principles Violations**:
   - Single Responsibility: Classes/functions doing too much
   - Open/Closed: Hard to extend without modification
   - Liskov Substitution: Inheritance hierarchy issues
   - Interface Segregation: Fat interfaces
   - Dependency Inversion: Concrete dependencies

2. **Code Smells Detection**:
   - Long methods/classes
   - Duplicate code
   - Large parameter lists
   - Feature envy
   - Data clumps
   - Primitive obsession

3. **Technical Debt Hotspots**:
   - Legacy code sections
   - Missing tests
   - Outdated dependencies
   - Performance bottlenecks
   - Security vulnerabilities
```

#### Scalability Analysis
```
Identify scaling bottlenecks:
1. **Performance Bottlenecks**:
   - Database query patterns
   - N+1 query problems
   - Memory leaks
   - CPU-intensive operations
   - Synchronous blocking operations

2. **Architectural Constraints**:
   - Monolithic vs microservice boundaries
   - Database scalability limits
   - Session management approaches
   - Caching strategies
   - Load balancing considerations

3. **Resource Limitations**:
   - Memory usage patterns
   - File I/O operations
   - Network communication patterns
   - External service dependencies
```

## 📊 Context Optimization Guidelines

### Information Prioritization
```
1. **High Priority** (Always include):
   - Core business logic and domain models
   - Authentication/authorization mechanisms
   - Database schema and relationships
   - API endpoints and data contracts
   - Critical dependencies and configurations

2. **Medium Priority** (Include if space allows):
   - Testing strategies and coverage
   - Deployment and infrastructure details
   - Performance optimization notes
   - Common debugging scenarios

3. **Low Priority** (Reference only):
   - Detailed implementation comments
   - Historical change logs
   - Extensive code examples
   - Non-critical utility functions
```

### Token Efficiency Strategies
```
1. **Concise Formatting**:
   - Use tables for structured data
   - Bullet points for lists
   - Code blocks for examples
   - Hierarchical headers for navigation

2. **Smart Summarization**:
   - Group related concepts
   - Use representative examples
   - Reference patterns instead of implementations
   - Link to external docs when detailed

3. **Quick Reference Sections**:
   - Environment variables table
   - Common commands list
   - Troubleshooting guide
   - Key file locations
```

## 🔍 Source Analysis Framework

### Code Analysis Commands
```bash
# Architecture discovery
find . -name "*.java" -o -name "*.ts" -o -name "*.js" | head -20
grep -r "class\|interface\|function" --include="*.java" --include="*.ts" | head -10

# Dependency analysis
find . -name "package.json" -o -name "pom.xml" -o -name "build.gradle"
grep -r "import\|require" --include="*.js" --include="*.ts" | head -10

# Configuration discovery
find . -name "*.yml" -o -name "*.yaml" -o -name "*.properties" -o -name ".env*"

# Database schema analysis
find . -name "*.sql" -o -name "*migration*" -o -name "*schema*"

# API endpoint discovery
grep -r "@RestController\|@RequestMapping\|@GetMapping\|@PostMapping" --include="*.java"
grep -r "app\.(get\|post\|put\|delete)" --include="*.js" --include="*.ts"
```

### Documentation Mining Patterns
```regex
# Business logic comments
/\* Business Rule:.*?\*/
// TODO:.*
// FIXME:.*
// NOTE:.*

# Configuration patterns
@ConfigurationProperties
@Value\(".*"\)
process\.env\..*
config\..*

# Security patterns
@Secured
@PreAuthorize
@RolesAllowed
authentication
authorization
```

## 📝 Optimal Context Structure Principles

### Structure Highlights Framework
Design your CLAUDE.md with these structural elements:

1. **Comprehensive Section Coverage**: 10-15 main sections covering everything from system overview to operational procedures
   - System Overview & Business Context
   - Technical Architecture & Design Patterns  
   - Data Models & API Specifications
   - Performance Metrics & Benchmarks
   - Configuration & Environment Setup
   - Development & Testing Guidelines
   - Known Issues & Technical Debt
   - Debugging & Troubleshooting Procedures
   - Deployment & Operations Guide
   - Team Resources & Documentation Links

2. **Performance Data Integration**: Include actual test results and metrics
   - Real load test numbers (concurrent users, RPS, response times)
   - Resource usage patterns (memory, CPU, I/O)
   - Bottleneck identification with specific measurements
   - Scaling characteristics with concrete data points

3. **Configuration Reference Organization**: System properties and settings organized by category
   - Environment variables grouped by purpose
   - Feature flags with their business impact
   - External service configurations
   - Security and compliance settings

4. **Practical Code Examples**: Working examples for common use cases
   - API usage patterns with request/response examples
   - Integration patterns with external services
   - Error handling and retry logic examples
   - Testing patterns and mock setups

5. **Architecture Deep Dive**: Technical implementation details
   - Thread models and concurrency patterns
   - Data flow diagrams and processing pipelines
   - Memory layout and optimization strategies
   - Integration points and service boundaries

6. **Operational Procedures**: Practical guides for day-to-day operations
   - Development environment setup
   - Deployment procedures and rollback plans
   - Monitoring and alerting configurations
   - Incident response and troubleshooting workflows

### Information Organization Strategy
```
Primary Navigation: Clear hierarchical headers with consistent naming
Quick Reference: Tables and summaries for immediate lookup
Progressive Disclosure: Summary → Details → Implementation specifics
Cross-Referencing: Links between related concepts and dependencies
Search Optimization: Keywords and terms that AI can easily match
```

## 📝 Output Structure Template

### Section Priority & Token Allocation
```
1. Project Overview (8%): Business context, tech stack, scale
2. Architecture Overview (18%): Core patterns, layers, design decisions
3. Data Flow & APIs (14%): Request flow, state management, key endpoints
4. Database Design (10%): Schema, relationships, constraints
5. Performance Metrics (8%): Actual benchmarks, load test results, bottlenecks
6. Configuration (10%): Environment, feature flags, dependencies
7. Development Guidelines (8%): Code standards, testing, git workflow
8. Pain Points & Debt (8%): Known issues, bottlenecks, improvements
9. Performance & Scale (6%): Current limits, scaling bottlenecks
10. Debugging Guide (6%): Common issues, troubleshooting steps
11. Documentation Resources (2%): Links to external docs, team contacts
12. Recent Changes (2%): Version history, migration notes
```

### Quality Assurance Checklist
```
Before finalizing CLAUDE.md verify against quality standards:
□ No Duplication: Each piece of information appears only once
□ Complete Coverage: All critical technical details preserved
□ Quick Lookup: Clear navigation and section headers
□ Concise Format: Structured data for fast scanning
□ Technical Accuracy: All details verified against source code

Content completeness:
□ All critical business logic is documented
□ Key APIs and endpoints are listed with examples
□ Database schema relationships are clear
□ Performance metrics with actual test results included
□ Environment setup is complete and verified
□ Common debugging scenarios are covered with solutions
□ Performance bottlenecks are identified with metrics
□ Security considerations are noted with specific measures
□ Team contacts and resources are current
□ Information is accurate and up-to-date
□ Context optimized for all four usage targets (building, reference, problem-solving, development)
```

## 🚀 Execution Instructions

### Step-by-Step Process
1. **Gather All Sources**: Collect Confluence docs, README files, API docs, and source code
2. **Initial Analysis**: Run documentation analysis phase completely
3. **Code Deep Dive**: Perform comprehensive source code analysis
4. **Pattern Recognition**: Identify architectural patterns and anti-patterns
5. **Quality Assessment**: Evaluate code quality and technical debt
6. **Context Compilation**: Build CLAUDE.md following the template structure
7. **Optimization Pass**: Ensure token efficiency while maintaining completeness
8. **Validation**: Verify all critical information is captured and accurate

### Success Criteria
- **Completeness**: All essential project information captured
- **Accuracy**: Technical details verified against source code
- **Usability**: Information structured for AI assistant efficiency
- **Maintainability**: Easy to update as project evolves
- **Token Efficiency**: Maximum information density within context limits

---

*Use this prompt to systematically analyze any codebase and create an optimal AI context that enables effective collaboration between developers and AI assistants.*