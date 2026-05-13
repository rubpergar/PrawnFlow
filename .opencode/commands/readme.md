---
description: Generate or overwrite the project README.md
---

Generate a complete README.md for this project.

Optional focus or tone for the README: `$ARGUMENTS`

Rules:
- Scan the full project structure to understand the project.
- Exclude the `agents/` directory and everything under it from the description.
- Detect the tech stack, project purpose, and main features from the existing code.
- Include standard sections: title, description, stack, installation, usage, directory structure (excluding `agents/`), contributing, license.
- If `$ARGUMENTS` is provided, use it as context to adjust the tone, focus, or sections of the README.
- If the project is still in its initial skeleton state with no product code, reflect that honestly.
- Overwrite the existing `README.md` with the new content.
- Do not include placeholder or example content that does not reflect the actual project state.

Flow:
1. Inspect the project structure, package files, source code, and config files.
2. Identify the tech stack, purpose, and main features.
3. Construct the README following the rules above.
4. Overwrite `README.md`.
5. Confirm the file was written.
