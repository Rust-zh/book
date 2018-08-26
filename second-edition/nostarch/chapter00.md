
[TOC]

<!--
# Introduction
-->

# 引言

<!--
Welcome to *The Rust Programming Language*, an introductory book about Rust.
-->

欢迎阅读*《Rust 程序设计语言》*，这是一本介绍 Rust 的书。

<!--
The Rust programming language helps you write faster, more reliable software.
High-level ergonomics and low-level control are often at odds in programming
language design; Rust challenges that conflict. Through balancing powerful
technical capacity and a great developer experience, Rust gives you the option
to control low-level details (such as memory usage) without all the hassle
traditionally associated with such control.
-->

Rust 程序设计语言能帮你编写出更快、更可靠的软件。在其它编程语言的设计中，上层工程学和底层控制往往无法兼得，而 Rust 则试图挑战这种冲突。通过权衡强大的技术能力与优秀的开发体验，Rust 允许你控制底层细节（比如内存使用），避免受过去做此类控制所经历的烦恼。

<!--
## Who Rust Is For
-->

## Rust 面向的用户

<!--
Rust is ideal for many people for a variety of reasons. Let’s look at a few of
the most important groups.
-->

Rust 对很多人来说都是理想的语言，原因有很多。我们来讨论几个最重要的群体。

<!--
### Teams of Developers
-->

### 开发者团队

<!--
Rust is proving to be a productive tool for collaborating among large teams of
developers with varying levels of systems programming knowledge. Low-level code
is prone to a variety of subtle bugs, which in most other languages can only be
caught through extensive testing and careful code review by experienced
developers. In Rust, the compiler plays a gatekeeper role by refusing to
compile code with these elusive bugs, including concurrency bugs. By working
alongside the compiler, the team can spend more time focusing on the program’s
logic rather than chasing down bugs.
-->
Rust 被证明是一种极具生产力的工具，它很适合大型的、拥有不同层次系统编程知识的开发团队进行互相协作。底层代码中容易出现大量隐晦的 bug，在其它编程语言中，这些 bug 只能通过大量的测试和经验丰富的开发者细心的代码审核来捕获。在 Rust 中，编译器充当了守门员的角色，它拒绝编译存在隐晦 bug 的代码，包括并发的 bug。通过与编译器的相互配合，团队可以将更多的时间用在专注程序逻辑，而非追踪 bug 上来。

<!--
Rust also brings contemporary developer tools to the systems programming world:

* Cargo, the included dependency manager and build tool, makes adding,
  compiling, and managing dependencies painless and consistent across the Rust
  ecosystem.
* Rustfmt ensures a consistent coding style across developers.
* The Rust Language Server powers Integrated Development Environment (IDE)
  integration for code completion and inline error messages.
-->

Rust 还将现代的开发者工具带到了系统编程的世界中：

* Cargo，内置的依赖管理工具，它能轻松地添加、编译和管理依赖，并在 Rust 生态系统中保持一致性。
* Rustfmt 能够确保开发者遵循一致的代码风格。
* Rust 语言服务器（Language Server）为集成开发环境（IDE）提供了强大的代码补全和内联的错误信息功能。

<!--
By using these and other tools in the Rust ecosystem, developers can be
productive while writing systems-level code.
-->

通过使用 Rust 生态系统中的各种工具，开发者可以在编写系统层代码时保持高生产力。

<!--
### Students
-->

### 学生

<!--
Rust is for students and those who are interested in learning about systems
concepts. Using Rust, many people have learned about topics like operating
systems development. The community is very welcoming and happy to answer
student questions. Through efforts such as this book, the Rust teams want to
make systems concepts more accessible to more people, especially those new to
programming.
-->

Rust 适用于学生或任何对操作系统概念感兴趣的人。通过 Rust，很多人已经了解了像操作系统开发这样的主题。社区非常欢迎并乐于解答学生们的问题。通过类似于本书这样的努力，Rust 团队希望更多人，特别是编程的新手来了解操作系统的概念。

<!--
### Companies
-->

### 公司

<!--
Hundreds of companies, large and small, use Rust in production for a variety of
tasks. Those tasks include command line tools, web services, DevOps tooling,
embedded devices, audio and video analysis and transcoding, cryptocurrencies,
bioinformatics, search engines, internet of things applications, machine
learning, and even major parts of the Firefox web browser.
-->

无论规模大小，数以百计的公司正在将 Rust 用于生产环境中的多种任务。这些任务包括命令行工具、Web 服务、DevOps 工具、嵌入式设备、音视频分析与转码、加密货币（
Cryptocurrency）、生物信息学（Bioinformatics）、搜索引擎、物联网（Internet of Things, IoT）程序、机器学习，甚至还包括 Firefox 浏览器的大部分模块。

<!--
### Open Source Developers
-->

### 开源开发者

<!--
Rust is for people who want to build the Rust programming language, community,
developer tools, and libraries. We’d love to have you contribute to the Rust
language.
-->

Rust 适用于希望构建 Rust 编程语言、社区、开发工具和库的开发者。我们非常期待你为 Rust 语言做出贡献。

<!--
### People Who Value Speed and Stability
-->

### 重视速度和稳定性的开发者

<!--
Rust is for people who crave speed and stability in a language. By speed, we
mean the speed of the programs that you can create with Rust and the speed at
which Rust lets you write them. The Rust compiler’s checks ensure stability
through feature additions and refactoring as opposed to brittle legacy code in
languages without these checks that developers are afraid to modify. By
striving for zero-cost abstractions, higher-level features that compile to
lower-level code as fast as code written manually, Rust endeavors to make safe
code be fast code as well.
-->

Rust 适用于在编程语言中追求速度和稳定性的开发者。所谓速度，即你用 Rust 开发出的程序的运行速度，以及你用 Rust 编写程序的速度。Rust 的编译器检查确保了增加功能和重构代码时的稳定性。这与缺少这些检查的语言形成鲜明对比，开发者通常害怕修改那些脆弱的遗留代码。通过力求零开销抽象（Zero-Cost Abstraction），高级的特性所编译成的底层代码与手写的一样快，Rust 致力于让安全的代码也同样快速。

<!--
Although we’ve not provided a complete list of everyone the Rust language hopes
to support, those we have mentioned are some of the biggest stakeholders.
Overall, Rust’s greatest ambition is to eliminate the dichotomy of the
trade-offs that programmers have accepted for decades: safety *and*
productivity, speed *and* ergonomics. Give Rust a try, and see if its choices
work for you.
-->

Rust 语言希望能支持更多用户，这里提及的只是最大的利益相关者。总的来说，Rust 最大的抱负是消除数十年来程序员不得不做的权衡：安全*与*生产力、速度*与*工程学。请尝试一下 Rust，看看它的选择是否适合你。

<!--
## Who This Book Is For
-->

## 本书面向的读者

<!--
This book assumes that you’ve written code in another programming language but
doesn’t make any assumptions about which one. We’ve tried to make the material
broadly accessible to those from a wide variety of programming backgrounds. We
don’t spend a lot of time talking about what programming *is* or how to think
about it. If you’re entirely new to programming, you would be better served by
reading a book that specifically provides an introduction to programming.
-->

本书假定你使用其它编程语言编写过代码，但并不假设你使用何种语言。我们尝试让这些材料能够广泛地适用于具有多种不同编程背景的开发者。我们不会花太多时间来讨论编程*是什么*或者如何理解它。如果你是个编程新手，那么最好先阅读专门介绍编程的书籍。

<!--
## How to Use This Book
-->

## 如何阅读本书

<!--
In general, this book assumes that you’re reading it in sequence from front to
back. Later chapters build on concepts in earlier chapters, and earlier
chapters might not delve into details on a topic; we typically revisit the
topic in a later chapter.
-->

一般而言，本书假定你会从头读到尾。后面的章节建立在之前章节概念的基础上，而之前的章节可能不会深入讨论某个主题的细节，通常后面的章节会再次讨论这些主题。

<!--
You’ll find two kinds of chapters in this book: concept chapters and project
chapters. In concept chapters, you’ll learn about an aspect of Rust. In project
chapters, we’ll build small programs together, applying what you’ve learned so
far. Chapters 2, 12, and 20 are project chapters; the rest are concept chapters.
-->

你会在本书中看到两类章节：概念章节和项目章节。在概念章节中，我们会学习 Rust 的某个方面；而在项目章节中，我们会运用之前所学的知识来一同构建小程序。第二、第十二和第二十章是项目章节，其余则都是概念章节。

<!-- 本段与出版的书中不一致
Additionally, Chapter 2 is a hands-on introduction to the Rust language. We’ll
cover concepts at a high level, and later chapters will provide additional
detail. If you want to get your hands dirty right away, Chapter 2 is the one
for that. At first, you might even want to skip Chapter 3, which covers Rust
features similar to other programming language features, and head straight to
Chapter 4 to learn about Rust’s ownership system. However, if you’re a
particularly meticulous learner who prefers to learn every detail before moving
onto the next, you might want to skip Chapter 2 and go straight to Chapter 3,
returning to Chapter 2 when you’d like to work on a project applying those
details.
-->

<!-- 出版内容
Chapter 1 explains how to install Rust, how to write a Hello, World!
program, and how to use Cargo, Rust’s package manager and build tool.
Chapter 2 is a hands-on introduction to the Rust language. Here we cover
concepts at a high level, and later chapters will provide additional detail. If
you want to get your hands dirty right away, Chapter 2 is the place for that.
At first, you might even want to skip Chapter 3, which covers Rust features
similar to those of other programming languages, and head straight to
Chapter 4 to learn about Rust’s ownership system. However, if you’re a
particularly meticulous learner who prefers to learn every detail before moving
on to the next, you might want to skip Chapter 2 and go straight to Chapter 3,
returning to Chapter 2 when you’d like to work on a project applying the
details you’ve learned.
-->

第一章介绍了如何安装 Rust，如何编写 Hello, World! 程序，以及如何使用 Rust 的包管理器和构建工具 Cargo。第二章是 Rust 语言的实战介绍。我们会在宏观上介绍一些概念，在稍后章节会详细介绍。如果你希望立刻就动手实践一下，第二章正好适合你。开始阅读时，你甚至可能希望略过第三章，它介绍了 Rust 与其它编程语言中类似的功能，然后直奔第四章学习 Rust 的所有权系统。然而，如果你是特别重视细节的学习者，倾向于在继续之前学习每一个细节，那么你可能希望略过第二章，直奔第三章，在想要构建项目来实践这些细节时再回过头来阅读第二章。

<!--
Chapter 5 discusses structs and methods, and Chapter 6 covers enums, `match`
expressions, and the `if let` control flow construct. You’ll use structs and
enums to make custom types in Rust.
-->

第五章讨论了结构体和方法，第六章介绍了枚举、`match` 表达式和 `if let` 控制流结构。在 Rust 中，你将会在 Rust 中使用结构体和枚举来创建自定义类型。

<!--
In Chapter 7, you’ll learn about Rust’s module system and about privacy rules
for organizing your code and its public Application Programming Interface
(API). Chapter 8 discusses some common collection data structures that the
standard library provides, such as vectors, strings, and hash maps. Chapter 9
explores Rust’s error handling philosophy and techniques.
-->

在第七章中，你会学习 Rust 的模块系统和私有性规则来组织代码及其公有应用程序接口（Application Programming Interface, API）。第八章讨论了一些标准库中提供的通用集合数据结构，比如向量（Vector）、字符串和散列映射（Hash Map）。第九章则探索了 Rust 的错误处理哲学和技术。

<!--
Chapter 10 digs into generics, traits, and lifetimes, which give you the power
to define code that applies to multiple types. Chapter 11 is all about testing,
which is still necessary even with Rust’s safety guarantees to ensure your
program’s logic is correct. In Chapter 12, we’ll build our own implementation
of a subset of functionality from the `grep` command line tool that searches
for text within files. For this, we’ll use many of the concepts we discussed in
the previous chapters.
-->

第十章深入介绍了泛型、特质（Trait）和生命周期，它们提供了定义出适用于多种类型的代码的能力。第十一章介绍了测试，即便 Rust 有安全性保证，也需要通过测试来确保程序逻辑的正确性。在第十二章中，我们构建了自己的命令行工具 `grep` 中部分功能的实现，它用于在文件中搜索文本。为此，我们需要利用之前章节中讨论过的很多概念。

<!--
Chapter 13 explores closures and iterators: features of Rust that come from
functional programming languages. In Chapter 14, we’ll examine Cargo in more
depth and talk about best practices for sharing your libraries with others.
Chapter 15 discusses smart pointers that the standard library provides and the
traits that enable their functionality.
-->

第十三章探索了闭包（Closure）和迭代器（Iterator）：Rust 中来自函数式编程语言的功能。在第十四章中，我们会加深对 Cargo 的理解并讨论向他人分享库的最佳实践。第十五章讨论了标准库提供的智能指针以及启用这些功能的特质（Trait）。
<!--
In Chapter 16, we’ll walk through different models of concurrent programming
and talk about how Rust helps you to program in multiple threads fearlessly.
Chapter 17 looks at how Rust idioms compare to object oriented programming
principles you might be familiar with.
-->

在第十六章中，我们会学习不同的并发编程模型，讨论 Rust 如何助你无畏地编写多线程程序。第十七章着眼于比较 Rust 的编程习语与你可能熟悉的面向对象编程原则。

<!--
Chapter 18 is a reference on patterns and pattern matching, which are powerful
ways of expressing ideas throughout Rust programs. Chapter 19 contains a
smorgasbord of advanced topics of interest, including unsafe Rust and more
about lifetimes, traits, types, functions, and closures.
-->

第十八章为模式和模式匹配的参考章节，它是一种在整个 Rust 程序中表达意图的强大方式。第十九章为高级主题的大杂烩，包括不安全（Unsafe）Rust 和更多关于生命周期、 特质、类型、函数和闭包的内容。

<!--
In Chapter 20, we’ll complete a project in which we’ll implement a low-level
multithreaded web server!
-->

在第二十章中，我们会完成一个项目，即实现一个底层的、多线程的 Web 服务器！

<!--
Finally, some appendixes contain useful information about the language in a
more reference-like format. Appendix A covers Rust’s keywords. Appendix B
covers Rust’s operators and symbols. Appendix C covers derivable traits
provided by the standard library. Appendix D covers macros.
-->

最后是一些附录，包含一些参考手册风格的关于语言的实用信息。附录 A 介绍了 Rust 的关键字；附录 B 介绍了 Rust 的运算符和符号；附录 C 介绍了标准库中提供的派生特质；附录 D 则介绍了宏。

<!--
There is no wrong way to read this book: if you want to skip ahead, go for it!
You might have to jump back to earlier chapters if you experience any
confusion. But do whatever works for you.
-->

怎样阅读本书都不会有任何问题：如果你希望略过一些内容，请随意！如果你产生了疑惑，可以再跳回之前的章节，总之怎样都行。

<!--
An important part of the process of learning Rust is learning how to read the
error messages the compiler displays: these will guide you toward working code.
As such, we’ll provide many examples of code that don’t compile along with the
error message the compiler will show you in each situation. Know that if you
enter and run a random example, it may not compile! Make sure you read the
surrounding text to see whether the example you’re trying to run is meant to
error. In most situations, we’ll lead you to the correct version of any code
that doesn’t compile.
-->

在学习 Rust 的过程中，一个重要的部分就是学习如何阅读编译器提供的错误信息：它们会指导你编写出能够工作的代码。为此，我们会提供很多无法通过编译的示例代码，以及各种情况下编译器会展示的错误信息。请注意，如果随便输入并运行随机的示例代码，它们可能会无法编译！请确保阅读你尝试运行的示例周围的任何内容，检视它们是否是故意写错的。在大部分情况下，我们都会指引着你将任何无法编译的代码纠正为正确的版本。

<!--
## Contributing to the Book
-->

## 为本书做出贡献

<!--
This book is open source. If you find an error, please don’t hesitate to file
an issue or send a pull request on GitHub at
*https://github.com/rust-lang/book/*. Please see CONTRIBUTING.md at
*https://github.com/rust-lang/book/blob/master/CONTRIBUTING.md* for more
details.
-->

本书是开源的。如果你发现了错误，请不要犹豫，尽管在 *https://github.com/rust-lang/book/* 上提问（Issue）或发送合并请求（Pull Request）吧！更多详情请参阅位于 *https://github.com/rust-lang/book/blob/master/CONTRIBUTING.md* 的CONTRIBUTING.md 文件。
