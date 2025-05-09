## 前言

*我常常觉得美国的程序员如果学习拉丁语，比学习另一个编程语言要更有益。*

—埃兹杰·迪克斯特拉

![Image](img/common.jpg)

Julia 是一种相对较新的编程语言。它在 2012 年进入公众视野，之前 MIT 的四位计算机科学家研究了两年半时间。Julia 的创造者解释了他们为何需要创建一种新语言：他们“贪心”。

已经有一些语言很快，比如 C 和 Fortran。这些语言非常适合用于编写在巨型超级计算机上运行的程序，用于模拟天气或设计飞机。但它们的语法并不最友好；这些语言中的程序要求一定的仪式感。并且它们并没有提供交互式体验；在终端中无法即兴创作和探索，必须遵循编辑-编译-运行的步骤。

也有其他语言，不需要仪式感，可以作为交互式计算器使用，比如 Python 和 MATLAB。然而，这些语言编写的程序速度较慢。而且，这些语言通常不适合保持大型程序的组织结构。

Julia 的创造者之所以“贪心”，是因为他们想要兼得一切：一种和 Python 一样易用的语言，但同时又有 Fortran 一样的速度。人们通常通过为 Python 等语言增加速度优化来解决这个问题，通常需要将程序中耗时的部分重写成更快的语言，比如 C。这样产生的“拼接体”意味着需要在两种语言中维护代码，这带来了组织、人员和心理上的额外负担。这就是所谓的“两语言问题”，而 Julia 的动机之一就是要解决这个问题。

Julia 现在被广泛誉为解决两语言问题的真正方案。事实上，它是仅有的三种属于“千万亿次俱乐部”的语言之一，在巨大的数值计算问题上达到顶级性能（另外两种是 Fortran 和 C++）。独特的是，Julia 将这种高性能与作为交互式计算器的能力结合在一起，无论是在其精心打磨的读取-求值-打印循环（REPL）中，还是在各种开发环境或基于浏览器的笔记本中。

对于那些曾使用过 Python、Octave、MATLAB、JavaScript（通过 Node）或其他基于 REPL 的语言系统的人来说，Julia 的使用体验将会非常熟悉。你只需在终端中输入`julia`，就会看到一个简短的启动信息和一个友好的交互式提示符。现在你可以输入表达式，并立即在终端中看到结果。你可以定义变量和函数，操作数组，导入函数库，从磁盘或网络读取数据，并且可以将语言作为一个复杂的计算器来使用。你无需声明变量的类型，也不需要编写任何额外的模板代码，这些代码并不会干扰你的工作。

这些是它与其他解释型语言的相似之处。你还会遇到一些不同之处。你可能会注意到偶尔会有几秒钟的延迟，而这种情况通常不会出现在像 Python 这样的语言中。这是因为 Julia 实际上并不是一种传统的解释型语言，它在幕后进行代码的预编译和即时编译（JIT）。

正如你将发现的，当你的计算变得庞大时，这种权衡是值得的。你对其他交互式语言的经验可能让你预期代码会变得非常缓慢，但你会发现，实际上，代码的执行速度与 Fortran 等编译语言一样快。

随着进一步的探索，你会发现 Julia 与其他你熟悉的语言不同。乍一看，它似乎与其他语言相似。你可以输入`1 + 1`并得到`2`的结果。但你会了解到，Julia 既不像 Python 那样面向对象，也不像 Haskell 那样传统的函数式编程语言，更不像 JavaScript 那样的语言。Julia 的设计基于一个不同的原理，这也是它强大之处的来源。

### **为什么科学家喜欢 Julia？**

Julia 的设计围绕着一种叫做多重分派（multiple dispatch）的机制，这得益于其强大而灵活的类型系统。稍后，你会了解到这些概念的含义，以及如何在你的程序中利用它们。现在，请将这个概念记住并留作日后参考：多重分派系统是 Julia 在科学界取得成功的关键因素之一，与其著名的互动性和速度同样重要。虽然 Julia 不是第一个采用这一特性的语言，但它是第一个将此特性与其他优点结合，真正使其对科研界有用的语言。

正是这个设计特性使得代码重用和重组达到了前所未有的程度和简便性。这一点，与任何基准测试一样，是吸引那些已将 Julia 作为计算工具的研究人员的原因。Julia 在科学界的快速发展，主要是因为它使得研究人员能够相互使用代码，并将不同的库重新组合，创造出库作者未曾预见到的新功能。你将在后续章节中看到许多这样的例子，特别是在第二部分中。你还将看到类型系统和 Julia 的元编程能力如何使你能够完美地将语言与问题相匹配，而不牺牲性能。

### **这本书能为你做什么？**

在阅读完第一部分和第二部分中你感兴趣的内容后，你将能够充分利用 Julia 解决任何遇到的计算问题。你将学会如何探索和可视化数据，解决方程式，编写仿真程序，并使用和创建库。本书的重点是将 Julia 应用于研究问题。方法直接且实用，理论计算机科学的内容尽量简化。我将教你如何编写高效的代码，使其能够在笔记本电脑或大型分布式系统上运行。无论你对科学研究、数学、统计学，还是仅仅为了娱乐感兴趣，你都将学会如何智能地使用这个工具，并享受使用的乐趣。

本书从基础开始，假设你从未接触过 Julia。我不假设你已经掌握了任何特定的数值方法或计算技术，会在需要时解释这些内容。我只假设你有一些基本的编程概念接触经验。换句话说，当我描述如何在 Julia 中写一个`if`语句时，我会期望你在一般意义上了解使用条件的概念。

### **如何使用本书**

第一部分的内容是按顺序构建的，因此，理想情况下，你应该按顺序阅读这些章节。相对而言，第二部分的章节只依赖于第一部分的内容，而不相互依赖。你可以不看物理章节而直接阅读生物学章节。当然，我鼓励每个人都阅读每一章！原因如下：一些特定的技术是在最相关的应用章节中开发的。然而，由于科学研究的性质，任何计算知识都可能在任何学科中找到应用。例如，一位生物学家可能会发现物理章节中关于微分方程求解器的内容对模拟种群动态有帮助。由于第二部分中的章节没有固定顺序，最自然的做法可能是首先阅读你最感兴趣的章节，其他章节可以在闲暇时再回头阅读。

本书有一个详细的索引，应该能帮助你轻松找到任何内容，无论它藏在哪里。

为了最大限度地利用本书，建议你一边阅读，一边在 Julia 提示符下进行实践，这样你可以在遇到问题时进行尝试。实践的方法比单纯阅读更能有效地巩固理解。当你跟随本书内容时，你会想尝试我的示例代码的不同变体，通过反复试验了解语言的行为。你不会弄坏任何东西。如果你进入了一个不知如何解决的奇怪状态，可以简单地退出 REPL 并重新启动。此外，Julia REPL 有一个完善的文档模式，你可以在其中访问任何特定函数的详细信息，以补充书中的内容。

本书有一个配套网站，网址为[*https://julia.lee-phillips.org*](https://julia.lee-phillips.org)，你可以在网站上找到文本中的所有主要代码示例的可运行版本、程序使用的数据文件、插图的彩色版本、示例动画以及模拟视频。

### **书籍概述**

在第一部分中，首先处理安装和编程环境的基础知识，然后重点学习 Julia：语法、数据类型、概念和最佳实践。本部分还包括有关模块和包系统以及可视化的章节。

**第一章：入门** 介绍了运行 Julia 和从本书中受益所需的硬件和经验，并提供了在各种操作系统上安装的指南。我们还回顾了最常见的编码环境，并给出了几点建议。

**第二章：语言基础** 介绍了 Julia 的概念、语法和数据类型，为你提供扎实的语言基础。

**第三章：模块与包** 描述了如何组织你的 Julia 程序，如何将他人的代码整合到自己的工作中，以及如何成为 Julia 社区的一部分。

**第四章：绘图系统** 重点讲解了 Julia 强大的`Plots`包。你将学习如何创建和自定义每种常见的 2D 和 3D 图表，以及如何创建交互式图形和用于出版的最终插图。

**第五章：集合** 介绍了数据类型，如集合、字符串、数组、字典、结构体和元组。本章涵盖了推导式和生成器、集合操作符、数组初始化和操作，以及 Julia 的各种字符串类型。

**第六章：函数、元编程与错误处理** 进一步探讨函数，讲解了不同的定义和传递参数的方式，以及高阶函数。包括元编程的介绍，涉及使用符号、表达式对象和宏来编写操作代码的代码。

**第七章：图表与动画** 展示了如何使用一个灵活且强大的包来制作数学和其他类型的图表，以及一个更专门化的工具来绘制节点和边图。我们将探索两个提供不同动画制作方法的包，并将在后续章节中使用这些包来制作插图和视频。

**第八章：类型系统** 详细介绍了 Julia 中不同种类的数字和其他对象、类型层次结构、类型断言与声明，以及如何创建我们自己的类型。它解释了如何将类型系统与多重分派相结合来组织程序，并讨论了类型与性能之间的关系。此外，关于绘图配方的部分揭示了 Julia 绘图系统的独特强大功能。

第二部分 包含了专门研究某一特定领域的章节，以及关于并行处理的最后一章。每个章节都使用一个或多个在某一应用领域广泛使用的专业包，并探讨至少一个该领域中的有趣问题。

**第九章：物理学** 展示了如何给数字添加单位和不确定性，这是许多领域的科学家可能感兴趣的主题。一个详细的热对流示例演示了如何使用强大的流体动力学包。该章节以介绍解决微分方程的最先进包作为结尾。

**第十章：统计学** 讨论了统计学和概率论中的概念，如分布，并将其与相关 Julia 包提供的函数和类型联系起来。它将这些概念应用于模拟感染的传播，并通过对 COVID 病例的实际数据进行切片和切割，介绍了数据框架。

**第十一章：生物学** 探讨了基于代理的建模，并展示了如何使用 Julia 的`Agents`包来模拟生物进化，生物学习如何避免被捕食者捕获。该章节基于统计学章节中的一些概念来分析结果。

**第十二章：数学** 聚焦于符号数学（计算机代数）和线性代数。它描述了第一主题的两种主要方法，包括混合数值-符号技术。它涵盖了使用线性代数包来求解方程，并通过利用类型系统高效地执行矩阵运算的基本方法。

**第十三章：科学机器学习** 探讨了一个相对较新的领域，其中利用机器学习的思想推断模型的属性。它展示了如何在多个场景中使用自动微分，并通过 Julia 的`Turing`包介绍了概率编程。

**第十四章：信号与图像处理** 聚焦于信号和图像。信号部分涵盖傅里叶分析、滤波和相关主题，使用鸟鸣声作为工作实例。图像部分通过在计数血细胞问题中的特征识别，探讨了图像大小调整、平滑处理和其他操作的多种技术。在这一部分，还进一步深入探讨了高级数组概念。

**第十五章：并行处理** 解释了如何在多个 CPU 核心或计算机上运行我们的程序。本章讨论了不同的并发范式，以及如何利用多线程和多处理技术。我们将看到如何在全球各地的网络机器上运行程序，而无需更改代码。

**进一步阅读**

+   要了解 Julia 语言的灵感来源，请阅读《我们为何创造 Julia》：[*https://julialang.org/blog/2012/02/why-we-created-julia/*](https://julialang.org/blog/2012/02/why-we-created-julia/)。

+   我的文章《*Julia 编程语言的非理性有效性*》发表于 *Ars Technica*，解释了 Julia 在科学家中广泛应用的根本原因：[*https://arstechnica.com/science/2020/10/the-unreasonable-effectiveness-of-the-julia-programming-language/*](https://arstechnica.com/science/2020/10/the-unreasonable-effectiveness-of-the-julia-programming-language/)。

+   如果你是 Python 程序员，并且想要简要了解语法上的差异，请查看 Dr. John D. Cook 在 [*http://www.johndcook.com/blog/2015/09/15/julia-for-python-programmers/*](http://www.johndcook.com/blog/2015/09/15/julia-for-python-programmers/) 上的文章《Python 程序员的 Julia 入门》。

+   如果你来自 Lisp，请阅读 Pascal Costanza 在 [*https://p-cos.blogspot.com/search?q=first+impression+of+Julia*](https://p-cos.blogspot.com/search?q=first+impression+of+Julia) 上的文章《Lisper 对 Julia 的第一印象》。虽然这篇文章是 2014 年的，但仍然值得一读。

+   要了解解释新语言需求的原始理论依据以及 Julia 设计决策如何满足这些需求，请参阅《Julia：一种全新的数值计算方法》，该文由 Julia 的创造者 Jeff Bezanson、Alan Edelman、Stefan Karpinski 和 Viral B. Shah 合著（[*http://arxiv.org/abs/1411.1607*](http://arxiv.org/abs/1411.1607)）。

+   如果你想了解 Julia 创造故事的另一个版本，可以查看 Klint Finley 的文章《公开的：人类创造了一种编程语言来统治一切》（[*https://www.wired.com/2014/02/julia/*](https://www.wired.com/2014/02/julia/)）。

+   《*Julia 加入了 Petaflop 俱乐部*》由 Julia Computing 发布，展示了 Julia 在天文（两方面）应用中的一个案例（[*https://cacm.acm.org/news/221003-julia-joins-petaflop-club/fulltext*](https://cacm.acm.org/news/221003-julia-joins-petaflop-club/fulltext)）。

+   John Russell 的《Julia 更新：采用率持续攀升；它是 Python 的挑战者吗？》([*https://www.hpcwire.com/2021/01/13/julia-update-adoption-keeps-climbing-is-it-a-python-challenger/*](https://www.hpcwire.com/2021/01/13/julia-update-adoption-keeps-climbing-is-it-a-python-challenger/))提供了一些有趣的历史视角。

+   Bradley Setzler 的《为什么我转向 Julia》是一个关于 Julia 在计量经济学中应用的案例研究，展示了在使用 NumPy 时，Julia 比 Python 的速度提高了 100 倍：[*https://juliaeconomics.com/2014/06/15/why-i-started-a-blog-about-programming-julia-for-economics/*](https://juliaeconomics.com/2014/06/15/why-i-started-a-blog-about-programming-julia-for-economics/)。
