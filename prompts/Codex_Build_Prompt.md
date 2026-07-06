# Codex Build Prompt

Use this prompt when asking Codex to build or improve the prototype.

```text
You are a senior frontend engineer.

Build a modern interactive Financial Health Dashboard based on the product documents in this repository.

Read these first:

- README.md
- docs/00_Product_Vision.md
- docs/01_Product_Principles.md
- docs/02_Information_Architecture.md
- docs/03_Feature_Roadmap.md
- docs/08_Design_System.md

Implementation requirements:

- Responsive layout
- Light and dark mode
- Dashboard-first structure
- Card-based UI
- Interactive charts
- Expandable sections
- Clean component structure
- Dummy data separated from UI logic
- No PDF-style page recreation
- No dense spreadsheet layout as default view

Core sections to build:

- Dashboard
- Financial Health Score
- Goals
- Net Worth
- Cash Flow
- Protection
- Risk View
- Recommendations
- AI Coach placeholder

Engineering requirements:

- Keep code readable
- Use reusable components
- Keep state simple
- Make dummy data easy to replace later
- Include clear file structure
- Add comments only where helpful
- Do not over-engineer V1

Quality bar:

The first demo must feel like a premium client product, not an internal worksheet.
```
