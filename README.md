# Composition Specifications for `flint`

This repository hosts a curated collection of chert compositions (`composition.json`) for **flint**, the C/C++ build system and package manager.

A composition file acts as the blueprint for flint. It instructs the build system on where to fetch a dependency, which source files to include or ignore, where headers are located, and which compiler/linker options to pass during compilation.

---

## File Structure Overview

At the root level, a `composition.json` file contains a JSON object where each key represents the package name (e.g., `"lua"`).

```json
  "<package_name>": {
    "version": "...",
    "remote": "...",
    "flags": [...],
    "lib_links": [...],
    "excludes": [...],
    "include_paths": [...],
    "src": [...]
  }

```

---

## Field Specifications

### 1. `version` *(String)* — **Mandatory**

* **Description:** Specifies the exact release tag or version identifier in the remote target repository.
* **Format:** String matching the repository tag (e.g., `"v5.5.1"`, `"1.2.11"`). If no tags are available use "unknown".

### 2. `remote` *(String)* — **Mandatory**

* **Description:** The full URL of the Git repository to be cloned by flint.
* **Format:** Standard HTTPS or SSH Git repository URL (e.g., `"[https://github.com/lua/lua](https://github.com/lua/lua)"`).

### 3. `flags` *(Array of Strings)*

* **Description:** C/C++ compiler and preprocessor flags required to build the target correctly (e.g., optimization levels, warning toggles, platform macro definitions).
* **Format:** Array of command-line flag strings.
* **Example:** `["-std=c99", "-O2", "-DLUA_USE_LINUX", "-Wall"]`

### 4. `lib_links` *(Array of Strings)*

* **Description:** External dynamic or static system libraries that must be passed to the linker during the final link phase.
* **Format:** Array of linker flags (typically prefixed with `-l`).
* **Example:** `["-ldl", "-lm", "-lpthread"]`

### 5. `excludes` *(Array of Strings)*

* **Description:** Specific source files within the source directories (`src`) that should **not** be compiled into the library (such as executable entry points, test drivers, or unused platform implementations).
* **Format:** File paths relative to the root of the fetched repository.
* **Example:** `["lua.c", "luac.c"]`

### 6. `include_paths` *(Array of Strings)*

* **Description:** Directories containing header files (`.h`, `.hpp`) needed by the compiler (equivalent to `-I` paths).
* **Format:** Directory paths relative to the repository root. Use `""` to specify the repository root directory itself.
* **Important Note:** Path resolution is **non-recursive**. Every subdirectory containing header files must be explicitly listed in this array.

### 7. `src` *(Array of Strings)*

* **Description:** Directories containing C/C++ source files (`.c`, `.cpp`) to be compiled.
* **Format:** Directory paths relative to the repository root. Use `""` to specify the repository root directory itself.
* **Important Note:** Source discovery is **non-recursive**. Subdirectories holding C/C++ source files will be ignored unless explicitly declared in this array.

---

## Canonical Example: Lua 5.5.1

Here is a complete example defining a composition for the **Lua** C library:

```json
  "lua": {
    "version": "v5.5.1",
    "remote": "https://github.com/lua/lua",
    "flags": [
      "-std=c99",
      "-O2",
      "-Wall",
      "-Wextra",
      "-Wfatal-errors",
      "-Wshadow",
      "-Wundef",
      "-Wwrite-strings",
      "-Wredundant-decls",
      "-Wdisabled-optimization",
      "-Wdouble-promotion",
      "-Wmissing-declarations",
      "-Wconversion",
      "-Wlogical-op",
      "-Wno-aggressive-loop-optimizations",
      "-Wdeclaration-after-statement",
      "-Wmissing-prototypes",
      "-Wnested-externs",
      "-Wstrict-prototypes",
      "-Wc++-compat",
      "-Wold-style-definition",
      "-DLUA_USE_LINUX",
      "-fno-stack-protector",
      "-fno-common",
      "-Wl,-E"
    ],
    "lib_links": [
      "-ldl",
      "-lm"
    ],
    "excludes": [
      "lua.c",
      "onelua.c"
    ],
    "include_paths": [
      ""
    ],
    "src": [
      ""
    ]
  }

```

---

## How to Create a New Composition

1. **Identify Target Repository & Version Tag:** Prerequisite.
Locate the canonical upstream Git repository URL and identify the precise target version tag (e.g., `v1.2.0`). Ensure the tag exists on the remote host.


2. **Analyze Upstream Source Layout:** Directory Discovery.
Inspect the repository folder structure. Make a list of all directories containing source files (`.c`/`.cpp`) and header files (`.h`/`.hpp`). Remember that `flint` does not recursively scan subdirectories, so child folders must be explicitly enumerated.


3. **Filter Exclusions & Main Entry Points:**
Identify standalone executable source files (e.g., `main.c`, CLI runners, or tests) that should not be included when compiling as a reusable library component. Add these to the `excludes` array.


4. **Set Platform & Linker Options:**
Check the upstream build system (e.g., Makefile or CMakeLists.txt) to extract required preprocessor definitions (e.g., `-D_GNU_SOURCE`), compilation optimization flags, and mandatory system library links (e.g., `-lpthread`, `-lm`).


5. **Validate JSON Syntax:**
Ensure your generated block strictly adheres to valid JSON rules (e.g., no trailing commas, double-quoted keys and string values).


---

## Contributing Guidelines

When submitting a new library composition to this repository:

1. Create a pull request containing your addition in a dedicated folder or within the central registry index.
2. Verify that `version` matches an official tag on the upstream `remote`.
3. Test that `flint` builds the package cleanly without missing symbol warnings or missing include headers.
