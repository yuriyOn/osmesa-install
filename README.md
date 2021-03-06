# osmesa-install

Script and patches to build and install variations of OSMesa http://www.mesa3d.org/osmesa.html:
- "mangled" or not (in mangled OSMesa, all functions start with `mgl` instead of `gl`)
- debug or not
- choice of osmesa driver: `swrast`, `softpipe`, `llvmpipe` or `swr` (SWR is not yet supported on macOS)
- possibility to also compile and install LLVM 4.0.0 or 3.4.2 for the `llvmpipe` driver

## Usage

- edit variables / paths as the beginning of the `osmesa-install.sh`
  script
- compile and install:
```
mkdir build
cd build
sh ../osmesa-install.sh
```
- there is a test program on the `osdemo` directory, with a few checks

## Notes and caveats

The script fixes the following Mesa bugs related to mangled OSMesa:
- [GL/gl_mangle.h misses symbols from GLES/gl.h](https://bugs.freedesktop.org/show_bug.cgi?id=91724)

Also note that the latest clang (tested with 4.0.0) does not build on 32 bits mingw64 due to the following gcc bug (older versions of clang work):
- http://lists.llvm.org/pipermail/cfe-dev/2016-December/052017.html
- https://gcc.gnu.org/bugzilla/show_bug.cgi?id=78936
