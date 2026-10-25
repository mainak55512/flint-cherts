**Study the supplied sample composition json:**

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
### Elements:

- version: version number/git tag name of the library
- flags: c/c++ compiler flags
- lib_links: library flags passed to compiler
- excludes: file paths that are ignored during compilation
- exclude_dirs: directory paths that are ignored during compilation
- exclude_exception: directory paths that resides inside an excluded directory, but are required for compilation
- remote: github repository url for the library

**NOTE**: `flags`, `lib_links`, `excludes`, `exclude_dirs` & `exclude_exception` can have entries starting with one of the following tags:

- `windows:`: applicable only for windows
- `linux:`: applicable only for linux
- `macos:`: applicable only for macOS
- `unix:`: applicable for both linux and macOS

Non-prefixed entries are applied for all operating systems.

**CRITICAL INSTRUCTIONS:**
You will be given one or more build configuration/scripts (makefile, CMakeLists.txt, bash script, powershell script etc.), your job is to study it and generate a composition json like the one that was given before.
Consider any other additional information provided along with this instruction.
Only return the json string, **NO EXPLAINATION REQUIRED**.
If you have understood the instruction properly, say "GOT IT".
