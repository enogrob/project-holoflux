---
agent: 'agent'
---

# Gen requirements analysis infra for the Story <issue> and its Codebase <codebase> entered as e.g. 4548 anubis

## Objective

Generate a requirements analysis infra for the new story entered e.g. <issue> generating this way a md file in #folder:issues/<issue>/<issue>-requirements-analysis-infra.md, show the requirements of the implementations to be made in the Infra Codebase to be configured or other appointed by the <issue>. 

## Context

Anubis is a microservice responsible for orchestrating the delivery of paying student data to higher education institution APIs (Kroton, Estácio, etc.). It manages enrollment flows from Quero Bolsa and new marketplaces, organizing payloads and logging structured events with retry mechanisms.

## Input Sources

- **Epic Documentation**: #file:inputs/epico.md (High-level project epic and goals)
- **Codebase**: #folder:src/<codebase> .
- **Anubis Existing Documentation**: #file:inputs/started-requirements.md
- **Features**: #folder:issues
- **Next Feature to be implemented**: #file:issues/<issue>/<issue>.md
- **SRE app-blueprint Documentation**: https://www.notion.so/quero/SRE-app-blueprint-9b793f60872c4406ae949a9a935b744a
- **app-blueprint Repo**: #folder:src/apps-blueprint
- **Infra Codebase to be Configured**: #folder:src/<codebase>/infra .
- **Reference Infra Repositories**:
  - Quero Deals: #folder:src/infra-quero-deals
  - Quero Bolsa: #folder:src/infra-querobolsa
- **Reference Repositories**:
  - Quero Deals: #folder:src/quero-deals
  - Quero Bolsa: #folder:src/quero_bolsa
  
## Requirements

- Analyse  all features described in the current feature file #folder:issues/<issue>/<issue>.md in order to foresee the required infra changes to be made in the Infra Codebase to be configured #folder:src/infra-<codebase> .
- Follow best practices for infra code quality, security, architecture and performance.
- Maintain a clean and organized infra codebase, adhering to standard conventions and patterns.
- If any clarifications or further information is needed, appoint it in each underlying step.
- Visual diagrams (Mermaid) for Infra structure and process flows
- Step-by-step breakdown for each implementation item (infrastructure as code, configurations, tests, documentation)

**Visual Standards:**

Provide Diagrams following these visual standards:

- Use pastel color themes compatible with both dark and light browser themes.
- Include relevant emojis for visual engagement and clarity.
- Organize complex diagrams using subgraphs for better readability.
- Size diagrams to fit A4 paper when printed (max width: 180mm).
- Use consistent color coding across all diagrams.

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

