# Physics 427 Homework 0

## 1. Setup Git

Homework submission in this course will be done through GitHub. You'll need to
make sure `git` is installed on your system. Use the package installation method
in Problem #1 to install it. 

The next step is to _fork_ this repository by clicking on the "Fork" button on
the GitHub page of this assignment. This will create a mirror of the homework
repository under your own GitHub account. You can then _clone_ this repository
using the following command:

``` sh
git clone https://github.com/your-user-name/Physics-427-homework-0.git
```

You will now have a directory called `Physics-427-homework-0` on your computer.
It will only contain one file, `README.md`, which contains the instructions you
are reading now. In the following sections we will be creating more files, which
will be included in the submission.

## 2. Setting Up C++ and Compile a Simple Program

Now let us set up a C++ compiler on your computer. We will be using the GNU
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

### Commit to git

In order to include this file into the homework submission, run the following command:

``` sh
git add hello_world.cpp
```

It will add this file to the so-called "staging area" for `git`. This is the
area that are going to be tracked by the `git` version control system. You can
now proceed to "commit" the file by writing:

``` sh
git commit -m "Added hello_world.cpp"
```

Committing means making a permanent change to the repository that is recorded by
`git`. `git` works by keeping track of a history of commits. Each commit has its
own hash number, and you will have the ability to look at individual commits or
revert to an older commit. The part after `-m` is called the commit message,
which goes into the commit log to indicate what you did for this particular
commit.

Now `git` knows about the change (of adding the file `hello_world.cpp`) on your
machine. In order to upload this commit to the internet, we need to "push" to a
remote server, which is GitHub in this case. We need to run:

``` sh
git push origin main
```

This will upload all your commits to GitHub, under the repository that you
forked in Problem #1. You should now be able to see this new file on the
repository webpage (of your fork, not the original assignment webpage).

## 3. 
