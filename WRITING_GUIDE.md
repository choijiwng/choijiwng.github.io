# Technical writing guide

Create new Markdown or MDX files in src/content/blog.

Frontmatter example:

    ---
    title: "WSL2 and Docker lab setup"
    description: "Assumptions, test environment, results and limitations"
    pubDate: "2026-11-22"
    draft: true
    ---

Set draft: false only after reviewing sources, code, claims, secrets,
privacy, license and the boundary between personal/team contributions.

Recommended article structure:
1. Problem and why it matters
2. Environment, assumptions and hypothesis
3. Experiments and independent evidence
4. Results, counterexamples and limitations
5. Next steps

Local checks: npm ci && npm run build
Merge approved changes to main to deploy automatically.
