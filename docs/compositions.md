## Flint Cherts

Paste the "composition" for the dependency in the `dependencies` section of your `composition.json` file and run `flint sync`.

### Arena (lang: C)

An arena allocator written purely in C.

**Install with flint:**

```bash
flint add https://github.com/mainak55512/arena@v0.1.1
```

**Composition:**

```json
"arena": {
    "version": "v0.1.1",
    "include_paths": [
        "include"
    ],
    "src": [
        "lib"
    ],
    "remote": "https://github.com/mainak55512/arena"
}
```

### CString (lang: C)

A String library with basic string manipulation capabilities.
Uses arena allocator as dependency.

**Install with flint:**

```bash
flint add https://github.com/mainak55512/CString@v0.1.1
```

**Composition:**

```json
"CString": {
    "version": "v0.1.1",
    "include_paths": [
        "include"
    ],
    "src": [
        "lib"
    ],
    "remote": "https://github.com/mainak55512/CString"
}
```

### Container (lang: C)

A vector library written in pure C.

**Install with flint:**

```bash
flint add https://github.com/mainak55512/container@v0.1.1
```

**Composition:**

```json
"container": {
    "version": "v0.1.1",
    "include_paths": [
        "include"
    ],
    "src": [
        "lib"
    ],
    "remote": "https://github.com/mainak55512/container"
}
```

### Cmap (lang: C)

A hashmap library written in pure C.
Depends on arena allocator.

**Install with flint:**

```bash
flint add https://github.com/mainak55512/Cmap@v0.1.1
```

**Composition:**

```json
"Cmap": {
    "version": "v0.1.1",
    "include_paths": [
        "include"
    ],
    "src": [
        "lib"
    ],
    "remote": "https://github.com/mainak55512/Cmap"
}
```

### yyjson (lang: C)

A json library written in pure C.

**Composition:**

```json
"yyjson": {
    "version": "0.12.0",
    "include_paths": [
        "src"
    ],
    "src": [
        "src"
    ],
    "remote": "https://github.com/ibireme/yyjson"
}
```

### Crow (lang: C++)

A http server library for C++ projects.

**Composition:**

```json
"Crow": {
    "version": "1.1.1",
    "flags": [
        "-std=c++17",
        "-O3",
        "-DASIO_NO_DEPRECATED",
        "-DCROW_ENABLE_SSL",
        "-DCROW_ENABLE_COMPRESSION"
    ],
    "lib_links": [
        "-lpthread",
        "-lssl",
        "-lcrypto",
        "-lz"
    ],
    "include_paths": [
        "include"
    ],
    "src": [],
    "remote": "https://github.com/CrowCpp/Crow"
}    
```

### Raylib (lang: C)

A graphics simulation library.

NOTE: the `flags` may change on the basis of environment. Below composition is for
x11 systems.

**Composition:**

```json
"raylib": {
    "version": "unknown",
    "flags": [
        "-std=c99", "-D_GNU_SOURCE", "-DGL_SILENCE_DEPRECATION=199309L",
        "-DPLATFORM_DESKTOP_GLFW", "-DGRAPHICS_API_OPENGL_33",
        "-DSUPPORT_MODULE_RSHAPES=1", "-DSUPPORT_MODULE_RTEXTURES=1",
        "-DSUPPORT_MODULE_RTEXT=1", "-DSUPPORT_MODULE_RMODELS=1",
        "-DSUPPORT_MODULE_RAUDIO=1", "-D_GLFW_X11"
    ],
    "lib_links": [
        "-lGL", "-lX11", "-lXrandr", "-lXinerama", "-lXi",
        "-lXcursor", "-lm", "-lpthread", "-ldl", "-lrt"
    ],
    "include_paths": [
        "src",
        "src/platforms",
        "src/external/glfw/include"
    ],
    "src": [
        "src"
    ],
    "remote": "https://github.com/raysan5/raylib.git"
}
```

### lua (lang: C)

An embeddable scripting language. This is the library version of the scripting language.

NOTE: the `flags` may change on the basis of environment.

**Composition:**

```json
"lua": {
  "version": "v5.5.1",
  "remote": "https://github.com/lua/lua",
  "flags": [
    "-std=c99", "-O2", "-Wall", "-Wextra", "-Wfatal-errors", "-Wshadow",
    "-Wundef", "-Wwrite-strings", "-Wredundant-decls", "-Wdisabled-optimization",
    "-Wdouble-promotion", "-Wmissing-declarations", "-Wconversion", "-Wlogical-op",
    "-Wno-aggressive-loop-optimizations", "-Wdeclaration-after-statement",
    "-Wmissing-prototypes", "-Wnested-externs", "-Wstrict-prototypes",
    "-Wc++-compat", "-Wold-style-definition", "-DLUA_USE_LINUX",
    "-fno-stack-protector", "-fno-common", "-Wl,-E"
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

### boost/asio (lang: C++)

Boost.org asio module

**Composition:**

```json
"asio": {
  "version": "unknown",
  "remote": "https://github.com/boostorg/asio.git",
  "flags": [
    "-std=c++11"
  ],
  "lib_links": [
    "-lpthread"
  ],
  "include_paths": [
    "include"
  ],
  "src": []
}
```

### boost/math (lang: C++)

Boost.org math module

**Composition:**

```json
"math": {
  "version": "unknown",
  "remote": "https://github.com/boostorg/math.git",
  "flags": [
    "-std=c++14",
    "-DBOOST_MATH_STANDALONE=1"
  ],
  "include_paths": [
    "include"
  ],
  "src": []
}
```

### mINI (lang: C++)

INI file reader and writer

**Composition:**

```json
"mINI": {
    "version": "0.9.20",
    "remote": "https://github.com/metayeti/mINI.git",
    "flags": [
        "-std=c++17"
    ],
    "include_paths": [
      "src"
    ],
    "src": []
}
```
