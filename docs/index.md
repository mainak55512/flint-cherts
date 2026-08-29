# CLI Reference

## Installation

Flint is currently available only for Linux.

**Prerequisits:**
- GCC/Clang compiler chain
- GIT

Run the following command in terminal:

```bash
curl -fsSL -H "Accept: application/vnd.github.v3.raw" https://api.github.com/repos/mainak55512/flint/contents/build.sh | bash
```

`flint` is invoked as:

```
flint <command> [args]
```

Running `flint` with no command prints a short usage summary and exits with status `1`.

## Commands

### `init`

Initialize a new flint project in the current directory.

```
flint init
```

---

### `add <url>`

Add a remote library dependency by URL.

```
flint add <url>
```

**Arguments**

| Argument | Description |
|---|---|
| `url` | The URL of the library to add as a dependency |

---

### `add-lib [args...]`

Add one or more local libraries to the project.

```
flint add-lib [args...]
```

**Arguments**

| Argument | Description |
|---|---|
| `args...` | One or more local library paths/names to register |

---

### `add-flag [args...]`

Add one or more compiler/build flags to the project configuration.

```
flint add-flag [args...]
```

**Arguments**

| Argument | Description |
|---|---|
| `args...` | One or more flags to add to the build configuration |

---

### `build`

Build the project.

```
flint build
```

---

### `run`

Build (if needed) and run the project.

```
flint run
```

---

### `gen`

Generate a `compile_commands.json` file for the project, for use with editor/IDE tooling and language servers.

```
flint gen
```

---

### `sync`

Sync project dependencies (e.g. fetch/update declared libraries).

```
flint sync
```

---

## Exit Codes

| Code | Meaning |
|---|---|
| `0` | Command completed successfully |
| `1` | No command provided, or an unknown command was given |

## Quick Reference

| Command | Description |
|---|---|
| `init` | Initialize a new project |
| `add <url>` | Add a remote library dependency |
| `add-lib [args...]` | Add local library dependencies |
| `add-flag [args...]` | Add build flags |
| `build` | Build the project |
| `run` | Build and run the project |
| `gen` | Generate `compile_commands.json` |
| `sync` | Sync dependencies |

