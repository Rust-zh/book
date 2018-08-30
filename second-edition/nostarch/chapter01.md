
[TOC]

<!--
# Getting Started
-->

# 入门指南

<!--
Let’s start your Rust journey! In this chapter, we’ll discuss:
-->

让我们开始 Rust 之旅吧！在本章中，我们会讨论：

<!--
* Installing Rust on Linux, macOS, and Windows
* Writing a program that prints “Hello, world!”
* Using `cargo`, Rust’s package manager and build system
-->

* 在 Linux、macOS 或 Windows 上安装 Rust
* 编写一个打印“Hello, world!”的程序
* 使用 Rust 的包管理和构建系统 `cargo`

<!--
## Installation
-->

## 安装

<!--
The first step is to install Rust. We’ll download Rust through `rustup`, a
command line tool for managing Rust versions and associated tools. You’ll need
an internet connection for the download.
-->

首先要安装 Rust。我们可以通过 `rustup` 下载 Rust，这是一个管理 Rust 版本和相关工具的命令行工具。下载时需要联网。

<!--
The following steps install the latest stable version of the Rust compiler. All
the examples and output in this book use stable Rust 1.21.0. Rust’s stability
guarantees ensure that all the examples in the book that compile will continue
to compile with newer Rust versions. The output might differ slightly between
versions, because Rust often improves error messages and warnings. In other
words, any newer, stable version of Rust you install using these steps should
work as expected with the content of this book.
-->

接下来的步骤会安装最新的稳定版 Rust 编译器。本书所有示例和输出采用稳定版的 Rust 1.21.0。Rust 的稳定性确保了本书所有示例都能在最新版本的 Rust 中编译。不同版本的输出可能略有不同，因为 Rust 经常改进错误信息和警告。也就是说，通过这些步骤安装的最新稳定版 Rust，能够正常运行本书中的内容。

<!--
> ### Command Line Notation
>
> In this chapter and throughout the book, we’ll show some commands used in the
> terminal. Lines that you should enter in a terminal all start with `$`. You
> don’t need to type in the `$` character; it indicates the start of each
> command. Many tutorials use the convention `$` for commands you run as a
> regular user and `#` for commands you run as an administrator. Lines that
> don’t start with `$` typically show the output of the previous command.
> Additionally, PowerShell specific examples will use `>` rather than `$`.
-->

> ### 命令行记法
>
> 在本章和全书中，我们会展示一些需要在终端下使用的命令。所有需要输入到终端的行都以 `$` 开头。但无需输入 `$`，它代表每行命令的起点。不以 `$` 起始的行通常为之前命令的输出。另外，PowerShell 专用的示例会采用 `>` 而非 `$`。

<!--
### Installing Rustup on Linux or macOS
-->

### 在 Linux 或 macOS 上安装 Rustup

<!--
If you’re using Linux or macOS, open a terminal and enter the following command:
-->
如果你使用 Linux 或 macOS，请打开终端并输入如下命令：

```
$ curl https://sh.rustup.rs -sSf | sh
```

<!--
The command downloads a script and starts the installation of the `rustup`
tool, which installs the latest stable version of Rust. You might be prompted
for your password. If the install is successful, the following line will appear:
-->

此命令会下载一个脚本以安装 `rustup` 工具，该工具可安装最新稳定版的 Rust。安装过程中可能会提示你输入密码。如果安装成功，将会出现如下内容：

```
Rust is installed now. Great!
```

<!--
Of course, if you distrust using `curl URL | sh` to install software, you can
download, inspect, and run the script however you like.
-->

当然，如果你不信任用  `curl URL | sh` 来安装软件，可在运行前下载并检查该脚本。

<!--
The installation script automatically adds Rust to your system PATH after your
next login. If you want to start using Rust right away instead of restarting
your terminal, run the following command in your shell to add Rust to your
system PATH manually:
-->


此安装脚本会自动将 Rust 加入系统的 PATH 环境变量中，在下一次登录时生效。如果你希望立刻就开始使用 Rust 而不重启终端，请在 Shell 中运行如下命令，手动将 Rust 加入系统的 PATH 变量中：

```
$ source $HOME/.cargo/env
```

<!--
Alternatively, you can add the following line to your *~/.bash_profile*:
-->

或者，你也可以在 `~/.bash_profile` 文件中增加如下这行代码：

```
$ export PATH="$HOME/.cargo/bin:$PATH"
```

<!--
Additionally, you’ll need a linker of some kind. It’s likely one is already
installed, but when you try to compile a Rust program and get errors indicating
that a linker could not execute, you’ll need to install one. You can install a
C compiler, because that will usually come with the correct linker. Check your
platform’s documentation for how to install a C compiler. Some common Rust
packages depend on C code and will need a C compiler too, so it might be worth
installing one now regardless.
-->

此外，你还需要某种链接器（linker），它很可能已经安装了。如果你在尝试编译 Rust 程序时，有错误指出无法执行链接器，这意味着你的系统上没有安装链接器，你需要自行安装。C 编译器通常带有正确的链接器，请查看你使用平台的文档，了解如何安装 C 编译器。一些常用的 Rust 包依赖 C 代码，也需要安装 C 编译器，因此现在安装一个是值得的。

<!--
### Installing Rustup on Windows
-->

### 在 Windows 上安装 Rustup

<!--
On Windows, go to *https://www.rust-lang.org/en-US/install.html* and follow the
instructions for installing Rust. At some point in the installation, you’ll
receive a message explaining that you’ll also need the C++ build tools for
Visual Studio 2013 or later. The easiest way to acquire the build tools is to
install Build Tools for Visual Studio 2017 at
*https://www.visualstudio.com/downloads/*. The tools are in the Other Tools and
Frameworks section.
-->

在 Windows 上，请访问 *https://www.rust-lang.org/en-US/install.html* 并按照说明安装 Rust。在安装过程中，你会收到一个信息说明为什么需要安装 Visual Studio 2013 或更新版本的 C++ 构建工具。获取它们最方便的方式是访问 *https://www.visualstudio.com/downloads/* 来安装 Visual Studio 2017，这些工具在“Other Tools and Frameworks”部分。

<!--
The rest of this book uses commands that work in both *cmd.exe* and PowerShell.
If there are specific differences, we’ll explain which to use.
-->

本书之后的部分将使用能够同时在 *cmd.exe* 和 PowerShell 中执行的命令。如果存在具体差异，我们会说明使用哪一个。

<!--
### Custom Installations Without Rustup
-->

### 不用 Rustup 自定义安装

<!--
If you prefer not to use `rustup` for some reason, please see the Rust
installation page at *https://www.rust-lang.org/install.html* for other options.
-->

如果因为某些缘故，你不想用 `rustup` 请参考 *https://www.rust-lang.org/install.html* 上的 Rust 安装页面了解更多选项。

<!--
### Updating and Uninstalling
-->

### 更新和卸载

<!--
After you’ve installed Rust via `rustup`, updating to the latest version is
easy. From your shell, run the following update script:
-->

当你通过 `rustup` 安装了 Rust 之后，很容易更新到最新版本。请在 Shell 中执行如下更新脚本：

```
$ rustup update
```

<!--
To uninstall Rust and `rustup`, from your shell run the following uninstall
script:
-->

要卸载 Rust 和 `rustup`，请在 Shell 中运行如下卸载脚本：

```
$ rustup self uninstall
```

<!--
### Troubleshooting
-->

### 故障排除

<!--
To check whether you have Rust installed correctly, open a shell and enter this
line:
-->

要检查是否正确安装了 Rust，请打开 Shell 并执行如下命令

```
$ rustc --version
```

<!--
You should see the version number, commit hash, and commit date for the latest
stable version that has been released in the following format:
-->

你应能看到已发布的最新稳定版的版本号、提交哈希值和提交日期，显示为如下格式：

```
rustc x.y.z (abcabcabc yyyy-mm-dd)
```

<!--
If you see this information, you have installed Rust successfully! If you don’t
see this information and you’re on Windows, check that Rust is in your `%PATH%`
system variable. If that’s all correct and Rust still isn’t working, there are
a number of places you can get help. The easiest is the #rust IRC channel on
*irc.mozilla.org*, which you can access through Mibbit at
*http://chat.mibbit.com/?server=irc.mozilla.org&channel=%23rust/*. At that
address you can chat with other Rustaceans (a silly nickname we call ourselves)
who can help you out. Other great resources include the Users forum at
*https://users.rust-lang.org/* and Stack Overflow at
*http://stackoverflow.com/questions/tagged/rust/*.
-->

如果出现这些内容，就说明 Rust 安装成功了！如果你并没有看到这些信息，并且使用的是 Windows，请检查 Rust 是否位于 `%PATH%` 系统变量中。如果一切正确但 Rust 仍不能使用，还有许多地方可以求助。最简单的是通过 *irc.mozilla.org* 上的 #rust IRC 频道，可以用 Mibbit（ *http://chat.mibbit.com/?server=irc.mozilla.org&channel=%23rust/* ）来访问它。然后就能和其他 Rustacean（Rust 用户的称号，有自嘲意味）聊天并寻求帮助。其它给力的资源包括用户论坛（ *https://users.rust-lang.org/* ）和 Stack Overflow（ *http://stackoverflow.com/questions/tagged/rust/* ）。

<!--
### Local Documentation
-->

### 本地文档

<!--
The installer also includes a copy of the documentation locally, so you can
read it offline. Run `rustup doc` to open the local documentation in your
browser.
-->

安装程序也自带本地文档，可以离线阅读。请运行 `rustup doc` 在浏览器中查看它。

<!--
Any time a type or function is provided by the standard library and you’re not
sure what it does or how to use it, use the application programming interface
(API) documentation to find out!
-->

任何时候，如果你拿不准标准库中的类型或函数的用途和用法，请参阅应用程序接口（Application Programming Interface，API）文档！

<!--
## Hello, World!
-->

## Hello, World!

<!--
Now that you’ve installed Rust, let’s write your first Rust program. It’s
traditional when learning a new language to write a little program that prints
the text “Hello, world!” to the screen, so we’ll do the same here!
-->

既然安装好了 Rust，我们就来编写第一个 Rust 程序。当学习一门新语言的时候，使用该语言在屏幕上打印 `Hello, world!` 是一项传统，这里我们将沿用这个传统！

<!--
> Note: This book assumes basic familiarity with the command line. Rust makes
> no specific demands about your editing, tooling, or where your code lives, so
> if you prefer to use an integrated development environment (IDE) instead of
> the command line, feel free to use your favorite IDE. Many IDEs now have some
> degree of Rust support; check the IDE’s documentation for details. Recently,
> the Rust team has been focusing on enabling great IDE support, and progress
> has been made rapidly on that front!
-->

> 注意：本书假设你熟悉基本的命令行操作。Rust 对于你的编辑器、工具，以及代码位于何处并没有特定的要求，如果你更倾向于使用集成开发环境（IDE）而非命令行，请尽管使用你喜欢的 IDE。目前很多 IDE 已经不同程度地支持了 Rust，请查看 IDE 文档了解更多细节。最近，Rust 团队已经致力于提供强大的 IDE 支持，而且进展飞速！

<!--
### Creating a Project Directory
-->

### 创建项目目录

<!--
You’ll start by making a directory to store your Rust code. It doesn’t matter
to Rust where your code lives, but for the exercises and projects in this book,
you’ll make a *projects* directory in your home directory to keep all your
projects there.
-->

首先创建一个存放 Rust 代码的目录。Rust 并不关心代码的存放位置，不过对于本书的练习和项目来说，我们建议你在 home 目录中创建 *projects* 目录，并将你的所有项目存放在这里。

<!--
Open a terminal and enter the following commands to make a *projects* directory
and a directory for the “Hello, world!” project within the *projects* directory.
-->

打开终端并输入如下命令创建 *projects*，并在 *projects* 目录中为 Hello, world! 项目再创建一个目录。

<!--
For Linux and macOS, enter this:
-->

对于 Linux 和 macOS，输入：

```
$ mkdir ~/projects
$ cd ~/projects
$ mkdir hello_world
$ cd hello_world
```

<!--
For Windows CMD, enter this:
-->

对于 Windows CMD，输入：

```
> mkdir "%USERPROFILE%\projects"
> cd /d "%USERPROFILE%\projects"
> mkdir hello_world
> cd hello_world
```

<!--
For Windows PowerShell, enter this:
-->

对于 Windows PowerShell，输入：

```
> mkdir $env:USERPROFILE\projects
> cd $env:USERPROFILE\projects
> mkdir hello_world
> cd hello_world
```

<!--
### Writing and Running a Rust Program
-->

### 编写并运行 Rust 程序

<!--
Next, make a new source file and call it *main.rs*. Rust files always end with
the *.rs* extension. If you’re using more than one word in your filename, use
an underscore to separate them. For example, use *hello_world.rs* rather than
*helloworld.rs*.
-->

接下来，新建一个源文件，命名为 *main.rs*。Rust 源文件总是以 *.rs* 扩展名结尾。如果文件名包含多个单词，使用下划线分隔它们。例如命名为 *hello_world.rs*，而非 *helloworld.rs*。

<!--
Now open the *main.rs* file you just created, and enter the code in Listing 1-1.
-->

现在打开刚创建的 *main.rs* 文件，输入示例 1-1 中的代码。

<!--
Filename: main.rs
-->

文件名：main.rs

```
fn main() {
    println!("Hello, world!");
}
```

<!--
Listing 1-1: A program that prints “Hello, world!”
-->

示例 1-1: 一个打印 `Hello, world!` 的程序

<!--
Save the file, and go back to your terminal window. On Linux or macOS, enter
the following commands to compile and run the file:
-->


保存文件，并回到终端窗口。在 Linux 或 macOS 上，输入如下命令，编译并运行该文件：

```
$ rustc main.rs
$ ./main
Hello, world!
```

<!--
On Windows, enter the command `.\main.exe` instead of `./main`.
-->

在 Windows 上，输入命令 `.\main.exe` 而非 `./main`：

```
> rustc main.rs
> .\main.exe
Hello, world!
```

<!--
Regardless of your operating system, the string `Hello, world!` should print to
the terminal. If you don’t see this output, refer back to the “Troubleshooting”
section for ways to get help.
-->

无论使用何种操作系统，终端应该都会打印字符串 `Hello, world!`。如果没有看到这些输出，回到 “故障排除” 部分查看寻求帮助的方法。

<!--
If you did see `Hello, world!` printed, congratulations! You’ve officially
written a Rust program. That makes you a Rust programmer! Welcome!
-->

如果 `Hello, world!` 出现了，恭喜你！你已经正式编写了一个 Rust 程序。现在你成为了一名 Rust 程序员，欢迎！

<!--
### Anatomy of a Rust Program
-->

### 分析 Rust 程序

<!--
Let’s review in detail what just happened in your “Hello, world!” program.
Here’s the first piece of the puzzle:
-->

现在，让我们再仔细看看 Hello, world! 程序中到底发生了什么。这是第一块拼图：

```
fn main() {

}
```

<!--
These lines define a *function* in Rust. The `main` function is special: it is
always the first code that runs in every executable Rust program. The first
line declares a function named `main` that has no parameters and returns
nothing. If there were parameters, they would go inside the parentheses, `(`
and `)`.
-->

这几行定义了一个 Rust *函数*。`main` 函数是一个特殊的函数：在可执行的 Rust 程序中，它总是最先运行的代码。第一行代码声明了一个名为 `main` 它没有参数也没有返回值。如果有参数的话，它们的名称应该出现在小括号 `(` 和 `)` 中。

<!--
Also, note that the function body is wrapped in curly brackets, `{` and `}`.
Rust requires these around all function bodies. It’s good style to place the
opening curly bracket on the same line as the function declaration, adding one
space in between.
-->

还须注意，函数体被括在花括号 `{` 和 `}` 中。Rust 要求所有函数体都要用花括号括住。一般来说，将左花括号与函数声明置于同一行并以空格分隔，是一种良好的代码风格。

<!--
At the time of this writing, an automatic formatter tool called `rustfmt` is
under development. If you want to stick to a standard style across Rust
projects, `rustfmt` will format your code in a particular style. The Rust team
plans to eventually include it with the standard Rust distribution, like
`rustc`. So depending on when you read this book, it might already be installed
on your computer! Check the online documentation for more details.
-->

在编写本书的时候，名为 `rustfmt` 的自动格式化工具正在开发中。如果你希望在 Rust 项目中保持一种标准风格，`rustfmt` 会将代码格式化为特定的风格。Rust 团队计划最终将该工具包含在标准 Rust 发行版中，就像 `rustc`。所以当你阅读本书的时候，它可能已经安装到你的电脑中了！查看在线文档以了解更多详情。

<!--
Inside the `main` function is the following code:
-->

`main` 函数中的代码如下：

```
    println!("Hello, world!");
```

<!--
This line does all the work in this little program: it prints text to the
screen. There are four important details to notice here. First, Rust style is
to indent with four spaces, not a tab.
-->

这行代码完成了这个小程序的所有工作：在屏幕上打印文本。这里有四个重要的细节需要注意。第一，Rust 的缩进风格使用 4 个空格而非 1 个制表符（Tab）。

<!--
Second, `println!` calls a Rust *macro*. If it called a function instead, it
would be entered as `println` (without the `!`). We’ll discuss Rust macros in
more detail in Appendix D. For now, you just need to know that using a `!`
means that you’re calling a macro instead of a normal function.
-->

第二，`println!` 调用了一个 Rust *宏（Macro）*。如果是调用函数，则应输入`println`（没有 `!`）。我们将在附录 D 中详细讨论宏。现在你只需记住，当看到符号 `!` 的时候，就意味着调用的是宏而不是普通函数。

<!--
Third, you see the `"Hello, world!"` *string*. We pass this string as an
argument to `println!`, and the string is printed to the screen.
-->

第三，`"Hello, world!"` 是一个*字符串*。我们把这个字符串作为参数传入 `println!` 中，字符串将被打印到屏幕上。

<!--
Fourth, we end the line with a semicolon `;`, which indicates that this
expression is over and the next one is ready to begin. Most lines of Rust code
end with a semicolon.
-->

第四，该行以分号 `;` 结尾，这代表当前表达式的结束和下一个表达式的开始。大部分 Rust 代码行均以分号结尾。

<!--
### Compiling and Running Are Separate Steps
-->

### 编译和运行是彼此独立的步骤

<!--
You’ve just run a newly created program, so let’s examine each step in the
process.
-->

你刚刚运行了一个新创建的程序，那么让我们检查此过程中的每一个步骤。

<!--
Before running a Rust program, you must compile it using the Rust compiler by
entering the `rustc` command and passing it the name of your source file, like
this:
-->

在运行 Rust 程序之前，我们必须先使用 Rust 编编译来编译它，即输入 `rustc` 命令并传入源文件的名称，如下：

```
$ rustc main.rs
```

<!--
If you have a C or C++ background, you’ll notice that this is similar to `gcc`
or `clang`. After compiling successfully, Rust outputs a binary executable.
-->

如果你有 C 或 C++ 的背景，就会发现这与 `gcc` 和 `clang` 类似。编译成功后，Rust 会输出一个二进制的可执行文件。

<!--
On Linux, macOS, and PowerShell on Windows, you can see the executable by
entering the `ls` command in your shell as follows:
-->

在 Linux、macOS 或 Windows 的 PowerShell 中，你只需在 Shell 中输入 `ls` 命令就能看见这个可执行文件，如下：

```
$ ls
main  main.rs
```

<!--
With CMD on Windows, you would enter the following:
-->

在 Windows 的 CMD 中，则需输入如下内容：

<!--
```
> dir /B %= the /B option says to only show the file names =%
main.exe
main.pdb
main.rs
```
-->

```
> dir /B %= /B 选项表示只显示文件名 =%
main.exe
main.pdb
main.rs
```

<!--
This shows the source code file with the *.rs* extension, the executable file
(*main.exe* on Windows, but *main* on all other platforms), and, when using
CMD, a file containing debugging information with the *.pdb* extension. From
here, you run the *main* or *main.exe* file, like this:
-->

这会列出扩展名为 `.rs` 的源文件、可执行文件（在 Windows 下是 *main.exe*，其它平台下是 *main*），以及当使用 CMD 时会有一个包含调试信息、扩展名为 *.pdb* 的文件。从这里开始运行 *main* 或 *main.exe* 文件，如下：

<!-- ```
$ ./main # or .\main.exe on Windows
``` -->

```
$ ./main # Windows 下则是 .\main.exe
```

<!--
If *main.rs* was your “Hello, world!” program, this line would print `Hello,
world!` to your terminal.
-->

如果 *main.rs* 是上文所述的“Hello, world!”程序，那么这行命令将会在终端中打印 `Hello, world!`。

<!--
If you’re more familiar with a dynamic language, such as Ruby, Python, or
JavaScript, you might not be used to compiling and running a program as
separate steps. Rust is an *ahead-of-time compiled* language, meaning you can
compile a program, give the executable to someone else, and they can run it
even without having Rust installed. If you give someone a *.rb*, *.py*, or
*.js* file, they need to have a Ruby, Python, or JavaScript implementation
installed (respectively). But in those languages, you only need one command to
compile and run your program. Everything is a trade-off in language design.
-->

如果你更熟悉动态语言，如 Ruby、Python 或 JavaScript，那么可能不习惯将编译和运行分为两个单独的步骤。Rust 是一种*预编译（Ahead-of-Time，AoT）*的语言，这意味着你可以先编译好程序，然后将可执行文件给其他人，他们甚至不需要安装 Rust 就可以运行。如果你给他人一个 *.rb*、*.py* 或 *.js* 文件，那么他们需要先（分别）安装 Ruby、Python 或 JavaScript 的实现。不过在这些语言中，只需要一句命令就可以编译和运行程序。这一切都是语言设计上的权衡取舍。

<!--
Just compiling with `rustc` is fine for simple programs, but as your project
grows, you’ll want to manage all the options and make it easy to share your
code. Next, we’ll introduce you to the Cargo tool, which will help you write
real-world Rust programs.
-->

只用 `rustc` 编译简单程序是没问题的，不过随着项目的增长，你可能需要管理项目的方方面面，并让代码易于分享。接下来，我们要介绍一个名为 Cargo 的工具，它会帮助你编写真实世界中的 Rust 程序。

<!--
## Hello, Cargo!
-->

## Hello, Cargo!

<!--
Cargo is Rust’s build system and package manager. Most Rustaceans use this tool
to manage their Rust projects because Cargo handles a lot of tasks for you,
such as building your code, downloading the libraries your code depends on, and
building those libraries. (We call libraries your code needs *dependencies*.)
-->

Cargo 是 Rust 的构建系统和包管理器。大多数 Rustacean 们使用 Cargo 来管理他们的 Rust 项目，因为它可以为你处理很多任务，比如构建代码、下载依赖库并编译这些库。（我们把代码所需要的库叫做*依赖（dependencies）*）。

<!--
The simplest Rust programs, like the one we’ve written so far, don’t have any
dependencies. So if we had built the “Hello, world!” project with Cargo, it
would only use the part of Cargo that handles building your code. As you write
more complex Rust programs, you’ll add dependencies, and if you start a project
using Cargo, adding dependencies will be much easier to do.
-->

最简单的 Rust 程序，比如我们刚刚编写的，没有任何依赖。所以如果使用 Cargo 来构建 Hello, world! 项目，将只会用到 Cargo 构建代码的那部分功能。随着编写的 Rust 程序更加复杂，你会添加依赖。如果你一开始就使用 Cargo 的话，添加依赖将会变得简单许多。

<!--
Because the vast majority of Rust projects use Cargo, the rest of this book
assumes that you’re using Cargo too. Cargo comes installed with Rust if you
used the official installers discussed in the “Installation” section. If you
installed Rust through some other means, check whether Cargo is installed by
entering the following into your terminal:
-->

由于绝大多数 Rust 项目都使用 Cargo，本书接下来的部分会假设你也使用 Cargo。“安装”一节中介绍的官方安装包自带了 Cargo。如果要通过其它方式安装，可在终端输入如下命令检查是否安装了 Cargo：

```
$ cargo --version
```

<!--
If you see a version number, you have it! If you see an error, such as `command
not found`, look at the documentation for your method of installation to
determine how to install Cargo separately.
-->

如果你看到了版本号，说明已安装！如果看到了类似 `command not found` 的错误，你应该查看相应的安装文档以确定如何单独安装 Cargo。

<!--
### Creating a Project with Cargo
-->

### 使用 Cargo 创建项目

<!--
Let’s create a new project using Cargo and look at how it differs from our
original “Hello, world!” project. Navigate back to your *projects* directory.
Then, on any operating system, run the following:
-->

我们使用 Cargo 创建一个新项目，然后看看与上面的 Hello, world! 项目有什么不同。回到 *projects* 目录。接着，可在任何操作系统下运行以下命令：

```
$ cargo new hello_cargo --bin
$ cd hello_cargo
```

<!--
The first command creates a new binary executable called *hello_cargo*. The
`--bin` argument passed to `cargo new` makes an executable application (often
just called a *binary*) as opposed to a library. We’ve named our project
*hello_cargo*, and Cargo creates its files in a directory of the same name.
-->

第一行命令新建了名为 *hello_cargo* 的二进制可执行程序。为 `cargo new` 传入 `--bin` 参数会生成一个可执行程序（通常就叫做*二进制文件（binary）*），而非一个库。项目被命名为 *hello_cargo*，同时 Cargo 在一个同名目录中创建项目文件。

<!--
Go into the *hello_cargo* directory and list the files. You’ll see that Cargo
has generated two files and one directory for us: a *Cargo.toml* file and a
*src* directory with a *main.rs* file inside. It has also initialized a new Git
repository along with a *.gitignore* file.
-->

进入 *hello_cargo* 目录并列出文件。你会看到 Cargo 生成了两个文件和一个目录：一个 *Cargo.toml* 文件，一个 *src* 目录，以及位于 *src* 目录中的 *main.rs* 文件。它也在 *hello_cargo* 目录初始化了一个 *git* 仓库，以及一个 *.gitignore* 文件。

<!--
> Note: Git is a common version control system. You can change `cargo new` to
> use  a different version control system or no version control system by using
> the `--vcs` flag. Run `cargo new --help` to see the available options.
-->

> 注：Git 是一个常用的版本控制系统（Version Control System，VCS）。可以通过 `--vcs` 参数让 `cargo new` 切换到其它版本控制系统（VCS）上，或者不使用 VCS。运行 `cargo new --help` 查看可用的选项。

<!--
Open *Cargo.toml* in your text editor of choice. It should look similar to the
code in Listing 1-2.
-->

请选用文本编辑器打开 `Cargo.toml` 文件。它看起来如示例 1-2 所示：

<!--
Filename: Cargo.toml
-->

文件名：Cargo.toml

```
[package]
name = "hello_cargo"
version = "0.1.0"
authors = ["Your Name <you@example.com>"]
```

<!--
Listing 1-2: Contents of *Cargo.toml* generated by `cargo new`
-->

示例 1-2：`cargo new` 命令生成的 `Cargo.toml` 的内容

<!--
This file is in the *TOML* (Tom’s Obvious, Minimal Language) format, which is
Cargo’s configuration format.
-->

此文件使用 *TOML（Tom's Obvious, Minimal Language）* 格式，这是 Cargo 配置文件的格式。

<!--
The first line, `[package]`, is a section heading that indicates that the
following statements are configuring a package. As we add more information to
this file, we’ll add other sections.
-->

第一行的 [package] 是一个片段（Section）标题，表明下面的语句用来配置一个包。随着在这个文件增加更多的信息，我们还将增加其它片段。

<!--
The next three lines set the configuration information Cargo needs to compile
your program: the name, the version, and who wrote it. Cargo gets your name and
email information from your environment, so if that information is not correct,
fix the information now and then save the file.
-->

接下来的三行设置了 Cargo 编译程序所需的配置：项目的名称、版本和作者。Cargo 从环境中获取你的名字和 email 信息，所以如果这些信息不正确，请修改并保存此文件。

<!--
The last line, `[dependencies]`, is the start of a section for you to list any
of your project’s dependencies. In Rust, packages of code are referred to as
*crates*. We won’t need any other crates for this project, but we will in the
first project in Chapter 2, so we’ll use this dependencies section then.
-->

最后一行的 [dependencies] 是罗列项目依赖的片段。在 Rust 中，代码包被称为 *crates*。这个项目并不需要其他的 crate，不过在第二章的第一个项目中会用到依赖，那时会用得上这个片段。

<!--
Now open *src/main.rs* and take a look:
-->

现在打开 *src/main.rs* 看一下：

<!--
Filename: src/main.rs
-->

文件名：src/main.rs

```
fn main() {
    println!("Hello, world!");
}
```

<!--
Cargo has generated a “Hello, world!” program for you, just like the one we
wrote in Listing 1-1! So far, the differences between our previous project and
the project Cargo generates are that Cargo placed the code in the *src*
directory, and we have a *Cargo.toml* configuration file in the top directory.
-->

Cargo 为你生成了一个 Hello World! 程序，正如我们之前编写的示例 1-1！目前为止，之前项目与 Cargo 生成项目的区别是 Cargo 将代码放在 *src* 目录，同时项目根目录包含一个 *Cargo.toml* 配置文件。

<!--
Cargo expects your source files to live inside the *src* directory. The
top-level project directory is just for README files, license information,
configuration files, and anything else not related to your code. Using Cargo
helps you organize your projects. There’s a place for everything, and
everything is in its place.
-->

Cargo 期望源文件存放在 *src* 目录中。项目根目录只存放 README、license 信息、配置文件和其他跟代码无关的文件。使用 Cargo 能够帮助你保持项目干净整洁，一切井井有条。

<!--
If you started a project that doesn’t use Cargo, as we did with our project in
the *hello_world* directory, you can convert it to a project that does use
Cargo. Move the project code into the *src* directory and create an appropriate
*Cargo.toml* file.
-->

如果你没有用 Cargo 开始项目，比如我们之前创建的 Hello,world! 项目，那么可以将其转化为一个 Cargo 项目。将代码放入 src 目录，并创建一个合适的 Cargo.toml 文件即可。

<!--
### Building and Running a Cargo Project
-->

### 构建并运行 Cargo 项目

<!--
Now let’s look at the difference when we build and run the “Hello, world!”
program with Cargo! From your *hello_cargo* directory, build your project by
entering the following command:
-->

现在让我们看看通过 Cargo 构建和运行 Hello, world! 程序有什么不同！在 *hello_cargo* 目录下，输入下面的命令来构建项目：

```
$ cargo build
   Compiling hello_cargo v0.1.0 (file:///projects/hello_cargo)
    Finished dev [unoptimized + debuginfo] target(s) in 2.85 secs
```

<!--
This command creates an executable file in *target/debug/hello_cargo* (or
*target\debug\hello_cargo.exe* on Windows) rather than in your current
directory. You can run the executable with this command:
-->

该命令会创建一个可执行文件 `target/debug/hello_cargo`（在 Windows 上是 `target\debug\hello_cargo.exe`），而非放在当前目录下。可通过此命令运行可执行文件：

<!--
```
$ ./target/debug/hello_cargo # or .\target\debug\hello_cargo.exe on Windows
Hello, world!
```
-->

```
$ ./target/debug/hello_cargo # 在 Windows 上则为 .\target\debug\hello_cargo.exe
Hello, world!
```

<!--
If all goes well, `Hello, world!` should print to the terminal. Running `cargo
build` for the first time also causes Cargo to create a new file at the top
level: *Cargo.lock*. This file keeps track of the exact versions of
dependencies in your project. This project doesn’t have dependencies, so the
file is a bit sparse. You won’t ever need to change this file manually; Cargo
manages its contents for you.
-->

如果一切顺利，终端上应该会打印出 `Hello, world!`。首次运行 `cargo build` 时，Cargo 还会在项目根目录下创建一个新文件：*Cargo.lock*。该文件记录了项目依赖的实际版本。这个项目并没有依赖，所以其内容较少。你自己永远也不需要碰这个文件，让 Cargo 处理它就行了。

<!--
We just built a project with `cargo build` and ran it with
`./target/debug/hello_cargo`, but we can also use `cargo run` to compile the
code and then run the resulting executable all in one command:
-->

我们刚刚用 `cargo build` 构建了项目，并使用 `./target/debug/hello_cargo` 运行了程序。不过我们也可以只用 `cargo run` 一条命令就同时编译并运行生成的可执行文件：

```
$ cargo run
    Finished dev [unoptimized + debuginfo] target(s) in 0.0 secs
     Running `target/debug/hello_cargo`
Hello, world!
```

<!--
Notice that this time we didn’t see output indicating that Cargo was compiling
`hello_cargo`. Cargo figured out that the files hadn’t changed, so it just ran
the binary. If you had modified your source code, Cargo would have rebuilt the
project before running it, and you would have seen this output:
-->

注意这一次并没有出现表明 Cargo 正在编译 `hello_cargo` 的输出。Cargo 发现文件并没有被改变，就直接运行了二进制文件。如果修改了源文件的话，Cargo 会在运行之前重新构建项目，并会出现像这样的输出：

```
$ cargo run
   Compiling hello_cargo v0.1.0 (file:///projects/hello_cargo)
    Finished dev [unoptimized + debuginfo] target(s) in 0.33 secs
     Running `target/debug/hello_cargo`
Hello, world!
```

<!--
Cargo also provides a command called `cargo check`. This command quickly checks
your code to make sure it compiles but doesn’t produce an executable:
-->

Cargo 还提供了一个叫 `cargo check` 的命令。该命令能够快速检查代码确保其可以编译，但并不产生可执行文件：

```
$ cargo check
   Compiling hello_cargo v0.1.0 (file:///projects/hello_cargo)
    Finished dev [unoptimized + debuginfo] target(s) in 0.32 secs
```

<!--
Why would you not want an executable? Often, `cargo check` is much faster than
`cargo build`, because it skips the step of producing an executable. If you’re
continually checking your work while writing the code, using `cargo check` will
speed up the process! As such, many Rustaceans run `cargo check` periodically
as they write their program to make sure it compiles. Then they run `cargo
build` when they’re ready to use the executable.
-->

为什么你会不需要可执行文件呢？通常 `cargo check` 要比 `cargo build` 快得多，因为它省略了生成可执行文件的步骤。如果编写代码时持续的进行检查，`cargo check` 会加速开发！为此很多 Rustaceans 编写代码时定期运行 `cargo check` 确保它们可以编译。当准备好使用可执行文件时才运行 `cargo build`。

<!--
To recap what we’ve learned so far about Cargo:
-->

我们来回顾下已经学过的 Cargo 内容：

<!--
* We can build a project using `cargo build` or `cargo check`.
* We can build and run a project in one step using `cargo run`.
* Instead of the result of the build being saved in the same directory as our
code, Cargo stores it in the *target/debug* directory.
-->

* 可以使用 `cargo build` 或 `cargo check` 构建项目。
* 可以使用 `cargo run` 一步构建并运行项目。
* 有别于将构建结果放在与源码相同的目录，Cargo 会将其放到 `target/debug` 目录。

<!--
An additional advantage of using Cargo is that the commands are the same no
matter which operating system you’re working on. So, at this point, we’ll no
longer provide specific instructions for Linux and macOS versus Windows.
-->

使用 Cargo 的一个额外的优点是，不管你使用什么操作系统，其命令都是一样的。所以从此以后本书将不再为 Linux 和 macOS 以及 Windows 提供相应的命令。

<!--
### Building for Release
-->

### 发布构建

<!--
When your project is finally ready for release, you can use `cargo build
--release` to compile it with optimizations. This command will create an
executable in *target/release* instead of *target/debug*. The optimizations
make your Rust code run faster, but turning them on lengthens the time it takes
for your program to compile. This is why there are two different profiles: one
for development when you want to rebuild quickly and often, and another for
building the final program you’ll give to a user that won’t be rebuilt
repeatedly and that will run as fast as possible. If you’re benchmarking your
code’s running time, be sure to run `cargo build --release` and benchmark with
the executable in *target/release*.
-->

当项目最终准备好发布时，可使用 `cargo build --release` 来优化编译项目。这会在 *target/release* 而非 *target/debug* 下生成可执行文件。这些优化可以让 Rust 代码运行的更快，不过启用这些优化也需要消耗更长的编译时间。这也就是为什么会有两种不同的配置：一种是为了开发，你需要经常快速重新构建；另一种是为用户构建最终程序，它们不会经常重新构建，并且希望程序运行得越快越好。如果你在测试代码的运行时间，请确保运行 `cargo build --release` 并使用 *target/release* 下的可执行文件进行测试。

<!--
### Cargo as Convention
-->

### 把 Cargo 当作习惯

<!--
With simple projects, Cargo doesn’t provide a lot of value over just using
`rustc`, but it will prove its worth as your programs become more intricate.
With complex projects composed of multiple crates, it’s much easier to let
Cargo coordinate the build.
-->

对于简单项目，Cargo 并不比 `rustc` 更有优势，不过随着开发的深入，终将证明其价值。对于拥有多个 crate 的复杂项目，交给 Cargo 来协调构建会简单得多。

<!--
Even though the `hello_cargo` project is simple, it now uses much of the real
tooling you’ll use in the rest of your Rust career. In fact, to work on any
existing projects, you can use the following commands to check out the code
using Git, change to that project’s directory, and build:
-->

即便 `hello_cargo` 项目十分简单，它现在也使用了很多在你之后的 Rust 生涯将会用到的实用工具。其实，要在任何已存在的项目上工作时，可以使用如下命令通过 Git 检出代码，进入到该项目目录下构建：

```
$ git clone someurl.com/someproject
$ cd someproject
$ cargo build
```

<!--
For more information about Cargo, check out its documentation at
*https://doc.rust-lang.org/cargo/*.
-->

关于更多 Cargo 的信息，请访问 *https://doc.rust-lang.org/cargo/* 查阅文档。
.

<!--
## Summary
-->

## 总结

<!--
You’re already off to a great start on your Rust journey! In this chapter,
you’ve learned how to:
-->

你已经踏上了 Rust 之旅！在本章中，你学习了如何：

<!--
* Install the latest stable version of Rust using `rustup`
* Update to a newer Rust version
* Open locally installed documentation
* Write and run a “Hello, world!” program using `rustc` directly
* Create and run a new project using the conventions of Cargo
-->

使用 `rustup` 安装最新稳定版的 Rust
更新到新版的 Rust
打开本地安装的文档
直接通过 `rustc` 编写并运行 Hello, world! 程序
使用 Cargo 创建并运行新项目

<!--
This is a great time to build a more substantial program to get used to reading
and writing Rust code. So, in the next chapter, we’ll build a guessing game
program. If you would rather start by learning how common programming concepts
work in Rust, see Chapter 3, and then return to Chapter 2.
-->

是时候通过构建更真实的程序来熟悉读写 Rust 代码了。所以在下一章，我们会构建一个猜数游戏程序。如果你更愿意从学习 Rust 常用的编程概念开始，请阅读第三章，之后再回到第二章来。
