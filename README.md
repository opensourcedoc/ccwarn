# ccwarn

`ccwarn`, aka *C* and *C*++ *Warn*ings, tests C or C++ source against both GCC and Clang automatically.

## Warning

`ccwarn` checks target source by compiling and executing it. Hence, DON'T use `ccwarn` to test untrusted source.

## Why `ccwarn`?

Both GCC and Clang are popular C and C++ compilers among Unix-like OSes. They can optionally emit non-erroneous warning messages during compilations. Programmers should try their best to reduce those warnings for better code quality.

Nevertheless, it is tedious to write Makefile or another project configuration file for each code base. To address this issue, `ccwarn` automatically tests your code base against both Clang and GCC without any project configuration file.

In addition to code warnings, `ccwarn` can be used to test language standard conformity for your code base against both GCC and Clang as well.

`ccwarn` intends to test small code base because `ccwarn` doesn't rely on any external project configuration, unsuitable for large and complex projects.

## System Requirements

`ccwarn` itself is written in POSIX shell. Besides a shell, `ccwarn` depends on

* GCC
* Clang

`ccwarn` will check these dependencies, emitting an error message if neither is installed on your system.

We tested `ccwarn` on several Unix or Unix-like systems:

* Ubuntu 18.04 LTS
* Amazon Linux, largely RHEL and CentOS compatible
* TrueOS, FreeBSD derived
* Solaris

It should work on other Unix-like systems as well.

## Supported File Formats

`ccwarn` supports the following file formats:

* *.c* for C source
* *.cpp*, *.cxx* or *.cc* for C++ source

`ccwarn` can handle projects that mix C and C++ together.

## Supported Language Standards

### C Standards

* C89: `c89`, `c90`, `ansi`
* C99: `c99`, `c9x`
* C11: `c11`, `c1x`
* C17: `c17`, `c18`
* C20: `c2x`

### C++ Standards

* C++98: `c++98`, `c++03`
* C++11: `c++11`, `c++0x`
* C++14: `c++14`, `c++1y`
* C++17: `c++17`, `c++1z`
* C++20: `c++2a`

## Usage

Before using `ccwarn`, add executable mode to it:

```
$ chmod +x path/to/ccwarn
```

Then, copy `ccwarn` to a valid **$PATH** like *$HOME/bin* or */usr/local/bin* to use it.

Test single C file:

```
$ ccwarn path/to/file.c
```

Test multiple files in a project:

```
$ ccwarn path/to/*.c
```

Test for a static library:

```
$ ccwarn static path/to/*.c
```

Test for a dynamic library:

```
$ ccwarn dynamic path/to/*.c
```

Test for C and C++ mixed code base:

```
$ ccwarn path/to/*.c path/to/*.cpp
```

Test some executable with arguments:

```
$ ccwarn path/to/*.c -- --opt param_a param_b param_c
```

Show help info:

```
$ ccwarn help
```

## Environment Variables

You can adjust the behavior of `ccwarn` with the following environment variables:

* **GCC** to set GCC compiler
* **GXX** to set G++ compiler
* **CLANG** to set Clang compiler
* **CLANGXX** to set Clang++ compiler
* **CSTD** to set C standard, default to C11
* **CXXSTD** to set C++ standard, default to C++17
* **OUT_FILE** to set the name of a temporary output file
* **CFLAGS** to set custom include paths and compiler flags for C
* **CXXFLAGS** to set custom include paths and compiler flags for C++
* **LDFLAGS** to set custom lib paths
* **LIBS** to set custom library linkages
* **LD_LIBRARY_PATH** to set custom binary file paths

All environment variables are optional, set with sensible default values.

## Note

If you just want to run some C or C++ source, see [ccrun](https://github.com/cwchentw/ccrun).

## License

Copyright 2019, Michael Chen; licensed under [MIT](https://opensource.org/licenses/MIT).
