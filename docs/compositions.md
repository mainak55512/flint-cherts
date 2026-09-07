## Flint Cherts

Paste the "composition" for the dependency in the `dependencies` section of your `composition.json` file and run `flint sync`.

### Arena (lang: C)

An arena allocator written purely in C.

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
