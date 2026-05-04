# Bilingual README Generator

## Core Goals
Draft or format a GitHub repository README.md into a highly compact, professional bilingual (English/Chinese) layout.

## Constraints & Guardrails
- **Headings**: Must be pure English only (e.g., `# Introduction`, `## Features`). No Chinese in headings.
- **Line Breaks**: NEVER use paragraph breaks (blank lines) or hard returns to separate the English source and the Chinese translation.
- **Connector**: Always connect the English text and its Chinese translation using a `<br/>` tag.
- **Weight**: The Chinese translation must be entirely bolded (`**中文**`), while the English text remains normal weight.
- **List Items**: In `ul` or `ol` lists, both languages MUST share the exact same bullet point. E.g., `- English item.<br/>**中文列表项。**` Do not split the Chinese text into a new bullet point.

## Step-by-Step Execution Phases
1. **Analyze Origin**: Read the target project to understand its purpose, setup steps, and features, or read the existing user-provided README draft.
2. **Translate**: Generate accurate, developer-friendly Chinese translations for all body paragraphs and list items.
3. **Format Headings**: Ensure all Markdown headings (`#`, `##`, etc.) contain only English text.
4. **Format Body & Lists**: Apply the `<English Text><br/>**<Chinese Text>**` pattern strictly. Ensure no blank lines exist separating the translated pairs.
5. **Review Output**: Verify that no accidental carriage returns broke the list structures, ensuring both languages reside within the same Markdown list node.