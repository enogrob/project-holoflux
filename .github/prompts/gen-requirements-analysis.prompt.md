---
agent: 'agent'
---

# Generate Requirements Analysis for Story

## Usage
```
Use this prompt with: #file:gen-requirements-analysis.prompt.md <issue-number> <codebase>

Examples:
- #file:gen-requirements-analysis.prompt.md 4548 anubis
- #file:gen-requirements-analysis.prompt.md 4959 quero_bolsa
- #file:gen-requirements-analysis.prompt.md 4277 kroton-stock-integration
```

## Objective
Generate a comprehensive requirements analysis document for the story specified by `<issue-number>`, analyzing the `<codebase>` context. The output will be saved to `issues/<issue-number>/<issue>-requirements-analysis.md`.

**Input Parameters:**
- `<issue-number>`: The GitHub issue/story number (e.g., 4548, 4959)
- `<codebase>`: The target codebase name (e.g., anubis, quero_bolsa, kroton-stock-integration) 

## Context
Anubis is a microservice responsible for orchestrating the delivery of paying student data to higher education institution APIs (Kroton, Estácio, etc.). It manages enrollment flows from Quero Bolsa and new marketplaces, organizing payloads and logging structured events with retry mechanisms.

## Input Sources
The prompt will automatically reference these resources based on the `<issue-number>` and `<codebase>` parameters:

- **Story/Issue**: `issues/<issue-number>/<issue-number>.md`
- **Epic Documentation**: `inputs/epico.md` (High-level project epic and goals)
- **Codebase**: `inputs/repositories/<codebase>/` (Target codebase for analysis)
- **Existing Documentation**: `inputs/started-requirements.md` (Project-wide requirements)
- **Reference Architectures**:
  - Quero Bolsa: `inputs/repositories/quero_bolsa/`
  - Anubis: `inputs/repositories/anubis/`
  - Quero Deals: `inputs/repositories/quero-deals/` (Similar microservice pattern)
  - Estácio Integration: `inputs/repositories/estacio-lead-integration/`
  - Kroton Integration: `inputs/repositories/kroton-lead-integration/`

## Output
- **File Location**: `issues/<issue-number>/<issue>-requirements-analysis.md`
- **Format**: Markdown with Mermaid diagrams
- **Purpose**: Define WHAT needs to be built (business requirements, not implementation)

## Workflow
1. **Start here**: Use this prompt first for any new story/issue
2. Read the story from `issues/<issue-number>/<issue-number>.md`
3. Analyze the specified `<codebase>` and reference architectures
4. Generate comprehensive requirements analysis
5. **Next step**: Use `#file:gen-implementation-instructions.prompt.md` with the same issue number to generate implementation details

## Requirements Analysis Scope

The requirements analysis should focus on **WHAT** needs to be built, not **HOW** to build it. This document bridges business needs with technical specifications.

### Document Structure

Generate a comprehensive requirements analysis covering:

1. **Executive Summary**
   - Feature overview and business value proposition
   - Key stakeholders and their objectives
   - Success criteria and acceptance metrics
   - Timeline and priority classification (P0/P1/P2)

2. **Functional Requirements**
   - User stories with clear acceptance criteria
   - Use cases with happy path and edge cases
   - Business rules and validation logic
   - Workflow diagrams (Mermaid sequence/flowchart)

3. **Data Requirements**
   - New entities and attributes needed
   - Changes to existing data models
   - Data validation rules and constraints
   - Entity relationship diagrams (Mermaid erDiagram)
   - Data migration considerations

4. **API/Interface Requirements**
   - Endpoints specification (RESTful/GraphQL)
   - Request/response payload examples (JSON schemas)
   - Authentication and authorization requirements
   - Rate limiting and quota specifications
   - Webhook/callback requirements

5. **Integration Requirements**
   - External systems to integrate with
   - Event publishing/consuming specifications
   - Data synchronization needs
   - Integration flow diagrams (Mermaid)

6. **Non-Functional Requirements**
   - Performance benchmarks (response time, throughput)
   - Scalability expectations (concurrent users, data volume)
   - Availability and reliability targets (SLA)
   - Security requirements (encryption, access control)
   - Compliance and regulatory needs

7. **Dependencies and Constraints**
   - Technical dependencies (services, APIs, libraries)
   - Team dependencies (other squads, external partners)
   - Technical constraints (infrastructure, technology stack)
   - Timeline dependencies

8. **Risks and Assumptions**
   - Technical risks and mitigation strategies
   - Business assumptions to validate
   - Open questions requiring clarification

9. **Out of Scope**
   - Explicitly list features NOT included
   - Future enhancements for later phases

### Analysis Guidelines
- Use domain language understandable by non-technical stakeholders
- Avoid implementation details (specific classes, methods, libraries)
- Focus on business requirements and system behavior
- Provide concrete examples and scenarios
- Include visual diagrams for complex flows
- Trace requirements back to the original issue/epic
- Highlight ambiguities and ask clarifying questions if needed

**Visual Standards:**
Provide Diagrams following these visual standards:
- Use pastel and line color themes compatible with both dark and light browser themes
- Include relevant emojis for visual engagement and clarity
- Organize complex diagrams using subgraphs for better readability
- Size diagrams to fit A4 paper when printed (max width: 180mm)
- Use consistent color coding across all diagrams

**Mermaid Theme Configuration:**
Use this theme init block at the start of every Mermaid diagram:
```mermaid
%%{init: {
  'theme':'base',
  'themeVariables': {
    'primaryColor':'#E8F4FD',
    'primaryBorderColor':'#4A90E2',
    'primaryTextColor':'#2C3E50',
    'secondaryColor':'#F0F8E8',
    'tertiaryColor':'#FDF2E8',
    'quaternaryColor':'#F8E8F8',
    'lineColor':'#5D6D7E',
    'fontFamily':'Inter,Segoe UI,Arial'
  }
}}%%
```

