---
agent: 'agent'
---
Generate a comprehensive review of a Pull Request (PR) for a GitHub issue entered as <issue> <pr> <repo> and save it to a local markdown file.

When I provide an issue number (e.g., "5189") and a PR number (e.g., "32") and its project anubis, you should:

1. Fetch the complete issue details using:
   - The `gh` CLI command: `gh issue view <issue> --repo quero-edu/jiractus --json number,title,body,author,state,createdAt,updatedAt,labels,comments`
2. Fetch the complete PR details using:
   - The `gh` CLI command: `gh pr view <pr> --repo quero-edu/<repo> --json number,title,body,author,state,createdAt,updatedAt,labels,comments,files`
3. Create the directory structure if it doesn't exist: `issues/<issue>/`
4. Generate a markdown file at: `issues/<issue>/<issue>-pr#<pr>-review.md`
5. Format the markdown file with:
   - PR title as the main heading
   - Metadata section (PR number, author, state, created date, labels)
   - PR body
   - Changed files summary
   - Review comments (inline and general)
   - Review summary and recommendations
   - Reference to the related issue (title, body, metadata)

The markdown file should be well-structured and include all relevant information from the PR and its review.

Conduct a comprehensive code review of the implementation specified. Follow these guidelines:


## Review Scope

Review the following:
- Implementation files in the specified directory or PR
- Associated test/spec files
- Related reference implementation (if provided)
- Original requirements/issue documentation

## Review Structure

Generate a detailed markdown review document that includes:

### 1. Executive Summary
- Brief overview of what was reviewed
- Overall assessment with status indicator (🔴 Critical Issues / 🟡 Needs Work / 🟢 Good / ✅ Excellent)
- Key findings (3-5 bullet points)
- Recommendation (merge/do not merge/needs work)

### 2. Strengths
List 3-5 positive aspects of the implementation:
- Good architectural decisions
- Clean code patterns
- Proper error handling
- Good test coverage
- Performance optimizations

### 3. Issues by Priority

For each issue found, provide:
- **Issue #N: [Title]**
- **Severity:** 🔴 CRITICAL / 🟡 HIGH / 🟡 MEDIUM / 🔵 LOW
- **Location:** File path and line numbers
- **Problem:** Detailed explanation with code snippet
- **Impact:** What happens if not fixed
- **Fix Required:** Concrete code example showing the fix

Group issues by priority:
- **🔴 Critical Issues** - Will cause runtime errors or data corruption
- **🟡 High Priority** - Missing features, reliability issues
- **🟡 Medium Priority** - Code quality, maintainability, flexibility
- **🔵 Low Priority** - Documentation, minor improvements, polish

### 4. Implementation Priority Matrix

Create a table with:
- Priority (P0, P1, P2, P3)
- Issue name
- Estimated effort (hours/days)
- Risk if ignored (🔴/🟡/🟢)

Calculate totals for each priority level.

### 5. Recommended Action Plan

Organize fixes into phases:

**Phase 1: Critical Fixes** (Must do before production)
- Goal
- Timeline
- Effort estimate
- List of tasks

**Phase 2: Important Improvements** (Should do)
- Goal
- Timeline
- Effort estimate
- List of tasks

**Phase 3: Enhancements** (Nice to have)
- Goal
- Timeline
- Effort estimate
- List of tasks

### 6. Testing Recommendations

Suggest additional tests needed:
- Unit tests with code examples
- Integration tests
- Edge cases to cover
- Performance tests

### 7. Documentation Checklist

Create a checklist for documentation needs:
- [ ] Class/module documentation
- [ ] Public method documentation
- [ ] Usage examples
- [ ] Environment variables
- [ ] API documentation
- [ ] Troubleshooting guide
- [ ] Error handling guide

### 8. Code Quality Metrics

Create a table comparing current vs target metrics:
- Test Coverage
- Code Complexity
- Documentation Coverage
- Error Handling
- Configuration Management

### 9. Questions for Team

List questions that need team/product decisions:
- Business requirements clarifications
- Technical architecture decisions
- Default values and configuration
- Feature scope questions

### 10. Definition of Done

Create checklist for when the implementation is truly complete:
- [ ] All P0 issues resolved
- [ ] All P1 issues resolved
- [ ] Tests pass with X% coverage
- [ ] No runtime errors
- [ ] Documentation complete
- [ ] Code review approved
- [ ] Integration tests pass
- [ ] Performance benchmarks met

### 11. Reference Materials

List all files and resources used in the review.

## Review Guidelines

**Be Thorough:**
- Check for runtime errors (missing methods, incorrect APIs)
- Verify logic correctness (math errors, off-by-one errors)
- Compare against reference implementations
- Check for missing features from requirements
- Validate data transformations
- Review error handling
- Check configuration management
- Review security concerns

**Be Specific:**
- Always include file paths and line numbers
- Show actual code snippets for problems
- Provide concrete fix examples
- Explain the "why" behind each issue
- Quantify impact when possible

**Be Practical:**
- Estimate effort for fixes
- Prioritize issues realistically
- Consider business context
- Balance perfection vs pragmatism
- Suggest phased approaches

**Be Constructive:**
- Start with strengths
- Explain issues clearly without blame
- Provide actionable fixes
- Focus on code, not coder
- Suggest improvements, not just criticisms

## Output

Create the review document at:
`issues/<issue>/<issue>-code-review.md`

Or if reviewing a PR:
`issues/<issue>/pr-<pr-number>-review.md`


## Notes

- Always compare implementation against requirements/specifications
- Use reference implementations when available for comparison
- Check both positive and negative aspects
- Focus on critical issues that would block production use
- Be clear about what needs immediate fixing vs nice-to-haves
- Provide effort estimates to help with planning
- Include code examples for all suggested fixes

