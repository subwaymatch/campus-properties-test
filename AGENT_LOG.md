# Agent log

Add a dated entry each time you work with your AI coding agent, with the newest entry at the bottom. Each entry records what you asked the agent, what it produced, and what you checked or changed. Paste your key prompts in exactly as you typed them. Include at least one time the agent got something wrong, and how you caught it.

Copy this outline for each entry:

```markdown
## YYYY-MM-DD: What you worked on

- **Asked:** "Paste your prompt here."
- **Agent produced:** What it made or changed.
- **Checked or changed:** How you checked it, and what you fixed.
```

## 2026-10-29: Building the Campus Comps home-sales site

- **Asked:** "Can you create a simple website using the data that would be published as GitHub pages?"
- **Agent produced:** Replaced the placeholder with a responsive static dashboard that reads the CSV in the browser, computes sale counts and median prices, and provides searchable and sortable town comparisons. Added data-quality notes and documented the site and independent checks in the README.
- **Checked or changed:** Previewed the page with a local HTTP server; confirmed it loaded 35,442 sales and 18 towns, displayed the $410,000 overall median, and filtered the town table to Carrboro. Checked the overall count, town count, overall median and Gainesville median independently using the SQLite dataset and Python's standard library.
