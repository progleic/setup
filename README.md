# Development environment

[Programação (LEIC.009)](https://moodle.up.pt/course/view.php?id=4083) @ [LEIC](https://paginas.fe.up.pt/~estudar/cursos/licenciatura-engenharia-informatica/)

## Basic requirements

1. Linux or Linux-compatible environment.
2. Required installation: [GCC](https://gcc.gnu.org) (C/C++ compiler) and [Make](https://www.gnu.org/software/make/) (build tool).
3. Optional (but recommended): [GDB](https://www.sourceware.org/gdb/) (C/C++ debugger).
4. A text editor of your choice. 

__All these tools are installed in FEUP's labs running Linux.__
 
## Compilation settings

### `Makefile`

Use this [Makefile](Makefile). To compile program `x` with source code `x.cpp` it then suffices to execute `make x`:

```
$ make x
g++ -std=c++11 -pedantic -Wall -Werror -g  -lm -fsanitize=address -fsanitize=undefined     x.cpp   -o x
```

### Compiler settings and their meaning

(according to Makefile contents) 

Option |  Meaning
-------|----------
`-std=c++11` `-pedantic` | Set C++ 2011 as the language standard, and enforce it strictly.
`-Wall -Werror` | Generate all possible warnings, treat warnings as compilation errors.
`-g`   | Generate executable with debug symbols, suitable for use with `gdb`.
`-lm` | Link with math library.
`-fsanitize=address -fsanitize=undefined`| Enable the use of [AddressSanitizer](https://github.com/google/sanitizers/wiki/AddressSanitizer) and [Undefined Behavior Sanitizer](https://clang.llvm.org/docs/UndefinedBehaviorSanitizer.html)


# Development environment for your PC

### Linux

#### Installing Linux

There are several Linux distributions, e.g., [Ubuntu](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview) as in FEUP's labs.

#### Package installation

Package [`build-essential`](https://packages.ubuntu.com/focal/build-essential) contains GCC:

On Ubuntu for instance, it can be installed as follows:

```
sudo apt install buid-essential 
```

To install `gdb`:

```
sudo apt install gdb
```

### Windows

#### Windows Subsystem for Linux (WSL) - RECOMMENDED 

Use the [Windows Subsystem for Linux (WSL)](https://docs.microsoft.com/en-us/windows/wsl/about).

WSL will provide you with a _"GNU/Linux environment -- including most command-line tools, utilities, and applications -- directly on Windows, unmodified, without the overhead of a traditional virtual machine or dualboot setup"_.

#### Alternative - Linux VM image

Use [Virtual Box](https://www.virtualbox.org/) for running a Linux VM,
e.g., check this [guide for Ubuntu](https://ubuntu.com/tutorials/how-to-run-ubuntu-desktop-on-a-virtual-machine-using-virtualbox#1-overview).


#### NOT RECOMMENDED!

[Mingw](https://www.mingw-w64.org/) or [Cygwin](http://cygwin.com/) are NOT recommended. The GCC compiler bundled with these environments may not 
contain all the required features. 


### MacOS

### gcc and gdb using Homebrew - RECOMMENDED

Install gcc and gdb using the [Homebrew package manager](https://brew.sh/).

- [gcc](https://formulae.brew.sh/formula/gcc#default)
- [gdb](https://formulae.brew.sh/formula/gdb#default) - you also need to follow the [complementary steps for code-signing gdb](https://sourceware.org/gdb/wiki/PermissionsDarwin)


#### Alternative - use clang

[XCode](https://developer.apple.com/xcode/) includes the [clang C/C++ compiler](https://clang.llvm.org/) that has the same command-line switches as gcc. The [LLDB debugger](https://lldb.llvm.org/) is also an alternative to gdb. 

Some necessary features may be missing from XCode's version of clang compiler, however. The [LLVM version configured through Homebrew](https://formulae.brew.sh/formula/llvm#default) should work better.

#### Alternative - Linux VM image

Check the instructions given for Windows previously.

### Online IDE

[Replit](https://replit.com)

