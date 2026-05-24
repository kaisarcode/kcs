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

## Build

`kcs` is written in Bash and requires no native compilation. It can be executed directly from the source directory or symlinked to your `PATH`.

### Requirements

- `shellcheck` must be installed on the host system to validate shell scripts.

---

## Beta Notice

This is a beta project realistically tested only on Debian x86_64. It was created out of a personal need for these tools, but no guarantees are provided regarding its stability or future support. You are free to test it, use it, and modify it as you please.

If you'd like to reach out, you can send an email to kaisar@kaisarcode.com. Please note that I do not accept pull requests; the goal is to avoid long-term dependency on platforms like GitHub, and I do not maintain fixed infrastructure to guarantee long-term stability for these projects.

---

## License

[![GPLv3](https://www.gnu.org/graphics/gplv3-127x51.png)](https://www.gnu.org/licenses/gpl-3.0.html)

This project is distributed under the **GNU General Public License version 3 (GPLv3)**.

---

## Repo

**GitHub:** [kaisarcode/kcs](https://github.com/kaisarcode/kcs)
