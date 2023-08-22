# Physics 427 Homework 0

## 1. Setting Up C++ and Compile a Simple Program

First let us set up a C++ compiler on your computer. We will be using the GNU
Compiler Collection (GCC), which includes a C++ compiler called `g++`.
Follow the instructions depending on your operating system:

### Windows

We will install the Windows Subsystem for Linux (WSL), which lets you install a
Linux distribution such as Ubuntu on your system, allowing you to run Linux
applications and commandline utilities directly on Windows. If you use Windows
10 version 2004 and higher, or Windows 11, you can directly install WSL with a
single command. Open PowerShell or Windows Command Prompt in administrator mode by
right-clicking and selecting __Run as administrator__, enter:

``` powershell
wsl --install
```
then restart your machine following the prompt. You may need to run Windows
Update before the installation can correctly do its job. For more information,
refer to
the [official tutorial](https://learn.microsoft.com/en-us/windows/wsl/install). By default, the above command will install the Ubuntu distribution
on your computer. Follow the
official
[setup guide](https://learn.microsoft.com/en-us/windows/wsl/setup/environment) to set up your WSL development environment including a Linux user name
and password, updating packages, and setting up Windows Terminal. You
_don't_ need to add additional distributions.

Once you have WSL, enter the Linux command line and install `gcc` using:

``` sh
sudo apt-get install gcc
```

### Mac OS

You can install GCC using `homebrew`. First, install `homebrew`
following the instructions on its [official website](https://brew.sh/).
`homebrew` can install packages that are often used in the Linux community
but not typically included in Mac OS.

You can now run the following command to install GCC:

``` sh
brew install gcc
```

### Linux

If you use Linux, I expect that you know how to manage software packages on your
computer. Make sure you install GCC using your package manager.

### Compiling a Hello World Program

First, check that you have installed the compiler correctly by running the
following command in your terminal (in the case of Windows, enter WSL first):

``` sh
g++ --version
```
If the command prints something like `g++ (GCC) 12.2.1` or some other versions, then you are ready to go. If not, go back to previous steps and figure out what you did wrong.

Write the following snippet into a text file and save it as `hello_world.cpp`:

``` c++
#include <iostream>
int main() {
  std::cout << "Hello World" << std::endl;
  return 0;
}
```

Now compile and run the code using the following command:

``` sh
g++ hello_world.cpp && ./a.out
```
The default output of `g++` is an executable binary file called
`a.out`, and we call that executable using `./a.out`.

## 2. Setup Git

Homework submission in this course will be done through GitHub. You'll need to
make sure `git` is installed on your system. Use the package installation method
in Problem #1 to install it. 

The next step is to _fork_ this repository. This will create a mirror of the
homework repository under your own GitHub account. You can then _clone_ this
repository using the following command:
``` sh
git clone https://github.com/your-user-name/Physics-427-homework-0.git
```


## Setup a Code Editor
