# Development environment

[Programação (LEIC.009)](https://moodle.up.pt/course/view.php?id=2030) @ [LEIC](https://paginas.fe.up.pt/~estudar/cursos/licenciatura-engenharia-informatica/)

## Basic requirements

1. Linux or Linux-compatible environment.
2. Required installation: [GCC](https://gcc.gnu.org) (C/C++ compiler) and [Make](https://www.gnu.org/software/make/) (build tool).
3. Optional (but recommended): [GDB](https://www.sourceware.org/gdb/) (C/C++ debugger).
4. [Visual Studio Code](https://code.visualstudio.com/) or a simple text editor of your choice. 

__All these tools are installed in FEUP's labs running Linux.__
 
## Compilation settings

### `Makefile`

Use this [Makefile](Makefile). 

To compile program `x` with source code `x.cpp` it then suffices to execute `make x`:

  ```
$ make x
g++ -std=c++11 -pedantic -Wall -Wuninitialized -Werror -g  -lm -fsanitize=address -fsanitize=undefined     x.cpp   -o x
  ```

To compile a program (`PROG`) with several sources (`CPP_FILES`) and headers (`HEADERS`) execute `make PROG=... CPP_FILES="..." HEADERS="..."`, for instance:

  ```
$ make PROG=hello CPP_FILES="hello.cpp hello_main.cpp" HEADERS="hello.h"
g++ -std=c++11 -pedantic -Wall -Wuninitialized -Werror -g  -lm -fsanitize=address -fsanitize=undefined  hello.cpp hello_main.cpp -o hello
  ```

### Compiler settings and their meaning

(according to Makefile contents) 

Option |  Meaning
-------|----------
`-std=c++11` `-pedantic` | Set C++ 2011 as the language standard, and enforce it strictly.
`-Wall -Wuninitialized -Werror` | Generate all standard warnings, warnings for uninitialized variables, and treat warnings as compilation errors.
`-g`   | Generate executable with debug symbols, suitable for use with GDB.
`-lm` | Link with math library.
`-fsanitize=address -fsanitize=undefined`| Enable the use of [AddressSanitizer](https://github.com/google/sanitizers/wiki/AddressSanitizer) and [Undefined Behavior Sanitizer](https://clang.llvm.org/docs/UndefinedBehaviorSanitizer.html)


# Development environment for your PC

### Linux

#### Installing Linux

There are several Linux distributions, e.g., [Ubuntu](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview) as in FEUP's labs.

#### Package installation

Package [`build-essential`](https://packages.ubuntu.com/focal/build-essential) contains GCC and Make. On Ubuntu for instance, this package can be installed as follows:

```
sudo apt install build-essential 
```

To install GDB as well, execute:

```
sudo apt install gdb
```



### Windows

#### Windows Subsystem for Linux (WSL) - RECOMMENDED 

Use the [Windows Subsystem for Linux (WSL)](https://docs.microsoft.com/en-us/windows/wsl/about).

WSL will provide you with a _"GNU/Linux environment -- including most command-line tools, utilities, and applications -- directly on Windows, unmodified, without the overhead of a traditional virtual machine or dualboot setup"_.

If you configure WSL to run Ubuntu, then you may install GCC and GDB as illustrated previously for (standalone) Linux;
simply run the following commands in the WSL command line:

```
sudo apt install build-essential 
sudo apt install gdb
```

#### Alternative - Linux VM image 

Use [Virtual Box](https://www.virtualbox.org/) for running a Linux VM,
e.g., check this [guide for Ubuntu](https://ubuntu.com/tutorials/how-to-run-ubuntu-desktop-on-a-virtual-machine-using-virtualbox#1-overview).

#### NOT RECOMMENDED!

[Mingw](https://www.mingw-w64.org/) or [Cygwin](http://cygwin.com/) are NOT recommended. The GCC compiler bundled with these environments may not 
contain all the required features. 


### MacOS

### GCC and GDB using Homebrew - RECOMMENDED

Install GCC and GDB using the [Homebrew package manager](https://brew.sh/).

- [GCC](https://formulae.brew.sh/formula/gcc#default)
- [GDB](https://formulae.brew.sh/formula/gdb#default) - you also need to follow the [complementary steps for code-signing GDB](https://sourceware.org/gdb/wiki/PermissionsDarwin)


#### Alternative - use clang

[XCode](https://developer.apple.com/xcode/) includes the [clang C/C++ compiler](https://clang.llvm.org/) that has the same command-line switches as gcc. The [LLDB debugger](https://lldb.llvm.org/) is also an alternative to GDB. 

Some necessary features may be missing from XCode's version of clang, however. 
The [LLVM clang version configured through Homebrew](https://formulae.brew.sh/formula/llvm#default) should work better.

#### Alternative - Linux VM image

Check the instructions given for Windows and VirtualBox above.

### Visual Studio Code setup

__Note__: Visual Studio Code does not include GCC, GDB or Make. Install those tools first as described above.

Steps:

- Install Visual Studio Code on [Linux](https://code.visualstudio.com/docs/setup/linux), [MacOS](https://code.visualstudio.com/docs/setup/mac), or [Windows](https://code.visualstudio.com/docs/setup/windows)
- [Install the C/C++ extension for Visual Studio Code](https://code.visualstudio.com/docs/languages/cpp)
- For Windows + WSL, see this tutorial: [Using C++ and WSL in VS Code](https://code.visualstudio.com/docs/cpp/config-wsl)

You can then use Visual Studio Code as a C++ editor and use the built-in terminal for compiling programs using `make`, then run or debug the programs, etc.

### Online IDE

You can use [Replit](https://replit.com) as a (temporary) work-around.

