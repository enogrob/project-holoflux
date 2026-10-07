---
agent: 'agent'
---
Fetch the content of a GitHub issue entered e.g. <issue> and save it to a local markdown file.

When I provide just an issue number (e.g., "5189"), you should:

1. Fetch the complete issue details using:
   - The `gh` CLI command: `gh issue view <issue> --repo quero-edu/jiractus --json number,title,body,author,state,createdAt,updatedAt,labels,comments`
2. Create the directory structure if it doesn't exist: `issues/<issue>/`
3. Generate a markdown file at: `issues/<issue>/<issue>.md`
4. Format the markdown file with:
   - Issue title as the main heading
   - Metadata section (issue number, author, state, created date, labels)
   - Issue body
   - Comments section (if any)

The markdown file should be well-structured and include all relevant information from the issue.

Example usage:
- User: "5189"
- Result: Creates `issues/5189/5189.md` with the full issue content from the current repository
