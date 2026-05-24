# kcs - KaisarCode Standards Validator

`kcs` is a command-line tool that validates KaisarCode files against formatting and standards rules. It checks for proper indentation, absence of trailing whitespaces, valid docblocks, shell-specific rules, markdown rules, and ensures there are no forbidden internal comments.

---

## CLI

### Examples

Validate a single shell script:

```bash
kcs ./script.sh
```

Validate a specific file type overriding automatic detection:

```bash
kcs -type shell ./script.txt
```

Validate the entire current directory recursively:

```bash
kcs .
```

Exclude a specific path pattern from validation:

```bash
kcs . -e vendor
```

---

### Parameters

| Command/Flag | Description |
| :--- | :--- |
| `<file\|dir>...` | Validate one or more files or directories |
| `-type <t>` | Force file type: `sh\|shell\|c\|cpp\|php\|md` |
| `-e`, `--exclude <p>` | Exclude path pattern |
| `-h`, `--help` | Show help and usage |

---

## Exclusion Rules (.kcsignore)

If a `.kcsignore` file exists in the directory where `kcs` is executed, it will automatically load and apply its exclusion patterns.

- Write one path pattern per line.
- Empty lines and lines starting with `#` (comments) are ignored.
- Patterns behave identically to the `-e` / `--exclude` command-line argument.

Example `.kcsignore`:

```text
# Exclude vendor dependencies
vendor/
node_modules/

# Exclude generated code
*.gen.c
```

---

## Build

`kcs` is written in Bash and requires no native compilation. It can be executed directly from the source directory or symlinked to your `PATH`.

### Requirements

- `shellcheck` must be installed on the host system to validate shell scripts.

---

## License

[![GPLv3](https://www.gnu.org/graphics/gplv3-127x51.png)](https://www.gnu.org/licenses/gpl-3.0.html)

This project is distributed under the **GNU General Public License version 3 (GPLv3)**.

---

## Repo

**GitHub:** [kaisarcode/kcs](https://github.com/kaisarcode/kcs)
