---
title: "优化最佳做法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Visual C++, 优化"
  - "优化, 最佳做法"
ms.assetid: f3433148-7255-4ca6-8a4f-7c31aac88508
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 优化最佳做法
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文档介绍在 Visual C\+\+ 中实现优化的一些最佳做法。  讨论了下列主题：  
  
-   编译器和链接器选项  
  
    -   按配置优化  
  
    -   应当使用哪个优化级别？  
  
    -   浮点开关  
  
-   优化 Declspec  
  
-   优化杂注  
  
-   \_\_restrict 和 \_\_assume  
  
-   内部函数支持  
  
-   异常  
  
## 编译器和链接器选项  
  
### 按配置优化  
 Visual C\+\+ 支持按配置优化 \(PGO\)。  此优化功能使用在过去执行所检测版本的应用程序时生成的配置文件数据来驱动以后对该应用程序的优化。  使用 PGO 可能会非常耗时，因此可能并非所有的开发人员都使用它，但是我们建议您对于产品的最终发布版本使用 PGO。  有关详细信息，请参阅[按配置文件优化](../../build/reference/profile-guided-optimizations.md)。  
  
 另外，已经针对“全程序优化”（又称作“链接时间代码生成”）以及 **\/O1** 和 **\/O2** 优化进行了改善。  通常，用下列选项之一编译的应用程序将比用以前的编译器编译的同一个应用程序快。  
  
 有关更多信息，请参见[\/GL（全程序优化）](../../build/reference/gl-whole-program-optimization.md)和[\/O1、\/O2（最小化大小、最大化速度）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)。  
  
### 应当使用哪个优化级别？  
 只要有可能，就应当用“按配置文件优化”来编译最终的发布版本。  如果不可能用 PGO 生成（无论是由于没有足够的基础结构来运行所检测的版本还是无权访问方案），我们建议您用“全程序优化”生成。  
  
 **\/Gy** 开关也非常有用。  它为每个函数生成一个单独的 COMDAT，当它开始移除未引用的 COMDAT 和 COMDAT 折叠时，为链接器提供了更大的灵活性。  使用 **\/Gy** 的唯一缺点在于，它会对生成时间有微小的影响。  因此，通常建议使用它。  有关详细信息，请参阅[\/Gy（启用函数级链接）](../../build/reference/gy-enable-function-level-linking.md)。  
  
 对于 64 位环境中的链接，建议使用 **\/OPT:REF,ICF** 链接器选项，对于 32 位环境中的链接，建议使用 **\/OPT:REF**。  有关详细信息，请参阅[\/OPT（优化）](../../build/reference/opt-optimizations.md)。  
  
 还强烈建议生成调试符号，对于优化的发布版本也是如此。  它并不影响生成的代码，而且会更便于调试应用程序（如果需要的话）。  
  
### 浮点开关  
 移除了 **\/Op** 编译器选项，并且添加了以下四个涉及浮点优化的编译器选项：  
  
|||  
|-|-|  
|**\/fp:precise**|这是默认的建议，而且应当用在大多数情况下。|  
|**\/fp:fast**|如果执行速度至关重要（例如，在游戏中），建议使用该选项。  这将导致最快的执行速度。|  
|**\/fp:strict**|如果需要精确的浮点异常和 IEEE 行为，建议使用该选项。  这将导致最慢的执行速度。|  
|**\/fp:except\[\-\]**|可以与 **\/fp:strict** 或 **\/fp:precise** 一起使用，但是不能与 **\/fp:fast** 一起使用。|  
  
 有关详细信息，请参阅[\/fp（指定浮点行为）](../../build/reference/fp-specify-floating-point-behavior.md)。  
  
## 优化 Declspec  
 在本节中，我们将查看两个可在程序中用来提高性能的 declspec：`__declspec(restrict)` 和 `__declspec(noalias)`。  
  
 `restrict` declspec 仅适用于返回指针的函数声明，如 `__declspec(restrict) void *malloc(size_t size);`  
  
 `restrict` declspec 适用于返回非别名指针的函数。  此关键字用于 `malloc` 的 C 运行库实现，因为它决不会返回已经在当前程序中使用的指针值（除非您执行某个非法操作，如在内存已被释放之后使用它）。  
  
 `restrict` declspec 为编译器提供执行编译器优化的更多信息。  对于编译器来说，最大的困难之一是确定哪些指针会与其他指针混淆，而使用这些信息对编译器很有帮助。  
  
 有必要指出，这是对编译器的一个承诺，编译器并不对其进行验证。  如果您的程序不恰当地使用 `restrict` declspec，则该程序的行为会不正确。  
  
 有关详细信息，请参阅[restrict](../../cpp/restrict.md)。  
  
 `noalias` declspec 也是仅适用于函数，它指出该函数是半纯粹的函数。  半纯粹的函数是指仅引用或修改局部变量、参数和第一层间接参数。  此 declspec 是对编译器的一个承诺，如果该函数引用全局变量或第二层间接指针参数，则编译器会生成将中断应用程序的代码。  
  
 有关详细信息，请参阅[noalias](../../cpp/noalias.md)。  
  
## 优化杂注  
 这些杂注有助于优化代码。  我们将首先讨论 `#pragma optimize`：  
  
```  
#pragma optimize("{opt-list}", on | off)  
```  
  
 通过该杂注，可以对每个函数设置一个给定优化级别。  该杂注非常适合下面的极少情况：当给定的函数是用优化功能编译时，应用程序崩溃。  可以使用该杂注来关闭针对单个函数的优化：  
  
```  
#pragma optimize("", off)  
int myFunc() {...}  
#pragma optimize("", on)  
```  
  
 有关详细信息，请参阅[optimize](../../preprocessor/optimize.md)。  
  
 内联是编译器所执行的最重要的优化之一，我们将在此处讨论两个可帮助修改此行为的杂注。  
  
 `#pragma inline_recursion` 有助于指定是否希望应用程序能够内联递归调用。  默认情况下，该杂注为 off。  对于小函数的浅表递归，可以打开该杂注。  有关详细信息，请参阅[inline\_recursion](../../preprocessor/inline-recursion.md)。  
  
 限制内联深度的另一个有用的杂注是 `#pragma inline_depth`。  如果您尝试限制程序或函数的大小，通常使用该杂注。  有关详细信息，请参阅[inline\_depth](../../preprocessor/inline-depth.md)。  
  
## \_\_restrict 和 \_\_assume  
 Visual C\+\+ 中有两个可帮助提高性能的关键字：[\_\_restrict](../../cpp/extension-restrict.md) 和 [\_\_assume](../../intrinsics/assume.md)。  
  
 首先，应当注意的是，`__restrict` 和 `__declspec(restrict)` 是两种不同的事物。  尽管它们在某种程度上相关，但它们的语义不同。  `__restrict` 是一个类型限定符（就像 `const` 或 `volatile`），不过，它专用于指针类型。  
  
 用 `__restrict` 修饰的指针称为“\_\_restrict 指针”。  \_\_restrict 指针只能通过 \_\_restrict 指针来访问。  换言之，不能使用其他指针来访问 \_\_restrict 指针所指向的数据。  
  
 `__restrict` 可以是 Visual C\+\+ 优化器的一个强大工具，但是在使用它时一定要格外小心。  如果使用不当，该优化器可能会执行将中断应用程序的优化。  
  
 `__restrict` 关键字替换以前版本中的 **\/Oa** 开关。  
  
 使用 `__assume,`，开发人员可以通知编译器假定某个变量的值。  
  
 例如，`__assume(a < 5);` 通知优化器该行代码中的 `a` 变量小于 5。  这也是对编译器的一个承诺。  如果此时 `a` 在程序中实际为 6，则在编译器经过优化之后，程序的行为可能会与预期的不同。  `__assume` 最适合用在 switch 语句和\/或条件表达式之前。  
  
 对于 `__assume` 有一些限制。  首先，像 `__restrict` 一样，它只是一个建议，因此编译器可以安全地忽略它。  同样，`__assume` 当前仅适用于变量与常量不相等的情况。  它并不传送符号不等式，例如，假定\(a \< b\)。  
  
## 内部函数支持  
 对于内部函数调用，由于编译器内在了解这种函数调用，因此它是从这种函数发出代码，而不是调用库中的函数。  位于 \<Installation\_Directory\>\\VC\\include\\intrin.h 中的头文件 intrin.h 包含三个对支持平台（x86、x64 和 ARM）都可用的内部函数。  
  
 内部函数使程序员能够深入代码内部，而不必使用程序集。  使用内部函数有多个好处：  
  
1.  代码的可移植性更强。  一些内部函数可以在多 CPU 结构上使用。  
  
2.  代码的可读性更强，因为代码仍是用 C\/C\+\+ 编写的。  
  
3.  代码可获得编译器优化的好处。  编译器越好，针对内部函数生成的代码越好。  
  
 有关更多信息，请参见[编译器内部函数](../../intrinsics/compiler-intrinsics.md)和[Benefits of Using Intrinsics](http://msdn.microsoft.com/zh-cn/57af8920-527f-44af-a741-a07cbe80bf02)。  
  
## 异常  
 使用异常会对性能造成影响。  在使用会禁止编译器执行某些优化的 try 块时，会引入一些限制。  在 x86 平台上，try 块会造成额外的性能下降，这是由于在代码执行过程中必须生成额外的状态信息。  在 64 位平台上，try 块不会使性能下降太多，但是一旦引发了异常，查找处理程序并展开堆栈这一过程所产生的开销会很大。  
  
 因此，建议您避免向代码中引进 try\/catch 块，除非特别需要它。  如果必须使用异常，请尽可能使用同步异常。  有关详细信息，请参阅[结构化异常处理](../../cpp/structured-exception-handling-c-cpp.md)。  
  
 最后，仅针对异常情况引发异常。  对于常规的控制流使用异常将有可能大大影响性能。  
  
## 请参阅  
 [优化代码](../../build/reference/optimizing-your-code.md)