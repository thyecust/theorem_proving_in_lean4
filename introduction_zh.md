引论 Introduction
============

计算机与定理证明
-----------------------------

*形式化验证* 用逻辑和计算方法来建立数学语言的论断。这包括常规数学证明，也包括硬件或者软件、网络协议、机械或混合系统符合规约的论断。
实践中数学证明和系统正确性验证之间没有明确的界限：形式化验证要求用数学语言描述硬件和软件系统，其正确性的论断便形如数学定理的证明。
反过来说，数学定理的证明可能用到一段计算，验证定理相当于验证这段计算做了我们希望的事。

支持一个数学论断的黄金标准事提供一个证明，二十世纪逻辑学的发展表明大部分（若非全然）证明方法可以简化到一小组公理和一定数量的基础系统规则。
使用这种简化，计算机有两种方式帮助建立论断：帮助寻找证明，帮助验证一个证明是正确的。

*自动定理证明*关注“寻找”一方。Resolution-定理证明器、tableau-定理证明器、快速SAT求解器等工具可以建立命题和一阶逻辑公式的有效性（validity）。
其它系统提供特定语言和问题域的搜索和决策过程，如整数/浮点数上的线性/非线性表达式。
诸如SMT（satisfiability modulo theories）的架构融合了通用领域的搜索方法和特定领域的过程。
计算机代数系统和专门数学软件负责数学计算，建立数学约束，或寻找数学对象。
一个计算也可以看成一个证明，这些系统同样帮助建立数学论断。

自动推理系统常牺牲可靠性，为电力和效率努力。这样的系统可能有bug，并且很难确定其结果是正确的。
相反，*交互式定理证明*聚焦于“验证”一方，每个论断要有一个合适公理基础的证明支持。
这建立了一个非常高的标准：每条推断规则和每步计算都由先前的定义和定理支撑，每条路都归于基本公理和规则。
事实上，所有这样的系统都提供非常详尽的“证明对象”（proof objects），可以发送给其它系统进行独立的检查。
建立这样的证明通常需要多得多的输入和用户交互，但是使你得以建立更深入、更复杂的证明。

*Lean 定理证明器* 旨在建立交互式和自动定理证明的桥梁，这个框架内置了自动化工具，也支持用户的交互和构建非常特定的公理化证明。
它的目标是同时支持数学推理和复杂系统推理，在每个问题域验证论断。

Lean依赖的逻辑有一个计算解释，Lean可以等效看作一个编程语言。不止是这样，它可以被当成一个写精确语义程序的系统，同时对这个程序的计算函数做推理。
Lean也有它自己的*元编程*机制，意味着你可实现自动化和使用Lean拓展Lean的功能。Lean的这些方面，在相伴的另一本教程里详细介绍，[Programming in Lean 4](TBD)，
尽管这本书里也会出现这个系统计算的一面。

About Lean
----------

*Lean*项目由Leonardo de Moura于2013在Microsoft Research Redmond启动。这是一个进行中的长期努力，许多潜在的自动化会随着时间逐步实现。
Lean使用[Apache 2.0 license](LICENSE)发布，一个宽容的开源许可证，允许他人自由使用和拓展代码和数学库。

使用[Quickstart](https://github.com/leanprover/lean4/blob/master/doc/quickstart.md)中的指导在你的计算机上安装Lean。
Lean的源代码，构建和指引见[https://github.com/leanprover/lean4/](https://github.com/leanprover/lean4/)。

本教程描述了Lean的现有版本，即Lean 4。

这本书
---------------

这本书旨在教授在Lean中开发和验证证明。大部分背景知识不是特定于Lean的。
开始，你需要学习Lean建立在什么逻辑系统之上，一种强健到足够证明所有常见数学定理、并且自然地表达的*依值类型论*。
更具体地，Lean建立在带有归纳类型的Calculus of Constructions之上。
Lean不仅可以在依值类型论里定义数学对象，表达数学断言，也可以用于写证明。

因为彻底的公理化证明细节过于繁琐，定理证明的挑战在于让计算机尽可能地填补其中的细节。
你会学习到在依值类型论里支持这一点的诸多方法。例如，项重写（term rewriting）和Lean简化项和表达式的自动化方法。
类似地，*详化*（elaboration）和*类型推断*（type inference）用于支持自由形式的代数推理。

最后你会学习特定于Lean的特性，包括你和系统交互的语言，Lean用来管理复杂理论和数据的机制。

文中你会见到这样的示例代码

```lean
theorem and_commutative (p q : Prop) : p ∧ q → q ∧ p :=
  fun hpq : p ∧ q =>
  have hp : p := And.left hpq
  have hq : q := And.right hpq
  show q ∧ p from And.intro hq hp
```

如果你在 [VS Code](https://code.visualstudio.com/) 中阅读这本书，你会在旁边看到一个按钮写着“try it!”。
按下这个按钮将复制代码到你的编辑器，加上必要的context使其可以编译。你可以往编辑器里输入，改变示例代码，Lean会检查结果并持续地给出反馈。
我们推荐你运行这些例子并做一些实验。你可以在VSCode使用命令"Lean 4: Open Documentation View"打开这本书。

致谢
---------------

This tutorial is an open access project maintained on Github. Many people have contributed to the effort, providing
corrections, suggestions, examples, and text. We are grateful to Ulrik Buchholz, Kevin Buzzard, Mario Carneiro, Nathan
Carter, Eduardo Cavazos, Amine Chaieb, Joe Corneli, William DeMeo, Marcus Klaas de Vries, Ben Dyer, Gabriel Ebner,
Anthony Hart, Simon Hudon, Sean Leather, Assia Mahboubi, Gihan Marasingha, Patrick Massot, Christopher John Mazey,
Sebastian Ullrich, Floris van Doorn, Daniel Velleman, Théo Zimmerman, Paul Chisholm, Chris Lovett, and Siddhartha Gadgil for their contributions.  Please see [lean prover](https://github.com/leanprover/) and [lean community](https://github.com/leanprover-community/) for an up to date list
of our amazing contributors.
