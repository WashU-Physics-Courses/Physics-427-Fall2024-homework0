# Physics 427 Homework 0

__Due 9:00am Friday 9/1/2023__

This homework is not graded and is designed to help you set up your computer
environment and understand the homework submission process. It has an unusual
deadline of Friday 9/1 since you will need to go through this set up process
before the first real homework is due.

## 0. Setting Up a Developing Environment

We want to set up a Linux development environment on your computer. This will be
important since most of the tools we use live in the command line, and they are
part of a software ecosystem. The instructions will depend on your operating system:

### Windows

We will need to install the Windows Subsystem for Linux (WSL), which lets you
have a Linux distribution such as Ubuntu on your system, allowing you to run
Linux applications and command line utilities directly on Windows. If you use
Windows 10 version 2004 and higher, or Windows 11, you can directly install WSL
with a single command. Open PowerShell or Windows Command Prompt in
administrator mode by right-clicking and selecting __Run as administrator__,
enter:

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

To install a software package, use `apt-get install`. For example, we will use
`git` throughout this course. Install `git` using the following command:

``` sh
apt-get install git
```

### Mac OS

You can install GCC using `homebrew`. First, install `homebrew` using the following command:

``` sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

`homebrew` can install packages that are often used in the Linux community but
not typically included in Mac OS. To install a software package, use `brew
install`. For example, we will use `git` throughout this course. Install `git`
using the following command:

``` sh
brew install git
```

### Linux

If you use Linux, I expect that you know how to manage software packages on your
computer. Make sure you install GCC using your package manager. If you use
Ubuntu, then the instruction is the same as WSL outlined above.

## 1. Setup Git

Homework submission in this course will be done through GitHub. You'll need to
make sure `git` is installed on your system, which was done in the previous
problem.

You can "clone" this repository onto your own computer, and add your content to
it. This will be your version of the homework and will be how it is submitted too. 

``` sh
git clone https://github.com/[your_user_name]/[your_assignment_repository]/
```

`[your_assignment_repository]` will look like something similar to
`phys-427-homework-0-[your_user_name]`. You will now have a directory with this
name on your computer. It will only contain one file, `README.md`, which has the
instructions you are reading now. In the following sections we will be creating
more files, and submit them as the actual assignment.

## 2. Setting Up C++ and Compile a Simple Program

Now let us set up a C++ compiler on your computer. We will be using the GNU
Compiler Collection (GCC), which includes a C++ compiler called `g++`.
Follow the instructions depending on your operating system:

### Compiling a Hello World Program

First, install `gcc` using the package manager we discussed above. You can check
that you have installed the compiler correctly by running the following command
in your terminal (in the case of Windows, enter WSL first):

``` sh
g++ --version
```

If the command prints something like `g++ (GCC) 12.2.1` or some other versions,
then you are ready to go. If not, go back to previous steps and figure out what
you did wrong.

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
repository webpage (of your fork, not the original assignment webpage). You can
upload to the repository as many times as you want up until the deadline cutoff
time. The system will freeze the repository automatically at the deadline, and
you will not be able to update it afterwards. 
