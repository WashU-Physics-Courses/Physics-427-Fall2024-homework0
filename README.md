# Physics 427 Homework 0

__Due 11:59pm Thursday 8/29/2024__

This homework is not graded and is designed to help you set up your computer environment and understand the homework submission process. It has an unusual deadline of Thursday 8/29 to force you go throuYgh this set up process before the first real homework is due.

## 1. Setting Up a Developing Environment

We want to set up a Linux development environment on your computer. This will be important since most of the tools we use live in the command line, and they are part of a software ecosystem. The instructions will depend on your operating system:

### Windows

We will need to install the Windows Subsystem for Linux (WSL), which lets you have a Linux distribution such as Ubuntu on your system, allowing you to run Linux applications and command line utilities directly on Windows. If you use Windows 10 version 2004 and higher, or Windows 11, you can directly install WSL with a single command. Open PowerShell or Windows Command Prompt in administrator mode by right-clicking and selecting __Run as administrator__, enter:

``` powershell
wsl --install
```
then restart your machine following the prompt. You may need to run Windows Update before the installation can correctly do its job. For more information, refer to the [official tutorial](https://learn.microsoft.com/en-us/windows/wsl/install). By default, the above command will install the Ubuntu distribution on your computer. Follow the official [setup guide](https://learn.microsoft.com/en-us/windows/wsl/setup/environment) to set up your WSL development environment including a Linux user name and password, updating packages, and setting up Windows Terminal. You _don't_ need to add additional distributions.

To install a software package, use `apt-get install`. For example, we will use `git` throughout this course. Install `git` using the following command:

``` sh
apt-get install git
```

Install `g++` using the following command:

```sh
apt-get install g++
```

### Mac OS

You can install GCC using `homebrew`. First, install `homebrew` using the following command:

``` sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

`homebrew` can install packages that are often used in the Linux community but not typically included in Mac OS. To install a software package, use `brew install`. For example, we will use `git` throughout this course. Install `git` using the following command:

``` sh
brew install git
```

Install `gcc` (which includes `g++`) using the following command:

```sh
brew install gcc
```

### Linux

If you use Linux as your everyday OS, I expect that you know how to manage software packages on your computer. Make sure you install GCC using your package manager. If you use Ubuntu, then the instruction is the same as WSL outlined above.

## 2. Setup Git

After installing `git`, the first thing you should do is set up your user name and email address. This is important because every Git commit uses this information, and it's immutably baked into the commits you start creating. You only need to do this once for a given computer:

``` sh
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
```
You may also want to run the following command, which sets the following default pull strategy. Otherwise `git` will ask you to set it the first time you need to do a merge when pulling.
``` sh
git config --global pull.rebase false
```

Homework submission in this course will be done through GitHub. You need to register for a free GitHub account. It is beneficial to set up an SSH key on GitHub to avoid typing your username and password everytime. To do this, install `openssh-client` (if you use WSL or Debian-based Linux distributions like Ubuntu) or `openssh` (if you use homebrew on Mac, or use Arch/SUSE based Linux distributions) using the package manager above. Then in the terminal, run:

``` sh
ssh-keygen
```
and accept all default options by just hitting "Enter". You will create an `rsa` key under `~/.ssh/` where `~` is your home directory (the default directory when you enter terminal). You need the content of `~/.ssh/id_rsa.pub`, which you can see by the following command:

``` sh
cat ~/.ssh/id_rsa.pub
```
You should see several lines of gibberish, starting with "ssh-rsa" and ending with your machine name. In your GitHub account settings, under "SSH and GPG Keys", you can create a "New SSH key" and copy the whole output of the above command (including "ssh-rsa" and your machine name) into the "Key" text box. Now you should be able to do the following without needing to type your GitHub username and password.

You need to "clone" this repository onto your own computer, and add your content to it. This will be your version of the homework and will be how it is submitted too. 

``` sh
git clone git@github.com:WashU-Physics-Courses/[your_assignment_repository]/
```

`[your_assignment_repository]` will look like something similar to `physics-427-fall-2024-homework-0-[your_user_name]`. Setting up an SSH key is required, since GitHub has disabled the username and password login option. You will now have a directory with this name on your computer. It will only contain one file, `README.md`, which has the instructions you are reading now. In the following sections we will be creating more files, and submit them as the actual assignment.

## 3. Setting Up C++ and Compile a Simple Program

Now let us set up a C++ compiler on your computer. We will be using the GNU Compiler Collection (GCC), which includes a C++ compiler called `g++`. 

### Compiling a Hello World Program

First, install `gcc` using the package manager we discussed above. You can check that you have installed the compiler correctly by running the following command in your terminal (in the case of Windows, enter WSL first):

``` sh
g++ --version
```

If the command prints something like `g++ (GCC) 12.2.1` or some other version, then you are ready to go. If not, go back to previous steps and figure out what you did wrong. __Note__: For MacOS, it comes with a special version of `g++` out of the box, so if you just call `g++` it will default to that version. To use the version you installed using `brew`, you need to call `g++-14` or `g++-13` depending on which version `brew` installed for you.

Write the following snippet into a text file and save it as `hello_world.cpp`:

``` c++
#include <iostream>
int main() {
  std::cout << "Hello World" << std::endl;
  return 0;
}
```
In general, `std::cout` is the most common way to write output to the terminal. You can write multiple different things in a line as long as they are separated by the operator `<<`. `std::endl` will end the output line and start a new line (and flush the output buffer).

Now compile and run the code using the following command (again, use `g++-14` or `g++-13` if you are on Mac):

``` sh
g++ hello_world.cpp && ./a.out
```

The first part of the command compiles the code and creates a binary executable file called `a.out`. The second part after `&&` runs the `a.out` program under the current directory. You should see "Hello World" printed on a new line in terminal.

`a.out` is the default executable output file from `g++`. You can change the name of the output file using the `-o` option. For example:

``` sh
g++ -o hello_world hello_world.cpp && ./hello_world
```


## 4. Working with git

In order to include this file into the homework submission, run the following command:

``` sh
git add hello_world.cpp
```

It will add this file to the so-called "staging area" for `git`. This is the area that are going to be tracked by the `git` version control system. You can now proceed to "commit" the file by writing:

``` sh
git commit -m "Added hello_world.cpp"
```

Committing means making a permanent change to the repository that is recorded by `git`. `git` works by keeping track of a history of commits. Each commit has its own hash number, and you will have the ability to look at individual commits or revert to an older commit. The part after `-m` is called the commit message, which goes into the commit log to indicate what you did for this particular commit.

Now `git` knows about the change (of adding the file `hello_world.cpp`) on your machine. In order to upload this commit to the internet, we need to "push" to a remote server, which is GitHub in this case. We need to run:

``` sh
git push origin main
```

This will upload all your commits to GitHub, under the repository that you forked in Problem #1. You should now be able to see this new file on the repository webpage (of your fork, not the original assignment webpage). You can upload to the repository as many times as you want up until the deadline cutoff time. The system will freeze the repository automatically at the deadline, and you will not be able to update it afterwards. 

In future assignments, the `git add/commit/push` cycle will be the main way to submit your work. At any point, you can run `git status` to check what files are untracked (they need to be added to the repository in order to be submitted), what files are updated (you also need to add the change before committing), what files are staged for commit (the files that have already been added), and how many commits you are ahead of (or behind) the upstream repository.

In general, do not add or commit compiled binary files like `a.out` to the git repository. You can filter them out so that git ignores them by writing a `.gitignore` file in the root of the repository (same level as `README.md`). An example `.gitignore` file (note `.` is part of the file name that tells Linux that it's a hidden file) is as follows:

``` sh
a.out
*.o
*.so
*.a
```

GitHub is a website that hosts `git` repositories and provides a variety of services related to these repositories. If you want to learn more about GitHub, you can take the optional "Intro to Git and GitHub" mini-course here: https://classroom.github.com/a/lM4if9io.
