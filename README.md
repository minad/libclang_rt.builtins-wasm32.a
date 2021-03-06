# libclang_rt.builtins-wasm32.a

LLVM 8 can compile to WebAssembly out of the box.

If you are using macOS with Homebrew, or another operating system with up-to-date LLVM packages, you're all set.

Almost.

Unless your WebAssembly application is compute-only, you still need some kind of interface with the system.

[WASI](https://wasi.dev) is the de facto standard, and can be compiled using a stock clang/LLVM 8 installation.

Its source code can be found here: [WASI sysroot](https://github.com/CraneStation/wasi-sysroot), and compiles fine even on non-Linux system.

*Now* you should be all set:

```sh
clang --target=wasm32-unknown-wasi --sysroot=/opt/wasi-sysroot -Ofast test.c
```

Almost.

Building an object file or library will work, but building a module will not, due to the `libclang_rt.builtins-wasm32.a` file missing.

You can either recompile `clang_rt` from the `wasi-sdk` repository to get it.

Or directly download that file here: [libclang_rt.builtins-wasm32.a](precompiled/).
