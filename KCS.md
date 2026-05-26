# KaisarCode Standards (KCS)

The **KaisarCode Standards (KCS)** establish the foundational rules for formatting, code organization, documentation, and architecture across the entire KaisarCode ecosystem. By adhering to these strict conventions, the ecosystem guarantees consistency, maximum composability, and readability. 

These standards are natively enforced by the `kcs` validation tool.

---

## Structure & Style

- **Language:** All content (code, comments, docs) must be written in English.
- **Indentation:** Use 4-space indentation exclusively. Tabs are forbidden.
- **Alignment:** Do not use alignment-based formatting or artificial whitespace padding.
- **Blank Lines:** Do not leave consecutive blank lines.
- **File Endings:** All files must end with exactly one newline.
- **Naming:** Use clear, self-descriptive names to avoid the need for explanatory comments.
- **Paths:** Do not hardcode user-specific or absolute paths.
- **Cleanliness:** Remove all debug logs, markers, and temporary instrumentation before committing.
- **No Numbered Outputs:** Diagnostic messages, prints, or logs (via `echo`, `printf`, `log_` functions, etc.) must not be prefixed with step numbers (e.g., `1.`, `2)`).
- **No Ornamented Outputs:** Echos, prints, or logs must not contain visual decorations or symbolic elements (such as horizontal separator dashes `---`, equals lines `===`, arrow symbols `->` or `=>`, titles formatted like `=== TITLE ===`, or non-ASCII characters like emojis and special shapes).
- **No Em Dash:** The em dash character "—" is forbidden in all files. Use the standard hyphen "-" character instead.

## Code Organization

- **Functions:** Keep all executable logic encapsulated inside functions.
- **Shell Scripts:** The main body of a shell script should only delegate to functions (e.g., calling `main "$@"`).
- **Filenames:** Default source filenames to one lowercase word. If a filename contains multiple words, they must be separated with a hyphen (`-`) and only a hyphen—underscores (`_`) are strictly forbidden. The only exception to this rule is for files representing class names. Shell CLI binaries should use kebab-case.

## Comment & Doc Policy

- **No Internal Comments:** Inline, internal, and explanatory comments within the code are strictly forbidden. If code requires comments to be understood, it must be refactored to be self-evident.
- **No Ornamented Comments:** Comments and DocBlocks must not contain visual separator lines (e.g., repeating dashes `---` or asterisks `***`), decorative arrows, or emojis.
- **Mandatory DocBlocks:** Every function, method, and class must be preceded by a formal documentation block. Missing documentation blocks will trigger validation failures.
- **DocBlock Spacing:** Leave exactly one blank line before every DocBlock.
- **Line Length:** Lines inside a DocBlock must not exceed 80 characters.
- **Summary:** Every DocBlock must begin with a brief summary line describing the function's behavior, not just restating the identifier name.
- **Tags:** Every DocBlock must include a `@return` tag documenting the return value. Optional `@param` and other tags go between the summary and `@return`.
- **Syntax:** Documentation syntax is language-specific:
    - **C/C++ & PHP:** `/** ... */`
    - **Shell:** `# ` directly above the function
- **Role:** Documentation is structural metadata detailing inputs, outputs, and usage—not narrative explanation.

## C/C++ Rules

- **POSIX:** Place POSIX feature definitions before all includes.
- **Prefixes:** Use the `kc_` prefix for all exported/public identifiers.
- **Filenames:** Use lowercase filenames with hyphens only. Underscores are strictly forbidden, except for files representing class names.
- **Memory:** Keep memory management completely explicit and leak-free. Hidden ownership or implicit allocation behavior is forbidden.
- **Signatures:** Keep multiline function signatures left-aligned with zero continuation indentation. Misaligned multiline signatures are not allowed.

## Shell Rules

- **Shebangs:** Use exactly `#!/bin/sh` or `#!/bin/bash` as the shebang.
- **Validation:** Ensure the final script passes `shellcheck -x` with zero errors or warnings.
- **Restrictions:** `/** ... */` comments, inline explanatory comments, and executing complex logic in the main body outside of function delegation are strictly forbidden.

## Markdown Rules

- **Headers:** Use exactly one Level-1 (`# `) heading per file. Multiple H1 headings are forbidden.
- **No Numbered Headings:** Headings (from H1 to H6) must not start with step numbers (e.g., `## 1. Header`).
- **No Ornamented Headings:** Headings must not contain decorative separators, arrows, or emojis (e.g., `## === TITLE ===` or `## Intro -> Details`).
- **Links:** Wrap URLs and email addresses with standard Markdown link syntax.
