# CLAUDE.md

## Commit and Versioning Standards

Follow [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) and [Semantic Versioning 2.0.0](https://semver.org/) specifications and @COMMIT_AND_VERSION_GUIDE.md

## Project Overview

Legal AI is a full-stack application for AI-assisted rental contract generation using pure Java backend with hexagonal architecture and React TypeScript frontend. The system guides users through contract creation via intelligent conversational interface.

**Technology Stack:**
- Backend: Pure Java 21 (no frameworks in core)
- Frontend: React 18 + TypeScript (built separately)
- Database: PostgreSQL with SQL scripts
- AI: Ollama integration (mistral-nemo:12b)
- Build: Maven for backend, npm for frontend
- Deployment: nginx serves frontend, Docker for backend

## Architecture

### Backend - Pure Java with Hexagonal Architecture

- **Domain Layer**: Rich domain models with business logic, no public getters/setters
- **Application Layer**: Use cases with Command and Visitor patterns for all operations
- **Adapters Layer**: REST endpoints, database ports, and AI integration

#### Architecture Principles

**Pure Java Core**: No reflection or heavy frameworks in application core - uses classic design patterns instead
**Hexagonal Architecture**: Clear separation between domain, application, and adapter layers
**Pattern-Heavy**: Extensive use of Command, Visitor, Builder, Decorator patterns
**Memory Efficient**: Streams data directly to JSON without intermediate DTOs using Visitor pattern

#### Key Patterns Used:
- **Command Pattern**: All state changes through commands with decorators (Transactional, Authorization, Audit)
- **Visitor/Builder Pattern**: Data extraction without breaking encapsulation, streaming JSON directly to output
- **Ports & Adapters**: Clear separation between core business logic and external integrations
- **Principal Pattern**: All commands executed through Principal (invoker) with proper authorization

#### Core Components:
- `*Application`: Central application class that orchestrates use cases
- `Principal`: Command invoker that manages security and execution context
- Commands are executed via `principal.execute(command)` pattern

#### Key Architecture Components

##### Domain Layer (`/domain/`)
- Rich domain models with behavior, not anemic data holders
- Full encapsulation - no public getters/setters
- Visitor pattern for data extraction without breaking encapsulation
- Domain objects call builder methods which stream directly to JSON output

##### Application Layer (`/application/`)
- Use Cases: Each business scenario as separate class
- Command Pattern: All state changes through commands
- Principal: Command invoker managing authorization and transactions
- Decorators: Cross-cutting concerns (TransactionalCommandDecorator, AuthorizationCommandDecorator, etc.)

##### Adapter Layer
- **Incoming** (`/adapter/in/`): usual for HTTP handlers
- **Outgoing** (`/adapter/out/`): usual for Database implementations
- Port implementations passed to Application constructor

##### Data Flow Pattern
1. REST extracts data from input stream → calls Use Case
2. Use Case creates Command → passes to Principal
3. Principal wraps with decorators → executes on Domain
4. Response: Domain fills Visitor/Builder → streams JSON directly to output

##### Key Files:
- `src/main/resources/*.yml`: Database, server, auth, AI settings
- `docker-compose.yml`: Container orchestration
- `db/*.sql`: Database schema SQL script

### Frontend - React TypeScript with Modern Patterns

- **Hook-based architecture**: Custom hooks for auth, loading, forms, modals
- **Service layer**: Centralized API client with proper TypeScript typing
- **Component structure**: Reusable UI components with strict TypeScript interfaces
- **PDF generation**: Client-side contract generation using jsPDF and html2canvas
