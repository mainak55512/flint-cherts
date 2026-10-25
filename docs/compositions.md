## Flint Cherts

Paste the "composition" for the dependency in the `sync` section of your `composition.json` file and run `flint sync`.

### Arena (lang: C)

An arena allocator written purely in C.

**Install with flint:**

```bash
flint add https://github.com/mainak55512/arena@v0.1.1
```

Or, 

```bash
flint add cherts:arena
```

**Composition:**

```json
"arena": {
    "version": "v0.1.1",
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

Or,

```bash
flint add cherts:CString
```

**Composition:**

```json
"CString": {
    "version": "v0.1.1",
    "remote": "https://github.com/mainak55512/CString"
}
```

### Container (lang: C)

A vector library written in pure C.

**Install with flint:**

```bash
flint add https://github.com/mainak55512/container@v0.1.2
```

Or,

```bash
flint add cherts:container
```

**Composition:**

```json
"container": {
    "version": "v0.1.2",
    "remote": "https://github.com/mainak55512/container"
}
```

### Cmap (lang: C)

A hashmap library written in pure C.
Depends on arena allocator.

**Install with flint:**

```bash
flint add https://github.com/mainak55512/Cmap@v0.1.2
```

Or,

```bash
flint add cherts:Cmap
```

**Composition:**

```json
"Cmap": {
    "version": "v0.1.2",
    "remote": "https://github.com/mainak55512/Cmap"
}
```

### yyjson (lang: C)

A json library written in pure C.

**Install with flint:**

```bash
flint add cherts:yyjson
```

**Composition:**

```json
"yyjson": {
    "version": "0.12.0",
    "exclude_dirs": ["fuzz", "misc", "test"],
    "remote": "https://github.com/ibireme/yyjson"
}        
```

### Crow (lang: C++)

A http server library for C++ projects.

**Install with flint:**

```bash
flint add cherts:crow
```

**Composition:**

```json
"Crow": {
    "version": "unknown",
    "flags": [
        "-std=c++17", "-O3", "-DASIO_NO_DEPRECATED",
        "-DCROW_ENABLE_SSL", "-DCROW_ENABLE_COMPRESSION"
    ],
    "lib_links": [
        "-lpthread", "-lssl", "-lcrypto", "-lz"
    ],
    "exclude_dirs": ["cmake", "docs", "examples", "scripts", "tests"],
    "remote": "https://github.com/CrowCpp/Crow"
}
```

### Raylib (lang: C)

A graphics simulation library.

NOTE: the `flags` may change on the basis of environment. Below composition is for
x11 systems.

**Install with flint:**

```bash
flint add cherts:raylib
```

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

    "excludes": [
        "src/rcore_desktop.c", "src/rcore_desktop_glfw.c",
        "src/rcore_desktop_sdl.c", "src/rcore_web.c",
        "src/rcore_android.c", "src/rcore_drm.c", "src/raylib.rc"
    ],
    "exclude_dirs": [
        "examples", "projects", "tools",
        "src/external", "src/platforms"
    ],
    "exclude_exception": ["src/external/glfw/include"],
    "remote": "https://github.com/raysan5/raylib.git"
}
```

### lua (lang: C)

An embeddable scripting language. This is the library version of the scripting language.

NOTE: the `flags` may change on the basis of environment.

**Install with flint:**

```bash
flint add cherts:lua
```

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
    "-ldl", "-lm"
  ],
  "excludes": [
    "lua.c", "onelua.c"
  ],
  "exclude_dirs": ["testes"]
}
```

### boost/asio (lang: C++)

Boost.org asio module

**Install with flint:**

```bash
flint add cherts:asio
```

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
  "exclude_dirs": [""],
  "exclude_exception": ["include"]
}
```

### boost/math (lang: C++)

Boost.org math module

**Install with flint:**

```bash
flint add cherts:math
```

**Composition:**

```json
"math": {
  "version": "unknown",
  "remote": "https://github.com/boostorg/math.git",
  "flags": [
    "-std=c++14",
    "-DBOOST_MATH_STANDALONE=1"
  ],
  "exclude_dirs": [""],
  "exclude_exception": ["include"]
}
```

### mINI (lang: C++)

INI file reader and writer

**Install with flint:**

```bash
flint add cherts:mINI
```

**Composition:**

```json
"mINI": {
    "version": "0.9.20",
    "remote": "https://github.com/metayeti/mINI.git",
    "flags": [
        "-std=c++17"
    ],
    "exclude_dirs": ["tests"]
}
```

### libsodium (lang: C)

A crypto library in C

**Install with flint:**

```bash
flint add cherts:libsodium
```

**Composition:**

```json
"libsodium": {
    "version": "unknown",
    "tmpl": {
        "SODIUM_LIBRARY_VERSION_MAJOR": "30",
        "SODIUM_LIBRARY_VERSION_MINOR":"0",
        "DLL_VERSION": "30",
        "SODIUM_LIBRARY_VERSION": "30:0:0"
    },
    "flags": ["-w"],
    "lib_links": ["-lpthread"],
    "exclude_dirs": ["build", "builds", "test"],
    "remote": "https://github.com/jedisct1/libsodium.git"
}
```

### Mongoose (lang: C)

A http library for C.

**Install with flint:**

```bash
flint add cherts:mongoose
```

**Composition:**

```json
"mongoose": {
    "version": "7.23",
    "remote": "https://github.com/cesanta/mongoose.git",
    "hash": "02bdbb9ed6f0a8f7c42228c6e7cb35d748b60551",
    "lib_links": [
        "windows:-lws2_32",
        "windows:-ladvapi32",
        "windows:-lcrypt32"
    ],
    "flags": [
        "-O3",
        "-Wall",
        "-DMG_TLS=MG_TLS_BUILTIN",
        "-DMG_ENABLE_LOG=0"
    ],
    "exclude_dirs": [
        "resources", "src", "test", "tutorials"
    ]
}
```

### libyaml(lang: C)

YAML library written in C

**Install with flint:**

```bash
flint add cherts:libyaml
```

**Composition:**

```json
"libyaml": {
    "version": "0.2.5",
    "flags": [
        "-D_POSIX_C_SOURCE=200809L",
        "-DYAML_VERSION_MAJOR=0",
        "-DYAML_VERSION_MINOR=2",
        "-DYAML_VERSION_PATCH=5",
        "'-DYAML_VERSION_STRING=\\\"0.2.5\\\"'",
        "-DYAML_DECLARE_STATIC"
    ],
    "lib_links": [],
    "excludes": [],
    "exclude_dirs": [
        "cmake",
        "doc",
        "examples",
        "tests",
        "win32"
    ],
    "exclude_exception": [],
    "remote": "https://github.com/yaml/libyaml.git"
}
```

### libcyaml(lang: C)

Schema based YAML library written in C

**Note:**
`libcyaml` library depends on `libyaml` library. If `libyaml` is already installed in your OS, add `-lyaml` in `lib_links`, else add it as a flint dependency with following:

```bash
flint add cherts:libyaml
```

**Install with flint:**

```bash
flint add cherts:libcyaml
```

**Composition:**

```json
"libcyaml": {
    "version": "unknown",
    "flags": [
        "-std=c11",
        "-O2",
        "-DNDEBUG",
        "-DVERSION_MAJOR=2",
        "-DVERSION_MINOR=0",
        "-DVERSION_PATCH=0",
        "-DVERSION_DEVEL=1"
    ],
    "lib_links": [],
    "excludes": [],
    "exclude_dirs": [
        "build",
        "docs",
        "examples",
        "test"
    ],
    "exclude_exception": ["include"],
    "remote": "https://github.com/tlsa/libcyaml.git"
}
```

### stb(lang: C)

Single-file public domain (or MIT licensed) libraries for C/C++
Included libraries: stb_image.h, stb_image_write.h, stb_image_resize2.h, stb_truetype.h, stb_rect_pack.h, stb_perlin.h, stb_voxel_render.h, stb_dxt.h, stb_easy_font.h, stb_tilemap_editor.h, stb_herringbone_wang_tile.h, stb_vorbis.c, stb_hexwave.h, stb_ds.h, stb_sprintf.h, stb_textedit.h, stb_c_lexer.h, stb_divide.h, stb_include.h, stb_leakcheck.h, stb_connected_components.h

**Install with flint:**

```bash
flint add cherts:stb
```

**Composition:**

```json
"stb": {
    "version": "unknown",
    "remote": "https://github.com/nothings/stb.git",
    "lib_links": ["-lm"],
    "exclude_dirs": [
        "tests",
        "deprecated",
        "tools"
    ]
}
```
