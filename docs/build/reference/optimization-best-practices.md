---
title: "优化最佳做法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, optimization
- optimization, best practices
ms.assetid: f3433148-7255-4ca6-8a4f-7c31aac88508
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ec12e847eef72827e11700be322fd2a2ca309037
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="optimization-best-practices"></a>优化最佳做法
本文档介绍 Visual c + + 中的优化选项的一些最佳做法。 本文讨论了以下主题：  
  
-   编译器和链接器选项  
  
    -   按配置文件优化  
  
    -   应使用的优化级别？  
  
    -   浮点开关  
  
-   优化 Declspec  
  
-   优化杂注  
  
-   __restrict 和\__assume  
  
-   内部函数的支持  
  
-   异常  
  
## <a name="compiler-and-linker-options"></a>编译器和链接器选项  
  
### <a name="profile-guided-optimization"></a>按配置文件优化  
 Visual c + + 支持按配置优化 (PGO)。 此优化使用从过去执行的已插入检测点版本的应用程序的配置文件数据驱动的应用程序的更高版本优化。 使用 PGO 可能很耗时，因此它可能不是指每个开发人员使用，但我们建议使用 PGO 适用于产品的最终发布版本。 有关详细信息，请参阅[按配置文件优化](../../build/reference/profile-guided-optimizations.md)。  
  
 此外，全程序优化 （也称作链接时间代码生成） 和**/O1**和**/O2**优化已得到改进。 一般情况下，使用这些选项之一编译的应用程序会比以前的编译器用编译相同应用程序更快。  
  
 有关详细信息，请参阅[/GL （全程序优化）](../../build/reference/gl-whole-program-optimization.md)和[/O1、 /O2 （最小化大小、 最大化速度）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)。  
  
### <a name="which-level-of-optimization-should-i-use"></a>应使用的优化级别？  
 有可能，最终发布版本应使用按配置优化进行编译。 如果它不能使用 PGO，生成是否是由于运行所检测的版本或不具有访问方案的不足基础结构，我们建议建筑物的全程序优化。  
  
 **/Gy**交换机也是非常有用。 它将生成单独 COMDAT，对于每个函数，为链接器提供更大的灵活性，就删除未引用的 Comdat 和 COMDAT 折叠。 使用唯一的缺点**/Gy**在于，它可以有对生成时间微小的影响。 因此，通常建议使用它。 有关详细信息，请参阅 [/Gy （启用函数级链接）](../../build/reference/gy-enable-function-level-linking.md)。  
  
 用于在 64 位环境中的链接，建议使用**/opt: ref、 ICF**链接器选项，以及在 32 位环境中**/opt: ref**建议。 有关详细信息，请参阅[/OPT （优化）](../../build/reference/opt-optimizations.md)。  
  
 此外，强烈建议生成调试符号，即使使用优化的发布版本。 它并不影响生成的代码中，并且更易于调试你的应用程序，如果很多需要。  
  
### <a name="floating-point-switches"></a>浮点开关  
 **/Op**编译器选项已被删除，并且已添加处理浮点优化以下四个编译器选项：  
  
|||  
|-|-|  
|**/fp： 精确**|这是默认的建议，并应在大多数情况下使用。|  
|**/fp:fast**|建议如果极其重要，例如在游戏的性能。 这将导致最快的性能。|  
|**/fp: strict**|建议的如果精确的浮点异常和 IEEE 所需行为。 这将导致速度最慢的性能。|  
|**/fp: except [-]**|可以结合使用**/fp: strict**或**/fp： 精确**，但不是**/fp:fast**。|  
  
 有关详细信息，请参阅 [/fp（指定浮点行为）](../../build/reference/fp-specify-floating-point-behavior.md)。  
  
## <a name="optimization-declspecs"></a>优化 Declspec  
 在本部分中我们将介绍可以在程序中使用，来帮助提高性能的两个 declspec:`__declspec(restrict)`和`__declspec(noalias)`。  
  
 `restrict` Declspec 只能应用于返回的指针，如的函数声明`__declspec(restrict) void *malloc(size_t size);`  
  
 `restrict` Declspec 返回非别名的指针的函数上使用。 此关键字用于 C 运行时库实现`malloc`因为它决不会返回一个指针值 （除非你正在某个非法操作，例如，使用内存，已被释放之后） 已在当前程序中使用。  
  
 `restrict` Declspec 为编译器提供了用于执行编译器优化的详细信息。 编译器将确定最困难的工作之一是哪些指针别名其他指针，并使用此信息可以大大帮助编译器。  
  
 值得指出的是，这是对编译器，不是编译器将验证的内容的一个承诺。 如果程序使用此`restrict`declspec 不当而导致，程序可能具有不正确的行为。  
  
 有关详细信息，请参阅[限制](../../cpp/restrict.md)。  
  
 `noalias` Declspec 还只应用到函数，并指示该函数为半纯函数。 半纯函数是指引用或修改局部变量、 参数和自变量的第一级间接寻址。 此 declspec 是对编译器，一个承诺，如果该函数引用全局变量或第二个一级间接寻址的指针自变量则编译器可能生成的代码，将中断应用程序。  
  
 有关详细信息，请参阅 [noalias](../../cpp/noalias.md)。  
  
## <a name="optimization-pragmas"></a>优化杂注  
 此外，还存在有助于优化代码的几个有用的杂注。 我们将讨论的第一个是`#pragma optimize`:  
  
```  
#pragma optimize("{opt-list}", on | off)  
```  
  
 此杂注，可基于函数的函数设置给定的优化级别。 这是理想的极少情况时给定的函数编译优化你的应用程序崩溃，其中。 你可以使用此关闭优化针对单个函数：  
  
```  
#pragma optimize("", off)  
int myFunc() {...}  
#pragma optimize("", on)  
```  
  
 有关详细信息，请参阅[优化](../../preprocessor/optimize.md)。  
  
 内联是最重要的优化编译器执行并此处我们将讨论几个帮助修改此行为的杂注之一。  
  
 `#pragma inline_recursion`可用于指定希望应用程序能够进行内联递归调用。 默认情况下处于关闭状态。 为小函数的浅表递归，你可能要开启此设置。 有关详细信息，请参阅[inline_recursion](../../preprocessor/inline-recursion.md)。  
  
 用于限制的深度的另一个有用杂注内联为`#pragma inline_depth`。 这是在你尝试将程序或函数的大小限制的情况下通常有用。 有关详细信息，请参阅[inline_depth](../../preprocessor/inline-depth.md)。  
  
## <a name="restrict-and-assume"></a>__restrict 和\__assume  
 有几个可以帮助提高性能的 Visual c + + 中的关键字： [__restrict](../../cpp/extension-restrict.md)和[__assume](../../intrinsics/assume.md)。  
  
 首先，应注意的是，`__restrict`和`__declspec(restrict)`是两个不同的事物。 虽然它们在某种程度上相关，其语义却不相同。 `__restrict`是的类型限定符，如`const`或`volatile`，但以独占方式为指针类型。  
  
 使用修改的指针`__restrict`称为*__restrict 指针*。 __Restrict 指针是一个指针，它仅可以通过访问\_（_r） 指针。 换而言之，另一个指针不能用于访问指向数据\_（_r） 指针。  
  
 `__restrict`可以 Visual c + + 优化器来说的强大工具，但将其用于格外注意。 如果使用不正确，则优化器可能会执行将会破坏您的应用程序优化。  
  
 `__restrict`关键字将替换**/Oa**切换从以前的版本。  
  
 与`__assume`，开发人员可以告诉编译器让假设某些变量的值。  
  
 例如`__assume(a < 5);`告知优化器在该行代码变量的`a`小于 5。 同样，这是对编译器的一个承诺。 如果`a`实际为 6 此时在程序中，则编译器具有优化之后，程序的行为可能不会与预期。 `__assume`将在 switch 语句和/或条件表达式之前最为有用。  
  
 有一些限制`__assume`。 首先，如`__restrict`，它是只是建议，因此编译器可以自由地忽略它。 此外，`__assume`当前仅适用于针对常量变量不相等。 它并不传播不相等符号，例如，assume(a<b)。  
  
## <a name="intrinsic-support"></a>内部函数的支持  
 内部函数是函数调用其中编译器内部函数了解该调用，并且初始屏幕而不是库中调用函数，它会发出该函数的代码。 位于 <Installation_Directory>\VC\include\intrin.h 中的标头文件 intrin.h 包含可用于三个受支持的平台（x86、x64 和 ARM）的所有内部函数。  
  
 内部函数使程序员能够深入探讨代码转而无需使用程序集。 有多个好处使用内部函数：  
  
1.  你的代码是更易于移植。 多个内部函数在多个 CPU 体系结构上都可用。  
  
2.  你的代码是易于阅读，因为 C/c + + 仍编写的代码。  
  
3.  你的代码获取编译器优化的好处。 因为编译器变得更好，可提高代码生成内部函数。  
  
 有关详细信息，请参阅[编译器内部函数](../../intrinsics/compiler-intrinsics.md)。  
  
## <a name="exceptions"></a>异常  
 会对性能与使用异常相关联的命中。 使用禁止编译器执行的某些优化的 try 块时，会引入一些限制。 在 x86 平台没有额外的性能下降 try 块由于必须在代码执行过程中生成的其他状态信息。 在 64 位平台，try 块不会降低性能进行很多，但查找处理程序和堆栈展开过程后引发异常，可能很昂贵。  
  
 因此，建议以避免 try/catch 块引入不真正需要它的代码。 如果必须使用异常，请尽可能使用同步的异常。 有关详细信息，请参阅 [Structured Exception Handling (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)。  
  
 最后，引发异常为异常用例。 有关常规控制流中使用异常可能会让性能会受到影响。  
  
## <a name="see-also"></a>请参阅  
 [优化代码](../../build/reference/optimizing-your-code.md)