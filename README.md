# ccwarn

`ccwarn`, aka *C* and *C*++ *Warn*ings, is a **strict and opinionated** tool that tests C or C++ source against both GCC and Clang.

It is designed as a **teaching aid and coding discipline enforcer**, not a full build system.

## Why `ccwarn`?

Both GCC and Clang are popular C and C++ compilers among Unix or Unix-like systems. They can optionally emit non-erroneous warning messages during compilations. Programmers should try their best to reduce those warnings for better code quality.

Nevertheless, it is tedious to write Makefile or another project configuration file for each code base. To address this issue, `ccwarn` automatically tests your code base against both Clang and GCC without any project configuration file.

In addition to code warnings, `ccwarn` can be used to test language standard conformity for your code base against both GCC and Clang as well.

`ccwarn` intends to test small code base because `ccwarn` doesn't rely on any external project configuration, unsuitable for large and complex projects.

## System Requirements

`ccwarn` itself is written in POSIX shell. Besides a shell, `ccwarn` depends on both GCC and Clang.

## Supported File Formats

- *.c* for C source
- *.cpp*, *.cxx* or *.cc* for C++ source

## Supported Language Standards

### C Standards

- C89 / C90 / ANSI
- C99
- C11
- C17 / C18
- C23

### C++ Standards

- C++98 / C++03
- C++11
- C++14
- C++17
- C++20
- C++23

## Usage

```sh
./ccwarn path/to/*.c path/to/*.cpp
```

## Warning Policy

`ccwarn` enforces a **strict but practical** warning policy.

### Enabled warnings

- -Wall -Wextra -Wpedantic
- -Wconversion
- -Wsign-conversion
- -Wshadow
- -Wformat=2
- -Wnull-dereference

### Treated as errors

- -Werror=conversion
- -Werror=sign-conversion
- -Werror=format=2

## Environment Variables

- GCC / GXX / CLANG / CLANGXX
- CSTD (default: c11)
- CXXSTD (default: c++20)
- CFLAGS / CXXFLAGS

## Philosophy

This tool enforces:

- explicit over implicit
- no unsafe conversions
- portability across compilers
- warnings treated as potential bugs

## Intended Use

Best for:

- small programs
- exercises
- learning projects
- warning cleanup

Not intended for large production codebases.

## License

MIT
