---
title: 优化最佳做法
ms.date: 11/04/2016
helpviewer_keywords:
- Visual C++, optimization
- optimization, best practices
ms.assetid: f3433148-7255-4ca6-8a4f-7c31aac88508
ms.openlocfilehash: edb036292b87593a3f8bb9b3f5ec5f7beb84c3a5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274165"
---
# <a name="optimization-best-practices"></a>优化最佳做法

本文档介绍了一些最佳做法优化视觉对象中C++。

## <a name="compiler-and-linker-options"></a>编译器和链接器选项

### <a name="profile-guided-optimization"></a>按配置优化

VisualC++支持*的按配置优化*(PGO)。 这种优化使用中的应用程序的受检测版本培训执行的配置文件数据来驱动更高版本的应用程序的优化。 使用 PGO 会耗费大量时间，因此它可能不是指每个开发人员使用，但我们建议为最终发布版本的产品使用 PGO。 有关详细信息，请参阅[按配置文件优化](profile-guided-optimizations.md)。

此外，*全程序优化*（也称作链接时间代码生成） 和 **/o1**并 **/o2**改进了优化。 一般情况下，使用以下选项之一编译的应用程序将使用早期的编译器编译的相同应用程序更快。

有关详细信息，请参阅[/GL （全程序优化）](reference/gl-whole-program-optimization.md)并[/o1，/o2 （最小化大小、 最大化速度）](reference/o1-o2-minimize-size-maximize-speed.md)。

### <a name="which-level-of-optimization-to-use"></a>优化以使用哪个级别

如有可能，应使用配置文件引导式优化编译最终发布版本。 如果它不能使用 PGO，生成是否由于不足，无法运行所检测的版本或无法访问方案的基础结构，我们建议使用全程序优化生成。

**/Gy**开关也是非常有用。 它将生成单独 COMDAT，对于每个函数，为链接器提供更大的灵活性，就删除未引用的 Comdat 和 COMDAT 折叠。 使用的唯一缺点 **/Gy**是，在调试时，它可能会导致问题。 因此，通常建议使用它。 有关详细信息，请参阅 [/Gy （启用函数级链接）](reference/gy-enable-function-level-linking.md)。

对于 64 位环境中的链接，它建议使用 **/opt: ref、 ICF**链接器选项，以及在 32 位环境中 **/opt: ref**建议。 有关详细信息，请参阅[/OPT （优化）](reference/opt-optimizations.md)。

此外，强烈建议生成调试符号，即使使用优化的发布版本。 它不会影响生成的代码，并可更轻松地调试应用程序中，如果很多需要。

### <a name="floating-point-switches"></a>浮点开关

**/Op**编译器选项已被删除，并且已添加处理浮点优化以下四个编译器选项：

|||
|-|-|
|**/fp:precise**|这是默认的建议，应在大多数情况下使用。|
|**/fp:fast**|建议如果性能而言至关重要，例如在游戏中。 这将导致最快的性能。|
|**/fp:strict**|建议的如果精确的浮点异常和 IEEE 所需行为。 这将导致最慢的性能。|
|**/fp:except[-]**|可以结合使用 **/fp: strict**或 **/fp： 精确**，但不是 **/fp: fast**。|

有关详细信息，请参阅 [/fp（指定浮点行为）](reference/fp-specify-floating-point-behavior.md)。

## <a name="optimization-declspecs"></a>优化 declspec

在本部分中我们将介绍可在程序中用于帮助提高性能的两个 declspec:`__declspec(restrict)`和`__declspec(noalias)`。

`restrict` Declspec 仅应用于返回指针，如的函数声明 `__declspec(restrict) void *malloc(size_t size);`

`restrict` Declspec 返回非别名指针的函数上使用。 此关键字用于 C 运行时库实现`malloc`因为它将永远不会返回一个指针值 （除非您要进行某个非法操作，例如，使用内存，已被释放之后） 已在当前程序中使用。

`restrict` Declspec 为编译器提供了有关执行的编译器优化的详细信息。 为了使编译器确定最困难的工作之一是哪些指针别名其他指针，极大地使用此信息可帮助编译器。

一点值得一提，这是对编译器，不是，编译器将验证的一个承诺。 如果您的程序使用此`restrict`declspec 不恰当地，您的程序可能不正确的行为。

有关详细信息，请参阅[限制](../cpp/restrict.md)。

`noalias` Declspec 也只应用到函数，并指示该函数为半纯粹的函数。 半纯函数是引用或修改局部变量、 参数以及参数的第一级间接寻址。 此 declspec 是对编译器的一个承诺，如果该函数引用的全局或第二个一级间接寻址的指针参数则编译器可能生成的代码，将中断该应用程序。

有关详细信息，请参阅 [noalias](../cpp/noalias.md)。

## <a name="optimization-pragmas"></a>优化杂注

此外，还有几个有用的杂注，可帮助优化代码。 我们将讨论的第一个是`#pragma optimize`:

```cpp
#pragma optimize("{opt-list}", on | off)
```

此杂注，可在函数的函数的基础上设置给定的优化级别。 这是理想之选这些极少数情况下，应用程序发生故障时通过优化编译给定的函数。 可以使用此来关闭单个函数的优化：

```cpp
#pragma optimize("", off)
int myFunc() {...}
#pragma optimize("", on)
```

有关详细信息，请参阅[优化](../preprocessor/optimize.md)。

内联是最重要的优化，该编译器会执行此处我们将讨论几个帮助修改此行为的杂注之一。

`#pragma inline_recursion` 可用于指定希望应用程序能内联递归调用。 默认情况下处于关闭状态。 对于较小的函数的浅表递归，你可能要启用此。 有关详细信息，请参阅[inline_recursion](../preprocessor/inline-recursion.md)。

限制的深度的另一个有用杂注内联为`#pragma inline_depth`。 这是通常在您想要将程序或函数的大小限制的情况下很有用。 有关详细信息，请参阅[inline_depth](../preprocessor/inline-depth.md)。

## <a name="restrict-and-assume"></a>__restrict 和\__assume

有几个视觉对象中的关键字C++，可以帮助提高性能： [__restrict](../cpp/extension-restrict.md)并[__assume](../intrinsics/assume.md)。

首先，应注意的是，`__restrict`和`__declspec(restrict)`是两个不同的事物。 尽管它们在某种程度上相关，其语义会不同。 `__restrict` 是类型限定符，如`const`或`volatile`，但专用于指针类型。

使用修改的指针`__restrict`被称为 *__restrict 指针*。 __Restrict 指针是一个指针，它只能通过访问\__restrict 指针。 换而言之，另一个指针不能用于访问指向的数据\__restrict 指针。

`__restrict` 视觉对象可以是一个强大的工具C++优化器，但谨慎使用。 如果使用不当，则优化器可能会执行将会破坏您的应用程序的优化。

`__restrict`关键字将替换 **/Oa**从以前的版本切换。

使用`__assume`，开发人员可以告知编译器进行假设某些变量的值。

例如`__assume(a < 5);`告知优化器在该行代码变量的`a`小于 5。 同样，这是对编译器的一个承诺。 如果`a`为实际 6 此时在程序中的，则程序编译器经过优化后的行为可能不为所期望的内容。 `__assume` 是 switch 语句和/或条件表达式之前最有用。

有一些限制`__assume`。 首先，如`__restrict`，它仅仅是一个建议，因此编译器可以自由地将其忽略。 此外，`__assume`目前仅适用于针对常量变量不相等。 它不会传播不相等符号，例如，assume(a < b)。

## <a name="intrinsic-support"></a>内部函数支持

内部函数是函数调用，编译器具有内在了解调用，而不是库中调用函数，它会发出该函数的代码。 标头文件\<intrin.h > 包含所有可用的内部函数的每个受支持的硬件平台。

内部函数使程序员能够深入了解代码转而无需使用程序集。 有使用内部函数的几个好处：

- 你的代码是可移植性。 几个内部函数是在多个 CPU 体系结构上可用。

- 你的代码是易于阅读，因为代码仍用 C 编写 /C++。

- 在代码中受益的编译器优化。 因为编译器做得更好，提高了内部函数的代码生成。

有关详细信息，请参阅[编译器内部函数](../intrinsics/compiler-intrinsics.md)。

## <a name="exceptions"></a>Exceptions

会对性能与使用异常相关联的命中。 使用禁止编译器执行某些优化的 try 块时，会引入一些限制。 在 x86 平台没有额外的性能下降 try 块由于必须在代码执行期间生成的其他状态信息。 在 64 位平台，try 块不会降低性能与很多，但一旦引发异常，查找处理程序，并展开堆栈的过程可能很昂贵。

因此，建议以避免不真正需要它的代码中引入 try/catch 块。 如果必须使用异常，如有可能使用同步异常。 有关详细信息，请参阅 [Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)。

最后，引发异常为异常用例。 使用常规控制流异常可能会让性能会受到影响。

## <a name="see-also"></a>请参阅

- [优化代码](optimizing-your-code.md)
