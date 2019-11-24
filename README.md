# ccwarn

`ccwarn`, *C* and *C*++ *Warn*ing, tests C or C++ source against both GCC and Clang automatically.

## Warning

`ccwarn` test target source by compiling and executing it. Hence, DON'T use `ccwarn` against untrusted source.

## Why `ccwarn`?

Both GCC and Clang are popular C and C++ compilers among Unix-like OSes. They can optionally emit non-erroneous warning messages during compilations. Programmers should try their best to reduce those warnings for better code quality.

Nevertheless, it is tedious to write Makefile or another project configuration file for each code base. To address this issue, `ccwarn` automatically tests your code base against both Clang and GCC without any project configuration file.

`ccwarn` intends to check small code base because `ccwarn` doesn't rely on any external project configuration, unsuitable for large and complex projects.

## System Requirements

`ccwarn` itself is written in POSIX shell. Besides, `ccwarn` depends on the following tools:

* GCC
* Clang

`ccwarn` will check these dependencies, emitting an error message if neither is installed on your system.

We tested `ccwarn` on Ubuntu 18.04 LTS. It should work on other Unix-like OSes as well.

## Supported File Formats

`ccwarn` supports the following file formats:

* *.c* for C source
* *.cpp*, *.cxx* or *.cc* for C++ source


`ccwarn` can handle projects that mix C and C++ together.

## Usage

Before using `ccwarn`, add executable mode to it:

```
$ chmod +x path/to/ccwarn
```

Then, copy `ccwarn` to a valid **$PATH** like *$HOME/bin* to use it.

Test against single C file:

```
$ ccwarn path/to/file.c
```

Test against several files:

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

Show help info:

```
$ objcheck help
```

## Environment Variables

You can adjust the behavior of `ccwarn` with the following environment variables:

* **GCC** to set GCC compiler
* **GPP** to set G++ compiler
* **CLANG** to set Clang compiler
* **CLANGPP** to set Clang++ compiler
* **OUT_FILE** to set the name of a temporary output file
* **CFLAGS** to set custom include paths and compiler flags for C
* **CXXFLAGS** to set custom include paths and compiler flags for C++
* **LDFLAGS** to set custom lib paths
* **LIBS** to set custom library linkages
* **LD_LIBRARY_PATH** to set custom binary file paths

All environment variables are optional, set with sensible default values.

## License

Copyright 2019, Michael Chen; licensed under [MIT](https://opensource.org/licenses/MIT).
